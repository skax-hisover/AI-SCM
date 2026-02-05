# FastAPI 프로젝트 - 백엔드

## 요구 사항

* [Docker](https://www.docker.com/).
* Python 패키지 및 환경 관리를 위한 [uv](https://docs.astral.sh/uv/).

## Docker Compose

[../development.md](../development.md) 가이드를 따라 Docker Compose로 로컬 개발 환경을 시작하세요.

## 일반 워크플로우

기본적으로 종속성은 [uv](https://docs.astral.sh/uv/)로 관리됩니다. 해당 사이트에서 설치하세요.

`./backend/` 디렉터리에서 다음 명령으로 모든 종속성을 설치할 수 있습니다:

```console
$ uv sync
```

그런 다음 가상 환경을 활성화할 수 있습니다:

```console
$ source .venv/bin/activate
```

에디터가 `backend/.venv/bin/python`에 있는 인터프리터로 올바른 Python 가상 환경을 사용하고 있는지 확인하세요.

데이터 및 SQL 테이블용 SQLModel 모델은 `./backend/app/models.py`에서, API 엔드포인트는 `./backend/app/api/`에서, CRUD(Create, Read, Update, Delete) 유틸리티는 `./backend/app/crud.py`에서 수정하거나 추가하세요.

## VS Code

VS Code 디버거를 통해 백엔드를 실행할 수 있는 설정이 이미 구성되어 있어서, 브레이크포인트를 사용하고, 일시 정지하고, 변수를 탐색하는 등의 작업을 할 수 있습니다.

VS Code Python 테스트 탭을 통해 테스트를 실행할 수 있도록 설정도 이미 구성되어 있습니다.

## Docker Compose Override

개발 중에 로컬 개발 환경에만 영향을 미치는 Docker Compose 설정을 `compose.override.yml` 파일에서 변경할 수 있습니다.

해당 파일의 변경 사항은 로컬 개발 환경에만 영향을 미치며, 프로덕션 환경에는 영향을 주지 않습니다. 따라서 개발 워크플로우에 도움이 되는 "임시" 변경 사항을 추가할 수 있습니다.

예를 들어, 백엔드 코드가 있는 디렉터리는 Docker 컨테이너에 동기화되어, 변경한 코드가 컨테이너 내부의 디렉터리로 실시간 복사됩니다. 이렇게 하면 Docker 이미지를 다시 빌드하지 않고도 변경 사항을 즉시 테스트할 수 있습니다. 이는 개발 중에만 해야 하며, 프로덕션에서는 최신 버전의 백엔드 코드로 Docker 이미지를 빌드해야 합니다. 하지만 개발 중에는 매우 빠르게 반복 작업할 수 있습니다.

기본 `fastapi run` 대신 `fastapi run --reload`를 실행하는 명령 오버라이드도 있습니다. 이는 (프로덕션처럼 여러 개가 아닌) 단일 서버 프로세스를 시작하고 코드가 변경될 때마다 프로세스를 다시 로드합니다. 문법 오류가 있는 상태에서 Python 파일을 저장하면 중단되고 종료되어 컨테이너가 멈춥니다. 그 후 오류를 수정하고 다시 실행하여 컨테이너를 다시 시작할 수 있습니다:

```console
$ docker compose watch
```

주석 처리된 `command` 오버라이드도 있습니다. 주석을 해제하고 기본값을 주석 처리할 수 있습니다. 이렇게 하면 백엔드 컨테이너가 "아무것도 하지 않는" 프로세스를 실행하지만 컨테이너는 살아 있습니다. 이를 통해 실행 중인 컨테이너 내부로 들어가서 명령을 실행할 수 있습니다. 예를 들어 설치된 종속성을 테스트하기 위한 Python 인터프리터나, 변경 사항을 감지하면 다시 로드하는 개발 서버를 시작할 수 있습니다.

`bash` 세션으로 컨테이너 내부로 들어가려면 다음으로 스택을 시작합니다:

```console
$ docker compose watch
```

그런 다음 다른 터미널에서 실행 중인 컨테이너로 `exec` 합니다:

```console
$ docker compose exec backend bash
```

다음과 같은 출력이 표시됩니다:

```console
root@7f2607af31c3:/app#
```

이는 컨테이너 내부의 `bash` 세션에 있으며, `root` 사용자로, `/app` 디렉터리 아래에 있다는 의미입니다. 이 디렉터리 안에는 "app"이라는 또 다른 디렉터리가 있으며, 그곳에 코드가 있습니다: `/app/app`.

거기서 `fastapi run --reload` 명령을 사용하여 디버그 실시간 리로딩 서버를 실행할 수 있습니다.

```console
$ fastapi run --reload app/main.py
```

...다음과 같이 보일 것입니다:

```console
root@7f2607af31c3:/app# fastapi run --reload app/main.py
```

그리고 Enter를 누릅니다. 이렇게 하면 코드 변경을 감지할 때 자동으로 다시 로드하는 실시간 리로딩 서버가 실행됩니다.

그럼에도 불구하고 변경 사항이 아닌 문법 오류를 감지하면 오류와 함께 멈춥니다. 하지만 컨테이너가 여전히 살아 있고 Bash 세션에 있으므로, 오류를 수정한 후 동일한 명령을 실행하여 빠르게 다시 시작할 수 있습니다 ("위쪽 화살표"와 "Enter").

...이 이전 세부 사항이 컨테이너를 아무것도 하지 않고 살아 있게 한 다음, Bash 세션에서 실시간 리로드 서버를 실행하는 것이 유용한 이유입니다.

## 백엔드 테스트

백엔드를 테스트하려면 다음을 실행합니다:

```console
$ bash ./scripts/test.sh
```

테스트는 Pytest로 실행되며, `./backend/tests/`에서 테스트를 수정하고 추가합니다.

GitHub Actions를 사용하면 테스트가 자동으로 실행됩니다.

### 실행 중인 스택 테스트

스택이 이미 실행 중이고 테스트만 실행하고 싶다면 다음을 사용할 수 있습니다:

```bash
docker compose exec backend bash scripts/tests-start.sh
```

해당 `/app/scripts/tests-start.sh` 스크립트는 나머지 스택이 실행 중인지 확인한 후 `pytest`를 호출합니다. `pytest`에 추가 인수를 전달해야 하는 경우 해당 명령에 전달하면 포워딩됩니다.

예를 들어, 첫 번째 오류에서 중지하려면:

```bash
docker compose exec backend bash scripts/tests-start.sh -x
```

### 테스트 커버리지

테스트가 실행되면 `htmlcov/index.html` 파일이 생성되며, 브라우저에서 열어 테스트 커버리지를 확인할 수 있습니다.

## 마이그레이션

로컬 개발 중에는 앱 디렉터리가 컨테이너 내부에 볼륨으로 마운트되므로, 컨테이너 내부에서 `alembic` 명령으로 마이그레이션을 실행할 수 있으며 마이그레이션 코드는 앱 디렉터리에 있습니다 (컨테이너 내부에만 있는 것이 아님). 따라서 git 저장소에 추가할 수 있습니다.

모델을 변경할 때마다 모델의 "revision"을 생성하고 해당 revision으로 데이터베이스를 "upgrade"해야 합니다. 이것이 데이터베이스의 테이블을 업데이트하기 때문입니다. 그렇지 않으면 애플리케이션에 오류가 발생합니다.

* 백엔드 컨테이너에서 대화형 세션을 시작합니다:

```console
$ docker compose exec backend bash
```

* Alembic은 이미 `./backend/app/models.py`에서 SQLModel 모델을 가져오도록 구성되어 있습니다.

* 모델을 변경한 후 (예: 열 추가), 컨테이너 내부에서 revision을 생성합니다. 예:

```console
$ alembic revision --autogenerate -m "Add column last_name to User model"
```

* alembic 디렉터리에 생성된 파일을 git 저장소에 커밋합니다.

* revision을 생성한 후, 데이터베이스에서 마이그레이션을 실행합니다 (이것이 실제로 데이터베이스를 변경합니다):

```console
$ alembic upgrade head
```

마이그레이션을 전혀 사용하고 싶지 않다면, `./backend/app/core/db.py` 파일에서 다음으로 끝나는 줄의 주석을 해제하세요:

```python
SQLModel.metadata.create_all(engine)
```

그리고 `scripts/prestart.sh` 파일에서 다음을 포함하는 줄을 주석 처리하세요:

```console
$ alembic upgrade head
```

기본 모델로 시작하고 싶지 않고 이전 revision 없이 처음부터 제거/수정하고 싶다면, `./backend/app/alembic/versions/` 아래의 revision 파일들 (`.py` Python 파일)을 제거할 수 있습니다. 그런 다음 위에서 설명한 대로 첫 번째 마이그레이션을 생성합니다.

## 이메일 템플릿

이메일 템플릿은 `./backend/app/email-templates/`에 있습니다. 여기에는 `build`와 `src` 두 개의 디렉터리가 있습니다. `src` 디렉터리에는 최종 이메일 템플릿을 빌드하는 데 사용되는 소스 파일이 포함되어 있습니다. `build` 디렉터리에는 애플리케이션에서 사용하는 최종 이메일 템플릿이 포함되어 있습니다.

계속하기 전에 VS Code에 [MJML 확장](https://github.com/mjmlio/vscode-mjml)이 설치되어 있는지 확인하세요.

MJML 확장을 설치한 후, `src` 디렉터리에서 새 이메일 템플릿을 생성할 수 있습니다. 새 이메일 템플릿을 생성하고 `.mjml` 파일이 에디터에서 열린 상태에서, `Ctrl+Shift+P`로 명령 팔레트를 열고 `MJML: Export to HTML`을 검색합니다. 이렇게 하면 `.mjml` 파일이 `.html` 파일로 변환되며, 이제 build 디렉터리에 저장할 수 있습니다.
