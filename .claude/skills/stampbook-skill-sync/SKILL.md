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
| 작업 브랜치 | **세션마다 지정된 브랜치를 쓸 것** (작업 지시에 적힌 이름. 예전 값 `claude/skill-search-feature-sd6plu`를 그대로 쓰지 말 것) |
| 제주 저장소 쓰기 | 가능 (Claude GitHub 앱에 jeju 연결됨) |

## 작업 순서

### 1. 제주 저장소를 붙여서 커밋 로그로 확인 (가장 빠르고 정확)

추측하지 말고 **커밋 메시지와 diff를 직접 볼 것.** 사용자가 뭘 바꿨는지 한 줄로 나온다.

```bash
# add_repo(owner=goldlucky7, repo=jeju, access=push) 로 붙인 뒤
git clone --depth 30 https://github.com/goldlucky7/jeju /home/user/jeju
git -C /home/user/jeju log --oneline -10
```
`template-state.md`의 **마지막 반영 커밋** 이후에 찍힌 커밋들이 이번에 반영할 것이다.

```bash
git -C /home/user/jeju diff <마지막반영커밋> origin/main -- index.html
```
- 마지막 반영 커밋이 곧 `origin/main`이면 → 변경 없음. "아직 반영할 새 기능이 없어요"라고 알리고 종료
- 기록에 커밋이 안 적혀 있는 옛 형식이면 아래로 지문을 맞춰 그 커밋을 찾는다:
```bash
for c in $(git -C /home/user/jeju log --format=%h -10); do
  echo "$c $(git -C /home/user/jeju show $c:index.html | sha256sum | cut -c1-16)"
done
```

> 저장소를 못 붙이는 상황이면 raw 파일을 받아 크기·지문만 비교해도 된다:
> `curl -sS -o jeju_now.html .../index.html && wc -c jeju_now.html && sha256sum jeju_now.html | cut -c1-16`

### 2. 바뀐 게 기능인지 데이터인지 가리기
diff를 읽으면 대개 바로 보인다. 애매하면 `template-state.md`의 **구조 목록(identifiers)** 과 비교한다:
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

⚠️ **구조 목록만 믿지 말 것.** 위 비교는 줄 맨 앞(들여쓰기 없는) 선언만 잡는다.
**"새 이름 없음"인데 파일 크기가 늘었다면 기능이 아니라 데이터·링크가 바뀐 것**이므로
반드시 실제 diff를 볼 것:
```bash
diff jeju_prev.html jeju_now.html > d.txt
grep -c '^>' d.txt          # 추가된 줄 수
grep '^[<>]' d.txt | cut -c1-140 | head -40
```
장소 이름·주소·링크가 대량으로 바뀌는 **데이터 품질 개선**도 스킬에 반영할 내용이다
(무엇을 어떻게 고쳤는지를 새 지역 제작 규칙으로 옮겨 적을 것).

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
BR=<이번 세션에 지정된 브랜치>          # 하드코딩 금지, 매번 작업 지시에서 확인
git fetch origin main
git checkout -B "$BR" origin/main       # 이전 PR이 머지됐으므로 항상 main에서 새로 시작
git add -A && git commit -m "..."
git push -u --force-with-lease origin "$BR"
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
