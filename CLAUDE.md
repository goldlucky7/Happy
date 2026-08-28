# Happy — 개인 스킬 저장소

사용자(비개발자)가 쓰는 Claude Code 스킬들을 모아둔 저장소입니다.

## 사용자에 대해

- **비개발자, 주로 안드로이드 폰으로 작업.** 함수명·변수명 대신 "화면에서 뭐가 달라지는지"로 설명할 것
- **번거로운 걸 싫어함.** 되묻지 말고 알아서 진행하고, 시작한 일은 끝(머지)까지 마칠 것
- 한국어로 소통

## 스킬 목록

| 스킬 | 언제 쓰나 |
|---|---|
| `travel-stampbook` | "부산 스탬프북 만들자" 등 여행 스탬프북 웹사이트 제작·수정 |
| `stampbook-skill-sync` | "스킬 업데이트했어" — 제주 템플릿이 바뀌어서 위 스킬 문서에 반영해야 할 때 |

## 작업 규칙

- 작업 브랜치: `claude/skill-search-feature-sd6plu`
- 이전 PR이 머지된 상태이므로 **매번 `origin/main`에서 브랜치를 새로 시작**할 것
  ```bash
  git fetch origin main && git checkout -B claude/skill-search-feature-sd6plu origin/main
  ```
- 수정 → 커밋 → 푸시 → PR 생성 → **머지까지** 한 번에 끝낸다 (사용자가 매번 "머지해줘"라고 말하지 않아도 되게)

## 관련 저장소

스탬프북 웹사이트 본체는 별도 저장소에 있습니다: `goldlucky7/jeju`
(배포 주소: https://goldlucky7.github.io/jeju/)
