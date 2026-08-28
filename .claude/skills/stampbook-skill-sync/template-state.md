# 제주 템플릿 마지막 동기화 기록

이 파일은 `travel-stampbook` 스킬 문서가 **어느 시점의 템플릿까지 반영했는지** 기록한 것이다.
새로 동기화할 때 이 값들과 비교하면 무엇이 새로 생겼는지 바로 알 수 있다.

## 마지막 확인

| 항목 | 값 |
|---|---|
| 확인 날짜 | 2026-08-28 |
| 파일 | `https://raw.githubusercontent.com/goldlucky7/jeju/main/index.html` |
| 크기 | 273,424 bytes |
| 지문 (sha256 앞 16자) | `7b479cf9d24bfa76` |
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
| **합계** | **237** |

## 반영 완료된 기능

- 초성 검색창, 세부 카테고리 칩 14개(카테고리+맛집종류+키워드 3중 판정)
- 📍 지역별로 보기 (권역 10개 + 카드 권역 배지)
- 📍 내 주변 15km 이내 보기 (거리순 상위 30곳, 🧭 거리 배지)
- 🧭 활동 강도 그룹핑 (실내 → 시원한 야외 → 차로 → 야외 → 걷기 → 등산)
- ⭐ 꼭 가볼 곳 탭 (필터 자동 해제 + "왜 꼭 가야 하냐면" 이유)
- 카테고리별 우선 추천·티어 그룹 (맛집/소품샵/술집/호텔) + 호텔 성급
- 🅿️ 주차 정보 배지·팁·주차장 지도 링크
- 📋 주소 복사 · 📷 대표 사진 보기 · 📞 전화 걸기
- 🤖 용어 사전 (점선 밑줄 자동 + 텍스트 선택 후 AI에게 묻기)
- 🆕 요즘 뜨는 곳 (updates.json 피드, 개별/전부 담기)
- 지금 필터 바 (활성 필터 태그·곳수·전체 해제)
- 도장 찍은 곳은 목록에서 숨기고 [갔다온 곳] 탭에 모음

## 코드 구조 목록 (이 시점 기준)

여기 **없는 이름이 새로 나타나면 그게 새 기능**이다.

```
BARTIER BAR_T CAT CATS CAT_EMOJI CHIPS CHO_LIST COUPLE_KEY EFF EFFORT EFF_OF
EFF_ORDER FT FTYPE GLOSSARY GLO_KEYS GLO_RE HOTELTIER HOTEL_T KEY LL MUST
MUSTBAR MUSTEAT MUSTHOTEL MUSTSHOP NEAR_LIMIT_KM NM PHOTO PK PKMAP PKT PK_OF
PK_ORDER PLACES READ_URL SHOPTIER SHOP_T STARS TEL TIERMAP UPD_SEEN_KEY UPD_URL
VJ WRITE_URL ZONES ZONE_KW ZONE_OF activeEff activeZone addCustomPlace
addEffGroups addFoodGroups addGrid addSubHead addTierGroups allPlaces autoSync
barNear byEff byPk chipMatch chipsEl clearNearby copyAddr currentFilter
customPlaces customToCard deleteCustomPlace distKm drawUpd drawUpdFail effGrid
effOf escHtml fetchRemote fmtDist ftOf gloDef gloInput gloModal gloSug gloWord
glossify hasPlace hoursModal list lsGet lsSet makeCard markUpdBtn matchesEff
matchesSearch mergeCustom modal nearbyBtn nearbyOn normalize onSelEnd online
openGlo openUpd passes pkOf placeText pushRemote render renderEffMenu
renderFilterBar renderHoursTable renderZoneMenu saveLocal scrollToList
searchClear searchInput searchQ selBtn setAiLinks setTab showGlo syncChips toCho
toggleBarNear toggleVisit updBtn updFeed updModal updSeen updateProgress
updateSyncLabel updateVisitedTab visibleCount visited zoneGrid zoneOf
```
