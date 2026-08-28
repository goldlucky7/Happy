---
name: stampbook-skill-sync
description: 제주 스탬프북 템플릿(goldlucky7/jeju)이 바뀌었을 때, 바뀐 내용을 찾아내 travel-stampbook 스킬 문서에 반영하고 커밋·PR·머지까지 끝내는 스킬. 사용자가 "스킬 업데이트했어", "스킬 바꿨어", "스킬 업뎃했어", "템플릿 바꿨어", "제주 스탬프북 바꿨어", "새 기능 넣었어 스킬에 반영해줘", "찾아서 업데이트해줘" 등으로 말하면 반드시 이 스킬을 사용할 것. 사용자는 스탬프북 웹사이트에 직접 기능을 추가한 뒤 이 말을 하므로, 무엇이 바뀌었는지 되묻지 말고 스스로 찾아낼 것.
---

# 스탬프북 스킬 동기화

사용자가 제주 스탬프북 사이트에 새 기능을 추가한 뒤 "스킬 업데이트했어"라고 하면, **무엇이 바뀌었는지 직접 찾아내서** `travel-stampbook` 스킬 문서에 반영한다.

## 핵심 원칙

- **되묻지 말 것.** "어떤 기능을 추가하셨나요?"라고 묻지 말고 코드를 직접 비교해서 알아낼 것
- **끝까지 갈 것.** 파일 수정 → 커밋 → 푸시 → PR 생성 → **머지까지** 한 번에 끝낸다 (사용자는 매번 "머지해줘"라고 말하는 걸 번거로워함)
- **비개발자 말투로 보고.** 함수명·변수명 대신 "화면에서 뭐가 달라지는지"로 설명

## 위치 정보

| 대상 | 위치 |
|---|---|
| 제주 템플릿 (원본 코드) | `https://raw.githubusercontent.com/goldlucky7/jeju/main/index.html` |
| 요즘 뜨는 곳 피드 | `https://raw.githubusercontent.com/goldlucky7/jeju/main/updates.json` |
| 수정할 스킬 문서 | 이 저장소(goldlucky7/Happy)의 `.claude/skills/travel-stampbook/SKILL.md` |
| 마지막 동기화 기록 | 이 폴더의 `template-state.md` |
| 작업 브랜치 | `claude/skill-search-feature-sd6plu` |

## 작업 순서

### 1. 템플릿 받아서 비교
```bash
cd <스크래치패드>
curl -sS -o jeju_now.html https://raw.githubusercontent.com/goldlucky7/jeju/main/index.html
wc -c jeju_now.html          # template-state.md의 크기와 비교
sha256sum jeju_now.html | cut -c1-16   # 지문이 같으면 변경 없음
```
- `template-state.md`에 적힌 **크기·지문**과 같으면 → 변경 없음. 사용자에게 "아직 반영할 새 기능이 없어요"라고 알리고 종료
- 다르면 계속 진행

### 2. 뭐가 새로 생겼는지 찾기
`template-state.md`의 **구조 목록(identifiers)** 과 현재 코드를 비교하는 게 가장 빠르다:
```bash
node -e '
const s=require("fs").readFileSync("jeju_now.html","utf8");
const ids=[...s.matchAll(/^(?:const|let|function|async function)\s+([A-Za-z_][A-Za-z0-9_]*)/gm)].map(m=>m[1]);
console.log([...new Set(ids)].sort().join(" "));
'
```
- 목록에 **없던 이름**이 새 기능이다. 그 이름으로 코드를 찾아 무슨 일을 하는지 읽는다
- 화면 변화도 같이 확인: `<body>`~`<script>` 사이 마크업에서 새 버튼·모달·영역을 찾는다
- 카테고리·장소 수가 바뀌었으면 실제로 세어본다:
```bash
node -e '
const s=require("fs").readFileSync("jeju_now.html","utf8");
const c={}; for(const m of s.matchAll(/cat:"(\w+)"/g)) c[m[1]]=(c[m[1]]||0)+1;
console.log(c, "total:", Object.values(c).reduce((a,b)=>a+b,0));
'
```
- 새 사이드카 파일(예: `updates.json`)이 생겼는지도 확인

### 3. 스킬 문서에 반영
`.claude/skills/travel-stampbook/SKILL.md`를 고친다. 새 기능마다 **아래 4곳을 빠짐없이** 손볼 것:

1. **description(맨 위)** — 기능 이름을 한 단어로 끼워넣기
2. **완성품 스펙** — 사용자 눈에 보이는 동작으로 한 줄 추가
3. **제작 순서 3~4단계** — 새 지역을 만들 때 **교체해야 할 데이터**와 **빠뜨리면 생기는 증상**을 표에 추가. 조사 단계에서 새로 수집해야 할 정보가 있으면 3단계에도 추가
4. **기존 스탬프북 수정 요청일 때** — 장소를 새로 추가할 때 같이 채워야 할 데이터에 추가

⚠️ **로직 함수는 "변경 금지" 목록에 이름을 추가**할 것. 새 지역판을 만들 때 실수로 고치면 기능이 죽는다.

### 4. template-state.md 갱신
이번에 확인한 크기·지문·구조 목록·장소 수로 `template-state.md`를 덮어쓴다. 다음 동기화가 쉬워진다.

### 5. 커밋 → PR → 머지 (한 번에)
```bash
git fetch origin main
git checkout -B claude/skill-search-feature-sd6plu origin/main   # 이전 PR이 머지됐으므로 항상 main에서 새로 시작
git add -A && git commit -m "..."
git push -u --force-with-lease origin claude/skill-search-feature-sd6plu
```
그다음 GitHub 도구로 `goldlucky7/Happy`에 PR을 만들고 **바로 머지**한다 (base: `main`).
- PR 본문 끝에는 Claude Code 출처 표기를 넣을 것

### 6. 사용자에게 보고
- 이번에 **뭐가 새로 생겼는지** 화면 기준으로 설명 (예: "버튼 누르면 위치를 물어보고 가까운 순으로 보여줘요")
- 스킬에 **어떤 규칙을 넣었는지** 짧게
- "머지까지 완료했다"고 명확히 마무리 (사용자가 "완료된 거니?"라고 되묻지 않게)

## 자주 하는 실수

- ❌ 사용자에게 뭐가 바뀌었는지 묻기 → 직접 찾을 것
- ❌ PR만 만들고 멈추기 → 머지까지 할 것
- ❌ 이미 머지된 브랜치 위에 계속 쌓기 → 매번 `origin/main`에서 새로 시작
- ❌ 기능만 적고 "새 지역 만들 때 뭘 교체해야 하는지" 안 적기 → 표에 반드시 추가
- ❌ 함수명·변수명으로 사용자에게 설명하기 → 화면 동작으로 설명
