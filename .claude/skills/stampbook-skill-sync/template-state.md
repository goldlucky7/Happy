# 제주 템플릿 마지막 동기화 기록

이 파일은 `travel-stampbook` 스킬 문서가 **어느 시점의 템플릿까지 반영했는지** 기록한 것이다.
새로 동기화할 때 이 값들과 비교하면 무엇이 새로 생겼는지 바로 알 수 있다.

## 마지막 확인

| 항목 | 값 |
|---|---|
| 확인 날짜 | 2026-08-29 |
| 파일 | `https://raw.githubusercontent.com/goldlucky7/jeju/main/index.html` |
| 크기 | 398765 bytes |
| 지문 (sha256 앞 16자) | `0a3aa42cf9e8916e` |
| 마지막 반영 커밋 | `5929a24` 🎢 탈것·놀이기구 카테고리 신설 (23곳) |
| 사이드카 파일 | `updates.json` (요즘 뜨는 곳 피드) |

## ⚠️ main에 아직 안 올라간 상태

`5929a24`는 **브랜치 `claude/jeju-template-category-63n8j5`에만 있고 `origin/main`에는 없다.**
즉 배포 사이트(https://goldlucky7.github.io/jeju/)에는 탈것 탭이 아직 안 보인다.

- 다음 동기화 때 `origin/main`과 비교하면 **크기 372118 / 지문 `fea256ff282ed750`(= 이전 커밋 `10ab2a8`)** 로 나올 수 있다. 그건 새 변경이 사라진 게 아니라 **아직 머지가 안 된 것**이다
- 브랜치가 머지되면 main이 위 표의 크기·지문과 같아진다
- 확인: `git -C /home/user/jeju log --oneline origin/main -1` 에 `5929a24`가 보이는지

## 장소 수

| 카테고리 | 곳수 |
|---|---|
| spot (관광지) | 99 |
| food (맛집) | 55 |
| cafe (카페) | 49 |
| shop (소품샵) | 12 |
| bar (술집·안주) | 15 |
| hotel (호텔) | 15 |
| spa (마사지) | 26 |
| cheap (가성비 카페) | 24 |
| **ride (탈것·놀이기구)** | **23** |
| **합계** | **318** |

세부 카테고리 칩: **19개** (🚢 배·잠수함·요트 / 🎢 탈것·놀이기구 2개 추가)

헤더 표기(`318 PLACES`)와 실제 PLACES 개수가 일치함. `<title>`·`.h-eyebrow`·`.h-sub` 세 곳 모두 318로 맞춰져 있다.

## 반영 완료된 기능

- 초성 검색창, 세부 카테고리 칩 19개(카테고리+맛집종류+키워드 3중 판정)
  - 그중 `🍧 빙수·팥빙수`(`cats:["cafe","food"]`)와 `🚢 배·잠수함·요트`(`cats:["ride","spot"]`)는 **탭을 가로지르는 테마 칩**
- 📍 지역별로 보기 (권역 10개 + 카드 권역 배지)
- 📍 내 주변 15km 이내 보기 (거리순 상위 30곳, 🧭 거리 배지)
- 🧭 활동 강도 그룹핑 (실내 → 시원한 야외 → 차로 → 야외 → 걷기 → 등산)
- ⭐ 꼭 가볼 곳 탭 (필터 자동 해제 + "왜 꼭 가야 하냐면" 이유)
- 카테고리별 우선 추천·티어 그룹 (맛집/소품샵/술집/호텔/마사지) + 호텔 성급
- 💸 가성비 카페 탭 (바다·경치 / 이동 중 / 시내·시장 3그룹)
- 🎢 **탈것·놀이기구 탭 23곳** (배 9 / 직접 몰기 7 / 하늘 2 / 놀이기구 3 / 말 2 — RIDEG·RIDE_GROUPS 5그룹)
  - 탭 머리글에 예약·결항 주의 + "이미 관광지 탭에 있는 탈것" 안내
  - 좌표는 확인된 8곳만 `LL`에 들어감 (나머지 15곳은 [내 주변]에서 빠짐 — 의도된 상태)
  - 전화번호는 확인된 17곳만 `TEL`에 들어감
- 🍧 팥빙수·빙수 카페 8곳 (카페 카테고리 안, 장소마다 다른 이모지)
- ⭐ 내 일정 탭 (가보고 싶어요 담기, 방문 예정 날짜, 지역별·날짜별 전환)
- 🚗 동선 순서 (묶음 안 최적 경로 정렬, 카드 순번·구간 거리, 총 거리 요약)
- 🎟 롯데렌터카 제주 웰컴 쿠폰팩 제휴처 39곳 (카드 배지·할인율 직접 메모·전체 모달)
- 🅿️ 주차 정보 배지·팁·주차장 지도 링크
- 📋 주소 복사 · 📷 대표 사진 보기 · 📞 전화 걸기
- 🤖 용어 사전 (점선 밑줄 자동 + 텍스트 선택 후 AI에게 묻기) — 탈것 용어 11개 추가(짚라인·패러글라이딩·활공장·ATV·버기카·레일바이크·도항선·외승·갑마장·세일링)
- 🆕 요즘 뜨는 곳 (updates.json 피드, 개별/전부 담기)
- 지금 필터 바 (활성 필터 태그·곳수·전체 해제)
- 도장 찍은 곳은 목록에서 숨기고 [갔다온 곳] 탭에 모음
- 저장 구조 `{v:도장, c:추가장소, w:가보고 싶은 곳+날짜, r:할인율 메모}`
- 🔗 카드 바깥 링크 3종 (네이버지도 / 관광포털 검색 / 후기·정보 검색) — 전부 장소 이름 기반 검색 링크
- 📝 데이터 품질: 지도에서 검색되는 이름 표기, 시장 안 가게는 지번+시장 내 주소

## 장소 하나를 추가할 때 같이 채워지는 표

`PLACES` · `TEL` · `PK` · `EFFORT` · `ZONE_OF` · `LL` — 6곳.
테마가 새로 생기면 `CHIPS` 한 줄이 더 붙는다.

**카테고리를 통째로 새로 만들면 10곳**으로 늘어난다 (CSS 2 + 탭 버튼 + `CAT`/`CATS`/`CAT_EMOJI` +
그룹 정의·출력 함수 + `render()` 분기 + 칩 + 곳수 3곳). 자세한 표는 `travel-stampbook/SKILL.md`의
"카테고리를 통째로 새로 만들 때" 절 참고. `ride` 추가가 그 절차 그대로였다.

## 코드 구조 목록 (이 시점 기준)

여기 **없는 이름이 새로 나타나면 그게 새 기능**이다. 총 173개.
(`5929a24`에서 `RIDEG` `RIDE_GROUPS` `addRideGroups` 3개가 늘었다)

⚠️ 이 목록은 줄 맨 앞(들여쓰기 없는) 선언만 잡는다. **"새 이름 없음"인데 파일 크기가 늘었다면
기능이 아니라 데이터가 바뀐 것**이므로 반드시 실제 diff를 볼 것.

```
BARTIER BAR_T CAT CATS CAT_EMOJI CHEAPG CHEAP_GROUPS CHIPS CHO_LIST COUPLE_KEY
DOW EFF EFFORT EFF_OF EFF_ORDER FT FTYPE GLOSSARY GLO_KEYS GLO_RE HOTELTIER
HOTEL_T JEJU_AIRPORT KEY LL LOTTE LOTTE_ALL LOTTE_IDS LOTTE_URL MUST MUSTBAR
MUSTEAT MUSTHOTEL MUSTSHOP MUSTSPA NEAR_LIMIT_KM NM PHOTO PK PKMAP PKT PK_OF
PK_ORDER PLACES READ_URL RIDEG RIDE_GROUPS SHOPTIER SHOP_T SPATIER SPA_T STARS
TEL TIERMAP UPD_SEEN_KEY UPD_URL VJ WRITE_URL ZONES ZONE_KW ZONE_OF activeEff
activeZone addCheapGroups addCustomPlace addEffGroups addFoodGroups addGrid
addRideGroups addRouteGrid addSubHead addTierGroups allPlaces autoSync barNear
byEff byPk chipMatch chipsEl clearNearby copyAddr currentFilter customPlaces
customToCard daysAway deleteCustomPlace distKm drawLotte drawUpd drawUpdFail
effGrid effOf escHtml fetchRemote fmtDay fmtDist ftOf gloDef gloInput gloModal
gloSug gloWord glossify hasPlace hopKm hoursModal isWished list llOf lotteModal
lsGet lsSet makeCard markUpdBtn matchesEff matchesSearch mergeCustom modal
nearbyBtn nearbyOn normalize onSelEnd online openGlo openUpd passes pathLen
pkOf placeText planGroup pushRemote rateOf rateSrc rates render renderEffMenu
renderFilterBar renderHoursTable renderPlan renderPlanByDate renderPlanByZone
renderZoneMenu routeNote routeOrder saveLocal saveRate saveWish scrollToList
searchClear searchInput searchQ selBtn setAiLinks setTab setWishDate showGlo
syncChips toCho toggleBarNear toggleVisit toggleWish updBtn updFeed updModal
updSeen updateProgress updateSyncLabel updateVisitedTab visibleCount visited
wish zoneGrid zoneOf
```

> 참고: 예전에 `goldlucky7/jeju` 푸시가 403으로 막혔던 것은 Claude GitHub 앱에
> 이 저장소가 연결돼 있지 않아서였다. 사용자가 앱에 jeju를 추가해 해결됐고,
> 이제 `add_repo`(access: push) → `git push origin HEAD:main`으로 바로 올라간다.
> 다시 403이 나면 https://github.com/apps/claude/installations/select_target 에서
> jeju가 아직 체크돼 있는지 확인할 것.
