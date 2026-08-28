# 제주 템플릿 마지막 동기화 기록

이 파일은 `travel-stampbook` 스킬 문서가 **어느 시점의 템플릿까지 반영했는지** 기록한 것이다.
새로 동기화할 때 이 값들과 비교하면 무엇이 새로 생겼는지 바로 알 수 있다.

## 마지막 확인

| 항목 | 값 |
|---|---|
| 확인 날짜 | 2026-08-28 |
| 파일 | `https://raw.githubusercontent.com/goldlucky7/jeju/main/index.html` |
| 크기 | 343839 bytes |
| 지문 (sha256 앞 16자) | `71338131fd878902` |
| 사이드카 파일 | `updates.json` (요즘 뜨는 곳 피드) |

## 장소 수

| 카테고리 | 곳수 |
|---|---|
| spot (관광지) | 99 |
| food (맛집) | 55 |
| cafe (카페) | 41 |
| shop (소품샵) | 12 |
| bar (술집·안주) | 15 |
| hotel (호텔) | 15 |
| spa (마사지) | 26 |
| cheap (가성비 카페) | 24 |
| **합계** | **287** |

⚠️ 템플릿 헤더 표기는 `263 PLACES`로 실제(287)와 어긋나 있음. 새 지역판을 만들 땐 실제 개수로 넣을 것.

## 반영 완료된 기능

- 초성 검색창, 세부 카테고리 칩 14개(카테고리+맛집종류+키워드 3중 판정)
- 📍 지역별로 보기 (권역 10개 + 카드 권역 배지)
- 📍 내 주변 15km 이내 보기 (거리순 상위 30곳, 🧭 거리 배지)
- 🧭 활동 강도 그룹핑 (실내 → 시원한 야외 → 차로 → 야외 → 걷기 → 등산)
- ⭐ 꼭 가볼 곳 탭 (필터 자동 해제 + "왜 꼭 가야 하냐면" 이유)
- 카테고리별 우선 추천·티어 그룹 (맛집/소품샵/술집/호텔/마사지) + 호텔 성급
- 💸 가성비 카페 탭 (바다·경치 / 이동 중 / 시내·시장 3그룹)
- ⭐ 내 일정 탭 (가보고 싶어요 담기, 방문 예정 날짜, 지역별·날짜별 전환)
- 🎟 롯데렌터카 제주 웰컴 쿠폰팩 제휴처 39곳 (카드 배지·할인율 직접 메모·전체 모달)
- 🅿️ 주차 정보 배지·팁·주차장 지도 링크
- 📋 주소 복사 · 📷 대표 사진 보기 · 📞 전화 걸기
- 🤖 용어 사전 (점선 밑줄 자동 + 텍스트 선택 후 AI에게 묻기)
- 🆕 요즘 뜨는 곳 (updates.json 피드, 개별/전부 담기)
- 지금 필터 바 (활성 필터 태그·곳수·전체 해제)
- 도장 찍은 곳은 목록에서 숨기고 [갔다온 곳] 탭에 모음
- 저장 구조 `{v:도장, c:추가장소, w:가보고 싶은 곳+날짜, r:할인율 메모}`

## 코드 구조 목록 (이 시점 기준)

여기 **없는 이름이 새로 나타나면 그게 새 기능**이다.

```
BARTIER BAR_T CAT CATS CAT_EMOJI CHEAPG CHEAP_GROUPS CHIPS CHO_LIST COUPLE_KEY
DOW EFF EFFORT EFF_OF EFF_ORDER FT FTYPE GLOSSARY GLO_KEYS GLO_RE HOTELTIER
HOTEL_T KEY LL LOTTE LOTTE_ALL LOTTE_IDS LOTTE_URL MUST MUSTBAR MUSTEAT
MUSTHOTEL MUSTSHOP MUSTSPA NEAR_LIMIT_KM NM PHOTO PK PKMAP PKT PK_OF PK_ORDER
PLACES READ_URL SHOPTIER SHOP_T SPATIER SPA_T STARS TEL TIERMAP UPD_SEEN_KEY
UPD_URL VJ WRITE_URL ZONES ZONE_KW ZONE_OF activeEff activeZone addCheapGroups
addCustomPlace addEffGroups addFoodGroups addGrid addSubHead addTierGroups
allPlaces autoSync barNear byEff byPk chipMatch chipsEl clearNearby copyAddr
currentFilter customPlaces customToCard daysAway deleteCustomPlace distKm
drawLotte drawUpd drawUpdFail effGrid effOf escHtml fetchRemote fmtDay fmtDist
ftOf gloDef gloInput gloModal gloSug gloWord glossify hasPlace hoursModal
isWished list lotteModal lsGet lsSet makeCard markUpdBtn matchesEff
matchesSearch mergeCustom modal nearbyBtn nearbyOn normalize onSelEnd online
openGlo openUpd passes pkOf placeText planGroup pushRemote rateOf rateSrc
rates render renderEffMenu renderFilterBar renderHoursTable renderPlan
renderPlanByDate renderPlanByZone renderZoneMenu saveLocal saveRate saveWish
scrollToList searchClear searchInput searchQ selBtn setAiLinks setTab
setWishDate showGlo syncChips toCho toggleBarNear toggleVisit toggleWish
updBtn updFeed updModal updSeen updateProgress updateSyncLabel
updateVisitedTab visibleCount visited wish zoneGrid zoneOf
```
