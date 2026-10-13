# App Design Five

[한국어](README.md) · [English](README.en.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md)

**앱을 만들기 전에 실제 이미지 시안 5장을 보고 고르는 AI 에이전트 스킬.**

이미지 5장 → 선택·혼합 의견 → 디자인 제작 → 요청한 앱 구현

같은 앱의 핵심 화면을 서로 다른 다섯 방향으로 비교합니다. “1번 구조에 4번 색감”처럼 고르거나 섞은 뒤, 선택한 방향을 OpenDesign(Local Codex)에서 디자인으로 만들고 요청한 범위에 맞춰 앱에 반영합니다. 단순 버그 수정이나 상태 질문에는 이 흐름을 시작하지 않습니다.

## 실제 실행 데모

가상의 할 일 앱 **“오늘 한 걸음”**으로 실제 이미지 5장 생성 → 시안 선택 → OpenDesign(Local Codex) 앱 생성을 실행했습니다. 사용자가 선택을 맡겨 2번을 골랐고, Aside 브라우저에서 기능·저장·오류·화면 크기 관련 **15개 확인 항목이 통과**했습니다.

![같은 앱의 다섯 가지 실제 생성 시안](demo/screenshots/five-concepts.png)

<img src="demo/screenshots/mobile-390x844.png" width="300" alt="선택한 2번 방향으로 생성된 실제 앱의 390×844 브라우저 화면">

[데모 실행 방법과 검증 기록](demo/README.md) · [앱 HTML](demo/app/index.html) · [긱뉴스 초안](promotion/geeknews.md) · [Threads 초안](promotion/threads.md)

GitHub의 HTML 파일 화면은 소스 보기입니다. 저장소를 내려받아 `demo/app/index.html`을 브라우저로 열면 앱을 조작할 수 있습니다. 모바일 이미지는 390×844 브라우저 프레임이며 실제 휴대폰 검증은 아직 하지 않았습니다.

## 작업 순서

1. 앱의 목적·플랫폼·핵심 화면·필수 기능을 정리합니다.
2. Codex 이미지 도구로 레이아웃과 정보 구성이 다른 **실제 이미지 5장**을 생성해 보여줍니다.
3. 사용자가 번호를 고르거나 방향을 섞고 수정 의견을 줍니다. 선택 없이 다음 디자인을 시작하지 않습니다.
4. 선택한 방향으로 OpenDesign 디자인을 만듭니다. 기본 실행 방식은 **Local Codex**입니다.
5. 앱 구현까지 요청했다면 실제 화면과 기능에 반영합니다. 디자인만 요청했다면 그 범위에서 마칩니다.

## 스킬과 MCP

| 형태 | 역할 | 이 프로젝트 |
| --- | --- | --- |
| 스킬 | AI에게 작업 순서와 기준을 알려줍니다. | `SKILL.md`와 참고 문서로 배포합니다. |
| MCP | AI가 프로그램의 도구나 자료를 이용하도록 연결합니다. | 디자인 단계에서 기존 OpenDesign 연결을 사용합니다. |

이 저장소는 **스킬 패키지**입니다. 별도의 MCP 서버, 이미지 엔진, OpenDesign 프로그램, API 키나 생성 크레딧을 포함하지 않습니다.

## 필요한 환경

| 환경 | 스킬 문서 | 이미지 생성 | 디자인·구현 |
| --- | --- | --- | --- |
| Codex | 공통 Agent Skills 형식 | 설치된 `imagegen` 스킬과 내장 이미지 도구가 필요 | 설치·인증된 OpenDesign + Local Codex |

스킬과 이미지 생성은 **Codex**, 선택한 디자인 제작은 **OpenDesign(Local Codex)**에서 진행합니다. 스킬 설치만으로 OpenDesign이 설치되거나 인증되지는 않습니다. 도구가 없는 단계는 미완료로 알리고, 유료 API·Cloud·BYOK로 자동 전환하지 않습니다.

## 설치

기존 `skills` CLI를 이용하는 선택 경로입니다. Node.js/npm이 필요하며, 이 명령은 외부 설치 도구를 실행합니다.

```sh
npx skills add dudqks0319-cpu/app-design-five --skill app-design-five -g -a codex
```

별도 설치 도구 없이 쓰려면 GitHub에서 ZIP을 내려받거나 저장소를 복제한 후 **저장소 폴더 안에서** 다음을 실행합니다. 같은 이름의 기존 스킬은 덮어쓰지 않습니다.

