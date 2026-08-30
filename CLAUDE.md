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

- 작업 브랜치는 **세션마다 다르게 지정된다.** 그 세션의 작업 지시에 적힌 이름을 쓸 것 (문서에 남은 옛 이름을 그대로 쓰지 말 것)
- 이전 PR이 머지된 상태이므로 **매번 `origin/main`에서 브랜치를 새로 시작**할 것
  ```bash
  git fetch origin main && git checkout -B <이번 세션 브랜치> origin/main
  ```
- 수정 → 커밋 → 푸시 → PR 생성 → **머지까지** 한 번에 끝낸다 (사용자가 매번 "머지해줘"라고 말하지 않아도 되게)

## 관련 저장소 — 둘의 역할이 다름

| 저장소 | 담는 것 | 언제 고치나 |
|---|---|---|
| `goldlucky7/Happy` (여기) | **스킬 문서만.** `travel-stampbook`(만드는 법) · `stampbook-skill-sync`(동기화) · `template-state.md`(기록) | 제주 사이트에 새 기능이 생겨서 "만드는 법"에 규칙을 추가해야 할 때 |
| `goldlucky7/jeju` | **웹사이트 본체.** `index.html` · `updates.json` · `lib/`(탑승권 인식기) · `tools/`(인식 검증 도구) · `CLAUDE.md`(인수인계) | 장소를 추가·수정하거나 사이트 기능을 고칠 때 |

- 배포 주소: https://goldlucky7.github.io/jeju/ (main에 푸시하면 1~2분 뒤 자동 반영)
- **제주에는 스킬 파일이 없다.** "스킬 업데이트"는 항상 Happy 쪽만 고치는 일이다
- 제주 저장소도 이제 Claude가 직접 푸시할 수 있다 (Claude GitHub 앱에 연결됨).
  403이 나면 https://github.com/apps/claude/installations/select_target 에서 jeju 체크 확인
- 새 지역판(부산 등)도 `goldlucky7/jeju` 안에 `busan.html` 형태로 함께 올린다
- **제주 쪽 작업을 이어받을 때는 `goldlucky7/jeju`의 `CLAUDE.md`를 먼저 볼 것.**
  지금 상태·남은 일·이미 밟은 함정·확인 방법이 정리돼 있다.
  저장소를 붙이면(`add_repo` → clone → `register_repo_root`) 자동으로 읽힌다
