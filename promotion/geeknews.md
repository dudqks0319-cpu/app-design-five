# 긱뉴스 Show GN 게시 초안

상태: **초안 — 게시하지 않음**. 아래 제목·링크·본문을 Show GN에 사용하면 됩니다. 본인이 만든 프로젝트를 Show GN에 올리라는 [긱뉴스 가이드라인](https://news.hada.io/guidelines)에 맞췄습니다.

## 제목

App Design Five — 앱 구현 전에 이미지 시안 5장을 고르는 Codex 스킬

## 링크

[GitHub 저장소](https://github.com/dudqks0319-cpu/app-design-five)

## 본문

AI에게 앱 화면을 부탁하면 첫 시안 하나를 계속 수정하게 되는 경우가 많았습니다. 그래서 제가 쓰던 “이미지 시안 5장부터 보고 고르기” 흐름을 Codex 스킬로 공개했습니다.

App Design Five는 같은 앱의 핵심 화면을 서로 다른 다섯 방향으로 먼저 생성합니다. 색만 바꾸는 대신 목록 구조, 정보 밀도, 글자, 주요 동작의 위치 등을 비교합니다. “1번 구조에 4번 색감”처럼 선택하거나 섞은 뒤 OpenDesign의 Local Codex 모드에서 디자인을 만들고, 요청한 범위만큼 앱에 반영합니다.

이번에는 가상의 할 일 앱 “오늘 한 걸음”으로 직접 실행했습니다.

- Codex 내장 이미지 도구로 시안 5장을 각각 생성했습니다.
- 2번 방향으로 OpenDesign(Local Codex)에서 조작 가능한 앱을 만들었습니다.
- 실제 Aside 브라우저에서 추가·완료·삭제, 새로고침 후 저장, 잘못된 입력과 저장 오류 대응 등 15개 확인 항목이 통과했습니다.
- 다섯 원본 이미지, 실제 화면 캡처, HTML 앱과 검증 기록을 저장소에 넣었습니다. 내려받아 브라우저에서 실행할 수 있습니다.

실행 중 OpenDesign의 브리프가 MCP 연결을 끊으면 사라지는 조건도 발견해 안내에 반영했습니다. 시작된 작업은 같은 식별자로 다시 조회할 수 있었습니다.

스킬 자체는 별도 MCP 서버나 이미지 엔진이 아닙니다. Codex 이미지 도구와 설치·인증된 OpenDesign이 필요합니다. 검증은 이 데모 한 사례이고 실제 휴대폰·다른 브라우저·외부 설치 CLI는 아직 확인하지 않았습니다.

MIT 라이선스이며 한국어·영어·중국어·일본어 사용 안내를 제공합니다.

[데모와 검증 기록](https://github.com/dudqks0319-cpu/app-design-five/tree/main/demo)

비슷한 이미지 우선 작업을 해보신 분들의 피드백을 받고 싶습니다. 시안 비교나 OpenDesign 전달에서 빠진 부분이 있다면 알려주세요.

## 본문에 넣을 이미지 링크

긱뉴스 본문은 이미지를 지원하지 않으므로 아래 GitHub 이미지 링크를 사용합니다. 비교 이미지는 생성 시안이고 두 번째는 실제 브라우저 화면이라는 설명을 함께 붙입니다.

[다섯 시안 비교](https://github.com/dudqks0319-cpu/app-design-five/blob/main/demo/screenshots/five-concepts.png) · [실제 구현 화면](https://github.com/dudqks0319-cpu/app-design-five/blob/main/demo/screenshots/mobile-390x844.png)
