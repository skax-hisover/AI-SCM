# FastAPI 프로젝트 - 배포

Docker Compose를 사용하여 원격 서버에 프로젝트를 배포할 수 있습니다.

이 프로젝트는 외부와의 통신 및 HTTPS 인증서를 처리하는 Traefik 프록시가 있다고 가정합니다.

CI/CD(지속적 통합 및 지속적 배포) 시스템을 사용하여 자동으로 배포할 수 있으며, GitHub Actions로 이를 수행하는 설정이 이미 포함되어 있습니다.

하지만 먼저 몇 가지를 설정해야 합니다. 🤓

## 사전 준비

* 원격 서버를 준비합니다.
* 도메인의 DNS 레코드가 방금 생성한 서버의 IP를 가리키도록 설정합니다.
* 도메인에 와일드카드 서브도메인을 설정하여 다양한 서비스에 대해 여러 서브도메인을 사용할 수 있도록 합니다. 예: `*.fastapi-project.example.com`. 이렇게 하면 `dashboard.fastapi-project.example.com`, `api.fastapi-project.example.com`, `traefik.fastapi-project.example.com`, `adminer.fastapi-project.example.com` 등 다양한 컴포넌트에 접근할 수 있습니다. 또한 `staging` 환경에도 유용합니다. 예: `dashboard.staging.fastapi-project.example.com`, `adminer.staging.fastapi-project.example.com` 등.
* 원격 서버에 [Docker](https://docs.docker.com/engine/install/)를 설치하고 설정합니다 (Docker Desktop이 아닌 Docker Engine).

## 공용 Traefik

들어오는 연결과 HTTPS 인증서를 처리하기 위해 Traefik 프록시가 필요합니다.

다음 단계는 한 번만 수행하면 됩니다.

### Traefik Docker Compose

* 원격 서버에 Traefik Docker Compose 파일을 저장할 디렉터리를 생성합니다:

```bash
mkdir -p /root/code/traefik-public/
```

Traefik Docker Compose 파일을 서버로 복사합니다. 로컬 터미널에서 `rsync` 명령을 실행하여 수행할 수 있습니다:

```bash
rsync -a compose.traefik.yml root@your-server.example.com:/root/code/traefik-public/
```

### Traefik 공용 네트워크

이 Traefik은 스택과 통신하기 위해 `traefik-public`이라는 Docker "공용 네트워크"가 필요합니다.

이렇게 하면 외부 세계와의 통신(HTTP 및 HTTPS)을 처리하는 단일 공용 Traefik 프록시가 있고, 그 뒤에 동일한 단일 서버에 있더라도 서로 다른 도메인을 가진 하나 이상의 스택을 둘 수 있습니다.

`traefik-public`이라는 Docker "공용 네트워크"를 생성하려면 원격 서버에서 다음 명령을 실행합니다:

```bash
docker network create traefik-public
```

### Traefik 환경 변수

Traefik Docker Compose 파일은 시작하기 전에 터미널에 몇 가지 환경 변수가 설정되어 있어야 합니다. 원격 서버에서 다음 명령을 실행하여 설정할 수 있습니다.

* HTTP 기본 인증용 사용자 이름을 생성합니다. 예:

```bash
export USERNAME=admin
```

* HTTP 기본 인증용 비밀번호로 환경 변수를 생성합니다. 예:

```bash
export PASSWORD=changethis
```

* openssl을 사용하여 HTTP 기본 인증용 비밀번호의 "해시" 버전을 생성하고 환경 변수에 저장합니다:

```bash
export HASHED_PASSWORD=$(openssl passwd -apr1 $PASSWORD)
```

해시된 비밀번호가 올바른지 확인하려면 출력해 볼 수 있습니다:

```bash
echo $HASHED_PASSWORD
```

* 서버의 도메인 이름으로 환경 변수를 생성합니다. 예:

```bash
export DOMAIN=fastapi-project.example.com
```

* Let's Encrypt용 이메일로 환경 변수를 생성합니다. 예:

```bash
export EMAIL=admin@example.com
```

**참고**: 다른 이메일을 설정해야 합니다. `@example.com` 이메일은 작동하지 않습니다.

### Traefik Docker Compose 시작

원격 서버에서 Traefik Docker Compose 파일을 복사한 디렉터리로 이동합니다:

```bash
cd /root/code/traefik-public/
```

이제 환경 변수가 설정되고 `compose.traefik.yml`이 준비되었으므로, 다음 명령을 실행하여 Traefik Docker Compose를 시작할 수 있습니다:

```bash
docker compose -f compose.traefik.yml up -d
```

## FastAPI 프로젝트 배포

이제 Traefik이 준비되었으므로 Docker Compose로 FastAPI 프로젝트를 배포할 수 있습니다.

**참고**: GitHub Actions를 사용한 지속적 배포 섹션으로 바로 넘어가셔도 됩니다.

## 코드 복사

```bash
rsync -av --filter=":- .gitignore" ./ root@your-server.example.com:/root/code/app/
```

참고: `--filter=":- .gitignore"`는 `rsync`에게 git과 동일한 규칙을 사용하라고 알려줍니다. Python 가상 환경과 같이 git이 무시하는 파일을 무시합니다.

## 환경 변수

먼저 몇 가지 환경 변수를 설정해야 합니다.

### 시크릿 키 생성

`.env` 파일의 일부 환경 변수는 기본값이 `changethis`입니다.

시크릿 키로 변경해야 합니다. 시크릿 키를 생성하려면 다음 명령을 실행합니다:

```bash
python -c "import secrets; print(secrets.token_urlsafe(32))"
```

출력된 내용을 복사하여 비밀번호 / 시크릿 키로 사용하세요. 다른 보안 키를 생성하려면 다시 실행하세요.

### 필수 환경 변수

`ENVIRONMENT`를 설정합니다. 기본값은 `local`(개발용)이지만, 서버에 배포할 때는 `staging` 또는 `production`과 같은 값을 설정합니다:

```bash
export ENVIRONMENT=production
```

`DOMAIN`을 설정합니다. 기본값은 `localhost`(개발용)이지만, 배포할 때는 자신의 도메인을 사용합니다. 예:

```bash
export DOMAIN=fastapi-project.example.com
```

`POSTGRES_PASSWORD`를 `changethis`가 아닌 다른 값으로 설정합니다:

```bash
export POSTGRES_PASSWORD="changethis"
```

토큰 서명에 사용되는 `SECRET_KEY`를 설정합니다:

```bash
export SECRET_KEY="changethis"
```

참고: 위의 Python 명령을 사용하여 보안 시크릿 키를 생성할 수 있습니다.

`FIRST_SUPERUSER_PASSWORD`를 `changethis`가 아닌 다른 값으로 설정합니다:

```bash
export FIRST_SUPERUSER_PASSWORD="changethis"
```

도메인을 포함하도록 `BACKEND_CORS_ORIGINS`를 설정합니다:

```bash
export BACKEND_CORS_ORIGINS="https://dashboard.${DOMAIN?Variable not set},https://api.${DOMAIN?Variable not set}"
```

다른 여러 환경 변수도 설정할 수 있습니다:

* `PROJECT_NAME`: 프로젝트 이름으로, 문서 및 이메일에서 API에 사용됩니다.
* `STACK_NAME`: Docker Compose 라벨 및 프로젝트 이름에 사용되는 스택 이름으로, `staging`, `production` 등에 따라 달라야 합니다. 점을 대시로 바꾼 동일한 도메인을 사용할 수 있습니다. 예: `fastapi-project-example-com` 및 `staging-fastapi-project-example-com`.
* `BACKEND_CORS_ORIGINS`: 쉼표로 구분된 허용 CORS 오리진 목록.
* `FIRST_SUPERUSER`: 첫 번째 슈퍼유저의 이메일로, 이 슈퍼유저가 새 사용자를 생성할 수 있습니다.
* `SMTP_HOST`: 이메일을 보내기 위한 SMTP 서버 호스트로, 이메일 제공업체(예: Mailgun, Sparkpost, Sendgrid 등)에서 제공합니다.
* `SMTP_USER`: 이메일을 보내기 위한 SMTP 서버 사용자.
* `SMTP_PASSWORD`: 이메일을 보내기 위한 SMTP 서버 비밀번호.
* `EMAILS_FROM_EMAIL`: 이메일을 보낼 이메일 계정.
* `POSTGRES_SERVER`: PostgreSQL 서버의 호스트 이름. 동일한 Docker Compose에서 제공하는 기본값 `db`를 그대로 둘 수 있습니다. 타사 제공업체를 사용하지 않는 한 일반적으로 변경할 필요가 없습니다.
* `POSTGRES_PORT`: PostgreSQL 서버의 포트. 기본값을 그대로 둘 수 있습니다. 타사 제공업체를 사용하지 않는 한 일반적으로 변경할 필요가 없습니다.
* `POSTGRES_USER`: Postgres 사용자로, 기본값을 그대로 둘 수 있습니다.
* `POSTGRES_DB`: 이 애플리케이션에 사용할 데이터베이스 이름. 기본값 `app`을 그대로 둘 수 있습니다.
* `SENTRY_DSN`: Sentry를 사용하는 경우 DSN.

## GitHub Actions 환경 변수

GitHub Actions에서만 사용되는 몇 가지 환경 변수가 있으며 설정할 수 있습니다:

* `LATEST_CHANGES`: GitHub Action [latest-changes](https://github.com/tiangolo/latest-changes)에서 병합된 PR을 기반으로 릴리스 노트를 자동으로 추가하는 데 사용됩니다. 개인 액세스 토큰이며, 자세한 내용은 문서를 참조하세요.
* `SMOKESHOW_AUTH_KEY`: [Smokeshow](https://github.com/samuelcolvin/smokeshow)를 사용하여 코드 커버리지를 처리하고 게시하는 데 사용됩니다. 지침에 따라 (무료) Smokeshow 키를 생성하세요.

### Docker Compose로 배포

환경 변수가 준비되면 Docker Compose로 배포할 수 있습니다:

```bash
cd /root/code/app/
docker compose -f compose.yml build
docker compose -f compose.yml up -d
```

프로덕션에서는 `compose.override.yml`의 오버라이드를 사용하지 않으므로, 사용할 파일로 `compose.yml`을 명시적으로 지정합니다.

## 지속적 배포 (CD)

GitHub Actions를 사용하여 프로젝트를 자동으로 배포할 수 있습니다. 😎

여러 환경 배포를 가질 수 있습니다.

이미 `staging`과 `production` 두 가지 환경이 설정되어 있습니다. 🚀

### GitHub Actions Runner 설치

* 원격 서버에서 GitHub Actions용 사용자를 생성합니다:

```bash
sudo adduser github
```

* `github` 사용자에게 Docker 권한을 추가합니다:

```bash
sudo usermod -aG docker github
```

* 일시적으로 `github` 사용자로 전환합니다:

```bash
sudo su - github
```

* `github` 사용자의 홈 디렉터리로 이동합니다:

```bash
cd
```

* [공식 가이드에 따라 GitHub Action 셀프 호스팅 러너를 설치합니다](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners#adding-a-self-hosted-runner-to-a-repository).

* 라벨을 묻는 메시지가 표시되면 환경에 대한 라벨을 추가합니다. 예: `production`. 나중에 라벨을 추가할 수도 있습니다.

설치 후 가이드는 러너를 시작하는 명령을 실행하라고 알려줍니다. 그러나 해당 프로세스를 종료하거나 서버에 대한 로컬 연결이 끊어지면 중지됩니다.

시작 시 실행되고 계속 실행되도록 하려면 서비스로 설치할 수 있습니다. 이를 위해 `github` 사용자를 종료하고 `root` 사용자로 돌아갑니다:

```bash
exit
```

이 작업을 수행하면 이전 사용자로 다시 돌아갑니다. 그리고 해당 사용자에 속한 이전 디렉터리에 있게 됩니다.

`github` 사용자 디렉터리로 이동하기 전에 `root` 사용자가 되어야 합니다(이미 `root`일 수 있음):

```bash
sudo su
```

* `root` 사용자로서 `github` 사용자의 홈 디렉터리 내 `actions-runner` 디렉터리로 이동합니다:

```bash
cd /home/github/actions-runner
```

* `github` 사용자로 셀프 호스팅 러너를 서비스로 설치합니다:

```bash
./svc.sh install github
```

* 서비스를 시작합니다:

```bash
./svc.sh start
```

* 서비스 상태를 확인합니다:

```bash
./svc.sh status
```

공식 가이드에서 자세한 내용을 읽을 수 있습니다: [셀프 호스팅 러너 애플리케이션을 서비스로 설정](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/configuring-the-self-hosted-runner-application-as-a-service).

### 시크릿 설정

저장소에서 필요한 환경 변수에 대한 시크릿을 설정합니다. 위에서 설명한 것과 동일하며 `SECRET_KEY` 등이 포함됩니다. [저장소 시크릿 설정에 대한 공식 GitHub 가이드](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository)를 따르세요.

현재 GitHub Actions 워크플로우는 다음 시크릿을 필요로 합니다:

* `DOMAIN_PRODUCTION`
* `DOMAIN_STAGING`
* `STACK_NAME_PRODUCTION`
* `STACK_NAME_STAGING`
* `EMAILS_FROM_EMAIL`
* `FIRST_SUPERUSER`
* `FIRST_SUPERUSER_PASSWORD`
* `POSTGRES_PASSWORD`
* `SECRET_KEY`
* `LATEST_CHANGES`
* `SMOKESHOW_AUTH_KEY`

## GitHub Action 배포 워크플로우

`.github/workflows` 디렉터리에 환경(GitHub Actions 러너의 라벨)에 배포하도록 이미 설정된 GitHub Action 워크플로우가 있습니다:

* `staging`: `master` 브랜치에 푸시(또는 병합) 후.
* `production`: 릴리스 게시 후.

추가 환경이 필요한 경우 이를 시작점으로 사용할 수 있습니다.

## URL

`fastapi-project.example.com`을 자신의 도메인으로 교체하세요.

### 메인 Traefik 대시보드

Traefik UI: `https://traefik.fastapi-project.example.com`

### 프로덕션

프론트엔드: `https://dashboard.fastapi-project.example.com`

백엔드 API 문서: `https://api.fastapi-project.example.com/docs`

백엔드 API 기본 URL: `https://api.fastapi-project.example.com`

Adminer: `https://adminer.fastapi-project.example.com`

### 스테이징

프론트엔드: `https://dashboard.staging.fastapi-project.example.com`

백엔드 API 문서: `https://api.staging.fastapi-project.example.com/docs`

백엔드 API 기본 URL: `https://api.staging.fastapi-project.example.com`

Adminer: `https://adminer.staging.fastapi-project.example.com`