```sh
mkdir -p "$HOME/.agents/skills"
if [ -e "$HOME/.agents/skills/app-design-five" ] || [ -L "$HOME/.agents/skills/app-design-five" ]; then
  echo '같은 이름의 스킬이 있습니다. 기존 내용을 먼저 확인하세요.'
else
  mkdir "$HOME/.agents/skills/app-design-five" &&
  cp -R SKILL.md LICENSE agents references "$HOME/.agents/skills/app-design-five/"
fi
```

프로젝트에서만 쓰려면 같은 파일을 `.agents/skills/app-design-five/`에 둡니다. 전역과 프로젝트에 같은 이름을 중복 설치하지 마세요. 설치 후 현재 호스트의 스킬 목록에서 확인합니다.

## 사용 예

```text
$app-design-five로 가계부 앱을 만들어줘.
먼저 이미지 시안 5장을 보여주고 내가 고르면 OpenDesign으로 이어가줘.
```

```text
$app-design-five로 디자인만 제안해줘. 코드는 아직 수정하지 마.
```

```text
1번의 목록 구조와 4번의 색감을 섞어줘. 글자는 더 크게 해줘.
```

준비된 이미지로 OpenDesign 제작을 이어가는 예:

```text
$app-design-five를 사용해줘. 준비된 이미지 중 3번을 선택할게.
이 방향으로 OpenDesign(Local Codex)에서 디자인을 만들고 앱에 반영해줘.
```

사용자의 선택, 실행 방식, 구현·검증 범위를 유지합니다. 이 스킬 자체는 추가 에이전트, 결제, 공개 배포나 GitHub 게시를 승인하지 않습니다.

## 확인 범위

- 스킬 형식·내부 문서 링크·로컬 설치 파일 일치 확인을 마쳤으며, Codex 스킬 카탈로그에 노출된 것을 확인했습니다.
- 2026-10-13 위의 가상 앱 한 사례에서 실제 이미지 5장 → 선택 → OpenDesign(Local Codex) → 앱 산출물 → 실제 브라우저 검증을 마쳤습니다. 모든 앱·환경에 대한 보증은 아닙니다.
- OpenDesign 브리프 수집·확인·실행 시작은 같은 MCP 연결에서 진행해야 했습니다. 실행이 시작된 뒤에는 같은 식별자로 재연결해 결과를 조회했습니다. [실행에서 확인한 연결 조건](references/tool-routing.md#connection-and-artifact-handling-observed-in-the-demo)을 안내에 반영했습니다.
- 외부 설치 CLI 명령은 이 프로젝트에서 아직 검증하지 않았습니다.
- 이미지, 디자인 결과, 소스 구현, 로컬 검사, 실제 기기와 출시 상태를 각각 실제 근거에 따라 보고합니다. 검증을 생략하면 생략했다고 알립니다.

## 파일과 개인정보

스킬 실행 지침은 하나의 영어 `SKILL.md`로 유지하고, 사용 안내는 네 언어로 제공합니다. `agents/openai.yaml`은 Codex UI 메타데이터, `references/`는 도구 연결과 디자인 전달 안내입니다.

일반 작업의 생성 이미지와 개인 브리프는 각 앱의 로컬 작업 폴더에 저장합니다. 명시적으로 공개를 요청받은 이 가상 데모의 이미지·앱·정리된 검증 기록만 `demo/`에 포함했습니다. `.local/` 작업 기록, 개인 화면과 인증 정보는 배포 대상에서 제외합니다. 설치·백그라운드 스크립트, 원격 수집, 자동 업데이트 기능은 포함하지 않습니다. 데모 앱에는 브라우저 안에서만 동작하는 JavaScript와 로컬 저장 기능이 있습니다.

## 라이선스와 참고

[MIT 라이선스](LICENSE). 사용자에게 소개받은 [oil-ui](https://github.com/oil-oil/oil-ui)의 여러 방향 비교 취지를 참고한 독립 스킬입니다. 해당 저장소의 코드·스킬 본문·이미지를 포함하지 않았습니다.

[Agent Skills 표준](https://agentskills.io/home) · [Codex 스킬](https://learn.chatgpt.com/docs/build-skills) · [OpenDesign](https://open-design.ai/) · [skills CLI](https://github.com/vercel-labs/skills) · [MCP](https://modelcontextprotocol.io/docs/learn/architecture)
