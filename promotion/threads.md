# Threads 게시 초안

상태: **초안 — 게시하지 않음**. 첫 글에 실제 비교 이미지, 이어지는 답글에 구현 화면을 붙이는 구성입니다. 이미지에 설명을 함께 쓰는 방식은 [Threads 공식 제작자 안내](https://about.fb.com/news/2024/10/find-your-community-with-new-threads-educational-insights/amp/)를 참고했습니다. 아래 문안은 Star 증가를 보장하는 성과 주장이 아닙니다.

## 첫 글 — 다섯 시안 이미지와 함께

```text
AI한테 앱 화면을 부탁하면 첫 시안 하나를 계속 고치게 되더라고요.

그래서 제가 쓰던 흐름을 오픈소스 스킬로 만들었습니다.

이미지 시안 5장 → 마음에 드는 방향 선택 → OpenDesign(Local Codex) → 앱 구현.

이번엔 같은 할 일 앱으로 실제로 돌려봤어요. 아래 다섯 장은 각각 생성한 시안입니다. 여러분이라면 몇 번을 고르시겠어요?

이름은 App Design Five. 한국어·영어·중국어·일본어 안내를 넣었습니다.

https://github.com/dudqks0319-cpu/app-design-five
```

첨부: [다섯 시안 비교](../demo/screenshots/five-concepts.png)

## 이어지는 답글 — 실제 구현 화면과 함께

```text
검증용으로는 2번을 골랐습니다. 진행률·입력·목록이 잘 나뉘어 있어서요.

이 화면은 시안 이미지가 아니라 OpenDesign(Local Codex)에서 만든 실제 앱입니다. 추가·완료·삭제와 새로고침 후 저장, 오류 처리 등을 실제 브라우저에서 확인했고 15개 항목이 통과했습니다.

이미지 원본, 앱 HTML, 화면 캡처와 검증 기록도 공개했습니다. 실제 휴대폰 검증은 아직입니다.

도움이 되면 GitHub Star로 저장해 주세요. 써보면서 막힌 부분은 Issue로 남겨주시면 좋겠습니다.

https://github.com/dudqks0319-cpu/app-design-five/tree/main/demo
```

첨부: [실제 앱의 390×844 브라우저 화면](../demo/screenshots/mobile-390x844.png)

## 이미지 설명

- 비교 이미지: 가상의 할 일 앱 “오늘 한 걸음”을 다섯 방향으로 각각 생성한 이미지 시안. 2번에 선택 표시가 있음.
- 구현 이미지: 선택한 2번 방향으로 만든 앱의 실제 브라우저 캡처. 390×844 프레임이며 실제 휴대폰 사진은 아님.
