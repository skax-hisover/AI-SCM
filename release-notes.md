# 릴리스 노트

## 최신 변경 사항

### 문서

* 📝 `CONTRIBUTING.md` 추가. PR [#2159](https://github.com/fastapi/full-stack-fastapi-template/pull/2159) by [@alejsdev](https://github.com/alejsdev).

### 내부

* 👷 pre-commit으로 mypy 실행. PR [#2169](https://github.com/fastapi/full-stack-fastapi-template/pull/2169) by [@YuriiMotov](https://github.com/YuriiMotov).
* ⬆ @tanstack/router-devtools 1.153.2에서 1.157.17로 업그레이드. PR [#2166](https://github.com/fastapi/full-stack-fastapi-template/pull/2166) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ @types/node 25.0.10에서 25.1.0으로 업그레이드. PR [#2168](https://github.com/fastapi/full-stack-fastapi-template/pull/2168) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ axios 1.13.2에서 1.13.4로 업그레이드. PR [#2164](https://github.com/fastapi/full-stack-fastapi-template/pull/2164) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆️ biome.json의 biome 스키마 버전을 2.3.12로 업그레이드. PR [#2154](https://github.com/fastapi/full-stack-fastapi-template/pull/2154) by [@alejsdev](https://github.com/alejsdev).
* ⬆ @biomejs/biome 2.3.11에서 2.3.12로 업그레이드. PR [#2153](https://github.com/fastapi/full-stack-fastapi-template/pull/2153) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 playwright v1.57.0-noble에서 v1.58.0-noble로 업그레이드. PR [#2150](https://github.com/fastapi/full-stack-fastapi-template/pull/2150) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ @tanstack/react-router 1.153.2에서 1.156.0으로 업그레이드. PR [#2152](https://github.com/fastapi/full-stack-fastapi-template/pull/2152) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ zod 4.3.5에서 4.3.6으로 업그레이드. PR [#2151](https://github.com/fastapi/full-stack-fastapi-template/pull/2151) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ @types/node 25.0.9에서 25.0.10으로 업그레이드. PR [#2149](https://github.com/fastapi/full-stack-fastapi-template/pull/2149) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ @tanstack/react-router-devtools 1.153.2에서 1.156.0으로 업그레이드. PR [#2147](https://github.com/fastapi/full-stack-fastapi-template/pull/2147) by [@dependabot[bot]](https://github.com/apps/dependabot).

## 0.10.0

### 기능

* ✅ 아이템 및 관리자 테스트 추가, 기존 테스트 리팩토링. PR [#2146](https://github.com/fastapi/full-stack-fastapi-template/pull/2146) by [@alejsdev](https://github.com/alejsdev).
* ✨ User 및 Item 모델에 created_at 필드 추가 및 엔드포인트 업데이트. PR [#2144](https://github.com/fastapi/full-stack-fastapi-template/pull/2144) by [@alejsdev](https://github.com/alejsdev).
* 🔧 npm에서 Bun으로 마이그레이션. PR [#2097](https://github.com/fastapi/full-stack-fastapi-template/pull/2097) by [@alejsdev](https://github.com/alejsdev).
* 🔧 node 모노레포 설정. PR [#2095](https://github.com/fastapi/full-stack-fastapi-template/pull/2095) by [@alejsdev](https://github.com/alejsdev).
* 🧑‍💻 uv 워크스페이스 구현. PR [#2090](https://github.com/fastapi/full-stack-fastapi-template/pull/2090) by [@alejsdev](https://github.com/alejsdev).
* 🔧 권장 VS Code 확장 추가. PR [#1386](https://github.com/fastapi/full-stack-fastapi-template/pull/1386) by [@tobiase](https://github.com/tobiase).
* ✨ 기본적으로 Argon2와 함께 pwdlib 사용, Bcrypt를 사용하는 기존 비밀번호 자동 업데이트 로직(및 테스트) 추가. PR [#2104](https://github.com/fastapi/full-stack-fastapi-template/pull/2104) by [@tiangolo](https://github.com/tiangolo).
* 🔨 pre-commit에서 프론트엔드 SDK 생성, 커스텀 워크플로우 제거. PR [#2111](https://github.com/fastapi/full-stack-fastapi-template/pull/2111) by [@tiangolo](https://github.com/tiangolo).

### 수정

* 🐛 비슈퍼유저 접근 제한을 위해 관리자 라우트에 사용자 인증 확인 추가. PR [#2145](https://github.com/fastapi/full-stack-fastapi-template/pull/2145) by [@alejsdev](https://github.com/alejsdev).
* 🐛 `read_user_by_id`에서 존재하지 않는 사용자 ID 처리. PR [#1396](https://github.com/fastapi/full-stack-fastapi-template/pull/1396) by [@saltie2193](https://github.com/saltie2193).

### 리팩토링

* 🔥 권장 확장에서 debugpy 제거, Python 확장에 포함됨. PR [#2143](https://github.com/fastapi/full-stack-fastapi-template/pull/2143) by [@tiangolo](https://github.com/tiangolo).
* 🔧 새로운 최상위 설정으로 프로덕션용 프론트엔드 빌드 컨텍스트 업데이트. PR [#2108](https://github.com/fastapi/full-stack-fastapi-template/pull/2108) by [@tiangolo](https://github.com/tiangolo).
* 🚚 Docker Compose 파일을 새 이름인 `compose.yml`로 변경. PR [#2106](https://github.com/fastapi/full-stack-fastapi-template/pull/2106) by [@tiangolo](https://github.com/tiangolo).
* 🔒️ 열거 공격 방지를 위해 인증이 일정 시간이 걸리도록 보장. PR [#2105](https://github.com/fastapi/full-stack-fastapi-template/pull/2105) by [@tiangolo](https://github.com/tiangolo).
* ✅ 단위 테스트의 잘못된 모킹 수정 (이슈 #1780). PR [#1781](https://github.com/fastapi/full-stack-fastapi-template/pull/1781) by [@vicaya](https://github.com/vicaya).
* 🐛 권한 부족 시 `items.py`가 상태 코드 `403`을 반환하도록 업데이트. PR [#1543](https://github.com/fastapi/full-stack-fastapi-template/pull/1543) by [@jpizquierdo](https://github.com/jpizquierdo).
* ✅ `test_user.py`에서 적절한 `is_active` 필드 사용. PR [#1479](https://github.com/fastapi/full-stack-fastapi-template/pull/1479) by [@nauanbek](https://github.com/nauanbek).
* ♻️ 중복 코드 제거로 비밀번호 재설정 로직 간소화. PR [#1440](https://github.com/fastapi/full-stack-fastapi-template/pull/1440) by [@youneshenniwrites](https://github.com/youneshenniwrites).

### 업그레이드

* ⬆ postgres 17에서 18로 업그레이드. PR [#1910](https://github.com/fastapi/full-stack-fastapi-template/pull/1910) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ traefik 3.0에서 3.6으로 업그레이드. PR [#1973](https://github.com/fastapi/full-stack-fastapi-template/pull/1973) by [@dependabot[bot]](https://github.com/apps/dependabot).

### 문서

* 📝 배포 문서 업데이트. PR [#2109](https://github.com/fastapi/full-stack-fastapi-template/pull/2109) by [@tiangolo](https://github.com/tiangolo).

### 내부

* 🎨 Python 스크립트 테스트 포맷팅. PR [#2112](https://github.com/fastapi/full-stack-fastapi-template/pull/2112) by [@tiangolo](https://github.com/tiangolo).
* 🔨 generate-client.sh 및 문서 업데이트. PR [#2110](https://github.com/fastapi/full-stack-fastapi-template/pull/2110) by [@tiangolo](https://github.com/tiangolo).
* 🔥 사용하지 않는 이전 스크립트 제거. PR [#2107](https://github.com/fastapi/full-stack-fastapi-template/pull/2107) by [@tiangolo](https://github.com/tiangolo).
* 👷 이슈 관리자용 `maybe-ai` 추가. PR [#2103](https://github.com/fastapi/full-stack-fastapi-template/pull/2103) by [@tiangolo](https://github.com/tiangolo).
* ⬆️ Dockerfile에서 uv를 0.9.26으로 업그레이드. PR [#2102](https://github.com/fastapi/full-stack-fastapi-template/pull/2102) by [@alejsdev](https://github.com/alejsdev).
* ⬆ lucide-react 0.556.0에서 0.562.0으로 업그레이드. PR [#2101](https://github.com/fastapi/full-stack-fastapi-template/pull/2101) by [@dependabot[bot]](https://github.com/apps/dependabot).
* 🔧 패키지 에코시스템용 dependabot 설정 업데이트. PR [#2100](https://github.com/fastapi/full-stack-fastapi-template/pull/2100) by [@alejsdev](https://github.com/alejsdev).
* 🔧 Biome 스키마 버전을 2.3.11로 업데이트. PR [#2099](https://github.com/fastapi/full-stack-fastapi-template/pull/2099) by [@alejsdev](https://github.com/alejsdev).
* 🔧 `package.json`에 테스트 스크립트 추가. PR [#2098](https://github.com/fastapi/full-stack-fastapi-template/pull/2098) by [@alejsdev](https://github.com/alejsdev).
* 🎨 pre-commit 수정 적용. PR [#2055](https://github.com/fastapi/full-stack-fastapi-template/pull/2055) by [@GniLudio](https://github.com/GniLudio).
* 👷 pre-commit 워크플로우 업데이트. PR [#2096](https://github.com/fastapi/full-stack-fastapi-template/pull/2096) by [@alejsdev](https://github.com/alejsdev).
* 🔧 biome.json 스키마 버전 업데이트. PR [#2092](https://github.com/fastapi/full-stack-fastapi-template/pull/2092) by [@alejsdev](https://github.com/alejsdev).
* "🔧 pre-commit-config.yaml ruff format에 --check 사용" 되돌리기. PR [#2091](https://github.com/fastapi/full-stack-fastapi-template/pull/2091) by [@alejsdev](https://github.com/alejsdev).
* 🔧 pre-commit-config.yaml ruff format에 --check 사용하도록 업데이트. PR [#2077](https://github.com/fastapi/full-stack-fastapi-template/pull/2077) by [@ryansydnor](https://github.com/ryansydnor).
* ⬆ actions/checkout 5에서 6으로 업그레이드. PR [#2074](https://github.com/fastapi/full-stack-fastapi-template/pull/2074) by [@dependabot[bot]](https://github.com/apps/dependabot).
* 👷 pre-commit 워크플로우 추가. PR [#2056](https://github.com/fastapi/full-stack-fastapi-template/pull/2056) by [@YuriiMotov](https://github.com/YuriiMotov).
* ⬆ /frontend에서 @tanstack/router-devtools 1.140.0에서 1.142.8로 업그레이드. PR [#2060](https://github.com/fastapi/full-stack-fastapi-template/pull/2060) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/react-router 1.141.2에서 1.142.8로 업그레이드. PR [#2062](https://github.com/fastapi/full-stack-fastapi-template/pull/2062) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @biomejs/biome 2.3.8에서 2.3.10으로 업그레이드. PR [#2061](https://github.com/fastapi/full-stack-fastapi-template/pull/2061) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/react-router-devtools 1.139.12에서 1.142.8로 업그레이드. PR [#2063](https://github.com/fastapi/full-stack-fastapi-template/pull/2063) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 zod 4.1.13에서 4.2.1로 업그레이드. PR [#2064](https://github.com/fastapi/full-stack-fastapi-template/pull/2064) by [@dependabot[bot]](https://github.com/apps/dependabot).
* 👷 커버리지 설정, 메인 테스트 오류 시 에러, Smokeshow 대기 안 함. PR [#2054](https://github.com/fastapi/full-stack-fastapi-template/pull/2054) by [@YuriiMotov](https://github.com/YuriiMotov).
* 👷 테스트 실패 시에도 Smokeshow 항상 실행. PR [#2053](https://github.com/fastapi/full-stack-fastapi-template/pull/2053) by [@YuriiMotov](https://github.com/YuriiMotov).
* ⬆ /frontend에서 @tanstack/react-router 1.140.0에서 1.141.2로 업그레이드. PR [#2045](https://github.com/fastapi/full-stack-fastapi-template/pull/2045) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ actions/download-artifact 6에서 7로 업그레이드. PR [#2051](https://github.com/fastapi/full-stack-fastapi-template/pull/2051) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ actions/upload-artifact 5에서 6으로 업그레이드. PR [#2050](https://github.com/fastapi/full-stack-fastapi-template/pull/2050) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @types/node 24.10.1에서 25.0.2로 업그레이드. PR [#2048](https://github.com/fastapi/full-stack-fastapi-template/pull/2048) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tailwindcss/vite 4.1.17에서 4.1.18로 업그레이드. PR [#2049](https://github.com/fastapi/full-stack-fastapi-template/pull/2049) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 vite 7.2.7에서 7.3.0으로 업그레이드. PR [#2047](https://github.com/fastapi/full-stack-fastapi-template/pull/2047) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 react-dom 19.2.1에서 19.2.3으로 업그레이드. PR [#2046](https://github.com/fastapi/full-stack-fastapi-template/pull/2046) by [@dependabot[bot]](https://github.com/apps/dependabot).

## 0.9.0

### 기능

* ✨ 모든 페이지에 메타 타이틀 지원 추가. PR [#2039](https://github.com/fastapi/full-stack-fastapi-template/pull/2039) by [@alejsdev](https://github.com/alejsdev).
* 🛂 프론트엔드를 Shadcn으로 마이그레이션. PR [#2010](https://github.com/fastapi/full-stack-fastapi-template/pull/2010) by [@alejsdev](https://github.com/alejsdev).

### 수정

* 🐛 `EMAILS_FROM_NAME` 타입을 `EmailStr` 대신 `str`로 수정. PR [#1940](https://github.com/fastapi/full-stack-fastapi-template/pull/1940) by [@martin0258](https://github.com/martin0258).
* 🐛 빈 문자열과 빈 리스트 모두에서 일관되도록 `parse_cors` 함수 수정. PR [#1672](https://github.com/fastapi/full-stack-fastapi-template/pull/1672) by [@rolkotaki](https://github.com/rolkotaki).
* 🐛 사용자 선택 시 사이드바 드로어 닫기. PR [#1515](https://github.com/fastapi/full-stack-fastapi-template/pull/1515) by [@dtellz](https://github.com/dtellz).
* 🐛 사용자 필드 편집 시 필수 비밀번호 유효성 검사 수정. PR [#1508](https://github.com/fastapi/full-stack-fastapi-template/pull/1508) by [@jpizquierdo](https://github.com/jpizquierdo).

### 리팩토링

* ♻️ 비밀번호 최대 길이 업데이트. PR [#1447](https://github.com/fastapi/full-stack-fastapi-template/pull/1447) by [@michaelAlvarino](https://github.com/michaelAlvarino).
* 🚚 백엔드 테스트를 `app` 디렉터리 외부로 이동. PR [#1862](https://github.com/fastapi/full-stack-fastapi-template/pull/1862) by [@YuriiMotov](https://github.com/YuriiMotov).
* ✨ Vite 환경 변수용 ImportMetaEnv 및 ImportMeta 인터페이스 추가. PR [#1860](https://github.com/fastapi/full-stack-fastapi-template/pull/1860) by [@alejsdev](https://github.com/alejsdev).
* 🔧 `tsconfig.json` 업데이트 및 오류 수정. PR [#1859](https://github.com/fastapi/full-stack-fastapi-template/pull/1859) by [@alejsdev](https://github.com/alejsdev).
* ♻️ ChangePassword 컴포넌트에서 Save 버튼의 disabled 속성 제거. PR [#1844](https://github.com/fastapi/full-stack-fastapi-template/pull/1844) by [@alejsdev](https://github.com/alejsdev).
* 👷🏻‍♀️ 클라이언트 생성용 CI 업데이트. PR [#1573](https://github.com/fastapi/full-stack-fastapi-template/pull/1573) by [@alejsdev](https://github.com/alejsdev).
* ♻️ 상속 클래스에서 중복 필드 제거. PR [#1520](https://github.com/fastapi/full-stack-fastapi-template/pull/1520) by [@tzway](https://github.com/tzway).
* 🎨 Skeleton 및 기타 컴포넌트에 사소한 UI 조정 추가. PR [#1507](https://github.com/fastapi/full-stack-fastapi-template/pull/1507) by [@alejsdev](https://github.com/alejsdev).
* 🎨 사소한 UI 조정 추가. PR [#1506](https://github.com/fastapi/full-stack-fastapi-template/pull/1506) by [@alejsdev](https://github.com/alejsdev).

### 업그레이드

* ⬆ /frontend에서 @types/react 19.1.12에서 19.1.13으로 업그레이드. PR [#1888](https://github.com/fastapi/full-stack-fastapi-template/pull/1888) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/router-plugin 1.131.41에서 1.131.43으로 업그레이드. PR [#1887](https://github.com/fastapi/full-stack-fastapi-template/pull/1887) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /backend에서 pydantic 2.11.7에서 2.11.9로 업그레이드. PR [#1891](https://github.com/fastapi/full-stack-fastapi-template/pull/1891) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @chakra-ui/react 3.26.0에서 3.27.0으로 업그레이드. PR [#1890](https://github.com/fastapi/full-stack-fastapi-template/pull/1890) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 axios 1.12.0에서 1.12.2로 업그레이드. PR [#1889](https://github.com/fastapi/full-stack-fastapi-template/pull/1889) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @types/node 24.3.1에서 24.4.0으로 업그레이드. PR [#1886](https://github.com/fastapi/full-stack-fastapi-template/pull/1886) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/router-devtools 1.131.41에서 1.131.42로 업그레이드. PR [#1881](https://github.com/fastapi/full-stack-fastapi-template/pull/1881) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/router-plugin 1.131.39에서 1.131.41로 업그레이드. PR [#1879](https://github.com/fastapi/full-stack-fastapi-template/pull/1879) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/react-query-devtools 5.87.3에서 5.87.4로 업그레이드. PR [#1876](https://github.com/fastapi/full-stack-fastapi-template/pull/1876) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 axios 1.11.0에서 1.12.0으로 업그레이드. PR [#1878](https://github.com/fastapi/full-stack-fastapi-template/pull/1878) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/router-devtools 1.131.40에서 1.131.41로 업그레이드. PR [#1877](https://github.com/fastapi/full-stack-fastapi-template/pull/1877) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/react-router 1.131.40에서 1.131.41로 업그레이드. PR [#1875](https://github.com/fastapi/full-stack-fastapi-template/pull/1875) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/router-devtools 1.131.36에서 1.131.37로 업그레이드. PR [#1871](https://github.com/fastapi/full-stack-fastapi-template/pull/1871) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/router-plugin 1.131.36에서 1.131.37로 업그레이드. PR [#1870](https://github.com/fastapi/full-stack-fastapi-template/pull/1870) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/react-query 5.87.1에서 5.87.4로 업그레이드. PR [#1868](https://github.com/fastapi/full-stack-fastapi-template/pull/1868) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @biomejs/biome 2.2.3에서 2.2.4로 업그레이드. PR [#1869](https://github.com/fastapi/full-stack-fastapi-template/pull/1869) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/react-router 1.131.36에서 1.131.37로 업그레이드. PR [#1872](https://github.com/fastapi/full-stack-fastapi-template/pull/1872) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆️ Biome를 최신 버전으로 업그레이드. PR [#1861](https://github.com/fastapi/full-stack-fastapi-template/pull/1861) by [@alejsdev](https://github.com/alejsdev).
* ⬆️ TanStack Router 종속성 업데이트. PR [#1853](https://github.com/fastapi/full-stack-fastapi-template/pull/1853) by [@alejsdev](https://github.com/alejsdev).
* ⬆️ @tanstack/react-query 5.28.14에서 5.87.1로 업그레이드. PR [#1852](https://github.com/fastapi/full-stack-fastapi-template/pull/1852) by [@alejsdev](https://github.com/alejsdev).
* ⬆ /frontend에서 @chakra-ui/react 3.8.0에서 3.26.0으로 업그레이드. PR [#1796](https://github.com/fastapi/full-stack-fastapi-template/pull/1796) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆️ @hey-api/openapi-ts 종속성 버전 업데이트 및 dependabot 설정 업데이트. PR [#1845](https://github.com/fastapi/full-stack-fastapi-template/pull/1845) by [@alejsdev](https://github.com/alejsdev).
* ⬆️ Playwright 업데이트. PR [#1793](https://github.com/fastapi/full-stack-fastapi-template/pull/1793) by [@alejsdev](https://github.com/alejsdev).
* ⬆️ React 및 관련 종속성 업그레이드. PR [#1843](https://github.com/fastapi/full-stack-fastapi-template/pull/1843) by [@alejsdev](https://github.com/alejsdev).

### 문서

* 📝 로컬 이메일 테스트용 Mailcatcher 설정 지침 추가. PR [#2038](https://github.com/fastapi/full-stack-fastapi-template/pull/2038) by [@alejsdev](https://github.com/alejsdev).
* 📝 Vite 링크를 포함하도록 `README` 업데이트. PR [#2037](https://github.com/fastapi/full-stack-fastapi-template/pull/2037) by [@alejsdev](https://github.com/alejsdev).
* 📝 오래된 워크플로우 배지 수정. PR [#2028](https://github.com/fastapi/full-stack-fastapi-template/pull/2028) by [@AymanAlSuleihi](https://github.com/AymanAlSuleihi).
* 📝 문서 업데이트. PR [#2036](https://github.com/fastapi/full-stack-fastapi-template/pull/2036) by [@alejsdev](https://github.com/alejsdev).
* ✏️ `deployment.md`의 작은 오타 수정. PR [#1679](https://github.com/fastapi/full-stack-fastapi-template/pull/1679) by [@cassmtnr](https://github.com/cassmtnr).

### 내부

* 🔥 사용하지 않는 종속성 제거. PR [#2035](https://github.com/fastapi/full-stack-fastapi-template/pull/2035) by [@alejsdev](https://github.com/alejsdev).
* ⬆ /frontend에서 react-dom 19.2.0에서 19.2.1로 업그레이드. PR [#2032](https://github.com/fastapi/full-stack-fastapi-template/pull/2032) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 vite 7.2.6에서 7.2.7로 업그레이드. PR [#2033](https://github.com/fastapi/full-stack-fastapi-template/pull/2033) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/router-plugin 1.139.12에서 1.140.0으로 업그레이드. PR [#2034](https://github.com/fastapi/full-stack-fastapi-template/pull/2034) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 lucide-react 0.555.0에서 0.556.0으로 업그레이드. PR [#2031](https://github.com/fastapi/full-stack-fastapi-template/pull/2031) by [@dependabot[bot]](https://github.com/apps/dependabot).
* 🔧 biome 설정에 Tailwind CSS 지시어 지원 추가. PR [#2029](https://github.com/fastapi/full-stack-fastapi-template/pull/2029) by [@alejsdev](https://github.com/alejsdev).
* ⬆ /frontend에서 react-hook-form 7.66.1에서 7.67.0으로 업그레이드. PR [#2018](https://github.com/fastapi/full-stack-fastapi-template/pull/2018) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/react-query 5.90.10에서 5.90.11로 업그레이드. PR [#2019](https://github.com/fastapi/full-stack-fastapi-template/pull/2019) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 axios 1.12.2에서 1.13.2로 업그레이드. PR [#2020](https://github.com/fastapi/full-stack-fastapi-template/pull/2020) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/router-devtools 1.139.3에서 1.139.12로 업그레이드. PR [#2021](https://github.com/fastapi/full-stack-fastapi-template/pull/2021) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 playwright v1.56.1-noble에서 v1.57.0-noble로 업그레이드. PR [#2016](https://github.com/fastapi/full-stack-fastapi-template/pull/2016) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆️ `biome.json`의 스키마 버전 업데이트. PR [#2017](https://github.com/fastapi/full-stack-fastapi-template/pull/2017) by [@alejsdev](https://github.com/alejsdev).
* ⬆ /frontend에서 vite 7.2.2에서 7.2.6으로 업그레이드. PR [#2015](https://github.com/fastapi/full-stack-fastapi-template/pull/2015) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @biomejs/biome 2.3.7에서 2.3.8로 업그레이드. PR [#2014](https://github.com/fastapi/full-stack-fastapi-template/pull/2014) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/react-query-devtools 5.91.0에서 5.91.1로 업그레이드. PR [#2013](https://github.com/fastapi/full-stack-fastapi-template/pull/2013) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/router-plugin 1.133.15에서 1.139.12로 업그레이드. PR [#2012](https://github.com/fastapi/full-stack-fastapi-template/pull/2012) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 form-data 4.0.4에서 4.0.5로 업그레이드. PR [#2011](https://github.com/fastapi/full-stack-fastapi-template/pull/2011) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ actions/checkout 5에서 6으로 업그레이드. PR [#2007](https://github.com/fastapi/full-stack-fastapi-template/pull/2007) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @types/react 19.2.2에서 19.2.7로 업그레이드. PR [#2003](https://github.com/fastapi/full-stack-fastapi-template/pull/2003) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/router-devtools 1.131.42에서 1.139.3으로 업그레이드. PR [#2001](https://github.com/fastapi/full-stack-fastapi-template/pull/2001) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 typescript 5.9.2에서 5.9.3으로 업그레이드. PR [#2002](https://github.com/fastapi/full-stack-fastapi-template/pull/2002) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @types/react-dom 19.2.2에서 19.2.3으로 업그레이드. PR [#2004](https://github.com/fastapi/full-stack-fastapi-template/pull/2004) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @types/node 24.10.0에서 24.10.1로 업그레이드. PR [#2005](https://github.com/fastapi/full-stack-fastapi-template/pull/2005) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /backend에서 pydantic-settings 2.11.0에서 2.12.0으로 업그레이드. PR [#2000](https://github.com/fastapi/full-stack-fastapi-template/pull/2000) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /backend에서 alembic 1.17.1에서 1.17.2로 업그레이드. PR [#1999](https://github.com/fastapi/full-stack-fastapi-template/pull/1999) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @biomejs/biome 2.2.4에서 2.3.7로 업그레이드. PR [#1998](https://github.com/fastapi/full-stack-fastapi-template/pull/1998) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 react-hook-form 7.66.0에서 7.66.1로 업그레이드. PR [#1997](https://github.com/fastapi/full-stack-fastapi-template/pull/1997) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @vitejs/plugin-react-swc 4.2.1에서 4.2.2로 업그레이드. PR [#1996](https://github.com/fastapi/full-stack-fastapi-template/pull/1996) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @chakra-ui/react 3.29.0에서 3.30.0으로 업그레이드. PR [#1995](https://github.com/fastapi/full-stack-fastapi-template/pull/1995) by [@dependabot[bot]](https://github.com/apps/dependabot).
* ⬆ /frontend에서 @tanstack/react-query-devtools 5.90.2에서 5.91.0으로 업그레이드. PR [#1994](https://github.com/fastapi/full-stack-fastapi-template/pull/1994) by [@dependabot[bot]](https://github.com/apps/dependabot).
* 🔧 Dependabot 업데이트에 라벨 추가. PR [#1992](https://github.com/fastapi/full-stack-fastapi-template/pull/1992) by [@alejsdev](https://github.com/alejsdev).

(이하 생략 - 파일이 너무 길어 주요 버전만 포함)

## 0.8.0

### 기능

* 🛂 Chakra UI v3로 마이그레이션. PR [#1496](https://github.com/fastapi/full-stack-fastapi-template/pull/1496) by [@alejsdev](https://github.com/alejsdev).
* ✨ E2E 테스트에서 사용하기 위한 비공개, 로컬 전용 API 추가. PR [#1429](https://github.com/fastapi/full-stack-fastapi-template/pull/1429) by [@patrick91](https://github.com/patrick91).
* ✨ 최신 openapi-ts로 마이그레이션. PR [#1430](https://github.com/fastapi/full-stack-fastapi-template/pull/1430) by [@patrick91](https://github.com/patrick91).

## 0.7.1

### 하이라이트

* Poetry에서 [`uv`](https://github.com/astral-sh/uv)로 마이그레이션.
* Docker Compose 파일, Traefik Dockerfile 간소화 및 개선.
* API가 자체 도메인 `api.example.com`을 사용하고 프론트엔드가 `dashboard.example.com`을 사용하도록 변경. 필요한 경우 별도로 배포하기 쉬워짐.
* Docker Compose의 백엔드와 프론트엔드가 이제 로컬 개발 서버와 동일한 포트에서 수신 대기하므로, Docker Compose 서비스를 중지하고 프론트엔드 설정 변경 없이 로컬 개발 서버를 실행할 수 있음.

## 0.7.0

많은 새로운 기능! 🎁

* Playwright를 사용한 E2E 테스트.
* 이메일 처리 개발 및 테스트를 위한 Mailcatcher 설정.
* 페이지네이션.
* 데이터베이스 키용 UUID.
* 새 사용자 가입.
* 여러 환경(staging, prod)에 배포 지원.
* 많은 리팩토링 및 개선.
* 여러 종속성 업그레이드.

## 0.6.0

최신 FastAPI, Pydantic, SQLModel 🚀

React, TS, Vite, Chakra UI, TanStack Query/Router, 생성된 클라이언트/SDK를 사용한 새로운 프론트엔드 🎨

CI/CD - GitHub Actions 🤖

테스트 커버리지 > 90% ✅

## 0.5.0

* Traefik 공용 네트워크를 DockerSwarm.rocks에서와 같이 `traefik-public`의 고정 기본값으로 설정하여 프로젝트 생성기의 개발 및 반복을 간소화.
* PostgreSQL 12로 업데이트.
* 패키지 관리에 Poetry 사용.
* 프로젝트 생성 후 Cookiecutter 훅으로 셸 스크립트의 Windows 줄 끝 수정.
* Vue CLI 버전 4로 업그레이드.

## 0.4.0

* 비밀번호 재설정 보안 수정. 토큰을 쿼리가 아닌 본문으로 수신.

## 0.3.0

* CRUD 유틸리티 업데이트로 타입 더 잘 사용.
* Pydantic 모델 이름 간소화, `UserInCreate`에서 `UserCreate` 등으로.
* 패키지 업그레이드.
* 새로운 일반 "Items" 모델, CRUD 유틸리티, 엔드포인트 및 테스트 추가.

## 0.2.0

* 백엔드 `Dockerfile` 간소화 및 업데이트.
* 백엔드 코드 리팩토링 및 간소화, 이름 지정, 임포트, 모듈 및 "네임스페이스" 개선.
* TypeScript 접근자로 Vuex 통합 개선 및 간소화.
* 프론트엔드 컴포넌트 레이아웃, 버튼 순서 등 표준화.

## 0.1.2

* 자기 자신 사용자를 업데이트하는 경로 작업 수정, 매개변수를 본문 페이로드로 설정.

## 0.1.1

초기 게시 이후 여러 버그 수정:

* 사용자용 경로 작업 순서.
* 프론트엔드가 올바른 형식으로 로그인 데이터 전송.
* CORS에 https://localhost 변형 추가.
