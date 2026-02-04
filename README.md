# Full Stack FastAPI 템플릿

<a href="https://github.com/fastapi/full-stack-fastapi-template/actions?query=workflow%3A%22Test+Docker+Compose%22" target="_blank"><img src="https://github.com/fastapi/full-stack-fastapi-template/workflows/Test%20Docker%20Compose/badge.svg" alt="Test Docker Compose"></a>
<a href="https://github.com/fastapi/full-stack-fastapi-template/actions?query=workflow%3A%22Test+Backend%22" target="_blank"><img src="https://github.com/fastapi/full-stack-fastapi-template/workflows/Test%20Backend/badge.svg" alt="Test Backend"></a>
<a href="https://coverage-badge.samuelcolvin.workers.dev/redirect/fastapi/full-stack-fastapi-template" target="_blank"><img src="https://coverage-badge.samuelcolvin.workers.dev/fastapi/full-stack-fastapi-template.svg" alt="Coverage"></a>

## 기술 스택 및 특징

- ⚡ [**FastAPI**](https://fastapi.tiangolo.com) – Python 백엔드 API
  - 🧰 [SQLModel](https://sqlmodel.tiangolo.com) – Python SQL 데이터베이스 연동(ORM)
  - 🔍 [Pydantic](https://docs.pydantic.dev) – FastAPI에서 사용하는 데이터 검증 및 설정 관리 라이브러리
  - 💾 [PostgreSQL](https://www.postgresql.org) – SQL 데이터베이스
- 🚀 [React](https://react.dev) – 프론트엔드
  - 💃 TypeScript, Hooks, [Vite](https://vitejs.dev) 등 최신 프론트엔드 스택 사용
  - 🎨 [Tailwind CSS](https://tailwindcss.com) 및 [shadcn/ui](https://ui.shadcn.com) 컴포넌트 사용
  - 🤖 자동 생성된 프론트엔드 클라이언트
  - 🧪 [Playwright](https://playwright.dev) – E2E 테스트
  - 🦇 다크 모드 지원
- 🐋 개발 및 프로덕션용 [Docker Compose](https://www.docker.com)
- 🔒 기본 제공 안전한 비밀번호 해싱
- 🔑 JWT(JSON Web Token) 인증
- 📫 이메일 기반 비밀번호 재설정 기능
- 📬 로컬 개발 시 이메일 테스트용 [Mailcatcher](https://mailcatcher.me)
- ✅ [Pytest](https://pytest.org)를 이용한 테스트
- 📞 [Traefik](https://traefik.io) – 리버스 프록시 / 로드 밸런서
- 🚢 Docker Compose 기반 배포 가이드 (자동 HTTPS 인증서를 처리하는 프론트엔드 Traefik 프록시 설정 포함)
- 🏭 GitHub Actions 기반 CI(지속적 통합) 및 CD(지속적 배포)

### 대시보드 로그인

[![API docs](img/login.png)](https://github.com/fastapi/full-stack-fastapi-template)

### 대시보드 - 관리자

[![API docs](img/dashboard.png)](https://github.com/fastapi/full-stack-fastapi-template)

### 대시보드 - 아이템

[![API docs](img/dashboard-items.png)](https://github.com/fastapi/full-stack-fastapi-template)

### 대시보드 - 다크 모드

[![API docs](img/dashboard-dark.png)](https://github.com/fastapi/full-stack-fastapi-template)

### 인터랙티브 API 문서

[![API docs](img/docs.png)](https://github.com/fastapi/full-stack-fastapi-template)

## 사용 방법

이 저장소를 **그대로 포크하거나 클론**해서 바로 사용할 수 있습니다.

✨ 그냥 동작합니다. ✨

### 비공개 저장소로 사용하기

비공개 저장소로 사용하고 싶은 경우, GitHub는 포크의 공개 범위를 변경하는 것을 허용하지 않기 때문에 단순 포크만으로는 안 됩니다.

대신 다음과 같이 할 수 있습니다.

- 예를 들어 `my-full-stack` 이라는 새 GitHub 저장소를 생성합니다.
- 이 저장소를 수동으로 클론하면서 프로젝트 이름을 원하는 이름(예: `my-full-stack`)으로 설정합니다.

```bash
git clone git@github.com:fastapi/full-stack-fastapi-template.git my-full-stack
```

- 새 디렉터리로 들어갑니다.

```bash
cd my-full-stack
```

- 원격 저장소(origin)를 방금 만든 새 저장소로 변경합니다(주소는 GitHub 인터페이스에서 복사).

```bash
git remote set-url origin git@github.com:octocat/my-full-stack.git
```

- 나중에 템플릿의 업데이트를 받아올 수 있도록 이 원본 저장소를 또 다른 "remote"로 추가합니다.

```bash
git remote add upstream git@github.com:fastapi/full-stack-fastapi-template.git
```

- 코드를 새 저장소로 푸시합니다.

```bash
git push -u origin master
```

### 원본 템플릿에서 업데이트 가져오기

이 저장소를 클론하고 수정한 뒤, 원본 템플릿의 최신 변경 사항을 반영하고 싶을 수 있습니다.

- 먼저 원본 저장소를 remote로 추가했는지 확인합니다.

```bash
git remote -v

origin    git@github.com:octocat/my-full-stack.git (fetch)
origin    git@github.com:octocat/my-full-stack.git (push)
upstream  git@github.com:fastapi/full-stack-fastapi-template.git (fetch)
upstream  git@github.com:fastapi/full-stack-fastapi-template.git (push)
```

- merge 없이 최신 변경 사항을 가져옵니다.

```bash
git pull --no-commit upstream master
```

이 명령은 템플릿의 최신 변경 사항을 커밋 없이 가져오기 때문에, 커밋 전에 변경 내용을 직접 확인할 수 있습니다.

- 충돌이 난 경우, 에디터에서 해결합니다.

- 모두 정리되면 변경 사항을 커밋합니다.

```bash
git merge --continue
```

### 설정

`.env` 파일의 설정을 변경해 자신에게 맞게 구성할 수 있습니다.

배포 전에 최소한 다음 값들은 꼭 변경해야 합니다.

- `SECRET_KEY`
- `FIRST_SUPERUSER_PASSWORD`
- `POSTGRES_PASSWORD`

이 값들은 가능한 한 환경 변수(예: CI/CD나 서버의 시크릿)에 설정해서 주입하는 것이 좋습니다.

자세한 내용은 [deployment.md](./deployment.md) 문서를 참고하세요.

### 시크릿 키 생성

`.env` 파일의 일부 환경 변수들은 기본값으로 `changethis`를 가지고 있습니다.

이 값들은 반드시 시크릿 키로 변경해야 합니다. 시크릿 키를 생성하려면 아래 명령을 실행합니다.

```bash
python -c "import secrets; print(secrets.token_urlsafe(32))"
```

출력된 값을 복사해서 비밀번호 / 시크릿 키로 사용하세요. 보안을 위해 여러 개가 필요하다면 이 명령을 여러 번 실행해 각각 다른 값을 사용합니다.

## Copier로 사용하는 대안적인 방법

이 저장소는 [Copier](https://copier.readthedocs.io)를 이용해 새 프로젝트를 생성하는 방식도 지원합니다.

Copier는 모든 파일을 복사하고, 몇 가지 설정값을 질문한 뒤, 입력값을 기반으로 `.env` 파일들을 자동으로 업데이트합니다.

### Copier 설치

아래와 같이 Copier를 설치할 수 있습니다.

```bash
pip install copier
```

또는 [`pipx`](https://pipx.pypa.io/)가 있다면 다음과 같이 실행할 수 있습니다.

```bash
pipx install copier
```

**참고**: `pipx`가 있다면 Copier를 굳이 설치하지 않고도 바로 실행할 수 있습니다.

### Copier로 프로젝트 생성

예를 들어 `my-awesome-project`처럼 새 프로젝트 디렉터리 이름을 정합니다.

프로젝트의 부모 디렉터리로 이동한 뒤, 아래와 같이 명령을 실행합니다.

```bash
copier copy https://github.com/fastapi/full-stack-fastapi-template my-awesome-project --trust
```

`pipx`가 있고 Copier를 설치하지 않았다면 다음처럼 바로 실행할 수 있습니다.

```bash
pipx run copier copy https://github.com/fastapi/full-stack-fastapi-template my-awesome-project --trust
```

**주의**: `.env` 파일들을 업데이트하는 [post-creation 스크립트](https://github.com/fastapi/full-stack-fastapi-template/blob/master/.copier/update_dotenv.py)를 실행하기 위해 `--trust` 옵션이 필수입니다.

### 입력 변수

Copier는 몇 가지 값을 질문합니다. 미리 알고 있으면 편리하지만, 나중에 `.env` 파일에서 수정해도 됩니다.

입력 변수와 기본값(일부는 자동 생성됨)은 다음과 같습니다.

- `project_name`: (기본값: `"FastAPI Project"`) API 사용자에게 표시되는 프로젝트 이름 (`.env`에 저장)
- `stack_name`: (기본값: `"fastapi-project"`) Docker Compose 라벨 및 프로젝트 이름에 사용되는 스택 이름 (공백, 마침표 없음, `.env`에 저장)
- `secret_key`: (기본값: `"changethis"`) 프로젝트용 시크릿 키 (`.env`에 저장, 위에서 설명한 방법으로 생성 가능)
- `first_superuser`: (기본값: `"admin@example.com"`) 첫 슈퍼유저의 이메일 (`.env`에 저장)
- `first_superuser_password`: (기본값: `"changethis"`) 첫 슈퍼유저의 비밀번호 (`.env`에 저장)
- `smtp_host`: (기본값: `""`) 이메일 전송용 SMTP 서버 호스트 (나중에 `.env`에서 설정 가능)
- `smtp_user`: (기본값: `""`) SMTP 서버 사용자명 (나중에 `.env`에서 설정 가능)
- `smtp_password`: (기본값: `""`) SMTP 서버 비밀번호 (나중에 `.env`에서 설정 가능)
- `emails_from_email`: (기본값: `"info@example.com"`) 이메일 발신자 주소 (나중에 `.env`에서 설정 가능)
- `postgres_password`: (기본값: `"changethis"`) PostgreSQL 데이터베이스 비밀번호 (`.env`에 저장, 위에서 설명한 방법으로 생성 가능)
- `sentry_dsn`: (기본값: `""`) Sentry를 사용할 경우 DSN (나중에 `.env`에서 설정 가능)

## 백엔드 개발

백엔드 개발 문서: [backend/README.md](./backend/README.md)

## 프론트엔드 개발

프론트엔드 개발 문서: [frontend/README.md](./frontend/README.md)

## 배포

배포 문서: [deployment.md](./deployment.md)

## 개발

일반 개발 문서: [development.md](./development.md)

여기에는 Docker Compose 사용법, 로컬 커스텀 도메인, `.env` 설정 등과 같은 내용이 포함됩니다.

## 릴리스 노트

릴리스 노트: [release-notes.md](./release-notes.md)

## 라이선스

Full Stack FastAPI 템플릿은 MIT 라이선스를 따릅니다.

