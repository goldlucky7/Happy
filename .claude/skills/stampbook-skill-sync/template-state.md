# 제주 템플릿 마지막 동기화 기록

이 파일은 `travel-stampbook` 스킬 문서가 **어느 시점의 템플릿까지 반영했는지** 기록한 것이다.
새로 동기화할 때 이 값들과 비교하면 무엇이 새로 생겼는지 바로 알 수 있다.

## 마지막 확인

| 항목 | 값 |
|---|---|
| 확인 날짜 | 2026-08-30 |
| 파일 | `https://raw.githubusercontent.com/goldlucky7/jeju/main/index.html` |
| 크기 | 431985 bytes |
| 지문 (sha256 앞 16자) | (아래 커밋 기준) |
| 마지막 반영 커밋 | `2ca1bb1` 안드로이드 내장 인식기가 "답을 안 줄 때" 스캔이 멎던 문제 수정 |
| 사이드카 파일 | `updates.json` (요즘 뜨는 곳 피드) · `lib/zxing.min.js` · `lib/jsQR.js` (탑승권 인식기) · `CLAUDE.md` (인수인계 문서) · `tools/` (탑승권 인식 검증 도구, 사이트에서는 쓰지 않음) |

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
| **합계** | **295** |

세부 카테고리 칩: **17개**

헤더 표기(`295 PLACES`)와 실제 PLACES 개수가 일치함. 이번 변경은 **기능만 추가**됐고 장소 수·칩 수는 그대로다.

## ✅ 밀린 작업 없음

2026-08-30 기준 제주 사이트와 스킬 문서가 모두 최신이다.

이번에 반영한 것: 커밋 `b64a0a1`(인수인계 문서 + 검증 도구) → `6e04d42`(안드로이드 인식 실패 수정 +
종이 탑승권 인식률 개선). 장소 데이터·칩은 그대로고 **탑승권 인식 쪽만** 손봤다.

> 사용자의 실제 t'way 종이 탑승권 사진으로 확인해 고친 건이다. 사진은 예약번호가 들어 있어
> 저장소에 넣지 않았다. 다시 검증할 일이 생기면 사용자에게 사진을 다시 받아 `/tmp`에서만 쓸 것.
>
> 사용자 기기는 **갤럭시 노트20(안드로이드)** — 기기 내장 인식기를 쓰는 갈래라
> 그 갈래가 조용히 죽었을 때가 문제였다. 아이폰이 아니라는 점을 기억할 것.

> 참고: `188adc2`는 처음에 기능 브랜치에만 올라가 있어서 사이트에 반영되지 않았다.
> 스탬프북 페이지는 **`main`을 본다**. 앞으로도 작업이 끝나면 반드시 main 까지 올릴 것.

> 참고: `goldlucky7/jeju` 푸시는 `add_repo`(access: push) → `git push origin main` 으로 바로 된다.
> 403이 나면 https://github.com/apps/claude/installations/select_target 에서 jeju 체크 확인.

## 반영 완료된 기능

- 초성 검색창, 세부 카테고리 칩 17개(카테고리+맛집종류+키워드 3중 판정)
  - 그중 `🍧 빙수·팥빙수`는 `cats:["cafe","food"]`로 **탭을 가로지르는 테마 칩**
- 📍 지역별로 보기 (권역 10개 + 카드 권역 배지)
- 📍 내 주변 15km 이내 보기 (거리순 상위 30곳, 🧭 거리 배지)
- 🧭 활동 강도 그룹핑 (실내 → 시원한 야외 → 차로 → 야외 → 걷기 → 등산)
- ⭐ 꼭 가볼 곳 탭 (필터 자동 해제 + "왜 꼭 가야 하냐면" 이유)
- 카테고리별 우선 추천·티어 그룹 (맛집/소품샵/술집/호텔/마사지) + 호텔 성급
- 💸 가성비 카페 탭 (바다·경치 / 이동 중 / 시내·시장 3그룹)
- 🍧 팥빙수·빙수 카페 8곳 (카페 카테고리 안, 장소마다 다른 이모지)
- ⭐ 내 일정 탭 (가보고 싶어요 담기, 방문 예정 날짜, 지역별·날짜별 전환)
- 🚗 동선 순서 (묶음 안 최적 경로 정렬, 카드 순번·구간 거리, 총 거리 요약)
- 🎟 롯데렌터카 제주 웰컴 쿠폰팩 제휴처 39곳 (카드 배지·할인율 직접 메모·전체 모달)
- 🅿️ 주차 정보 배지·팁·주차장 지도 링크
- 📋 주소 복사 · 📷 대표 사진 보기 · 📞 전화 걸기
- 🤖 용어 사전 (점선 밑줄 자동 + 텍스트 선택 후 AI에게 묻기)
- 🆕 요즘 뜨는 곳 (updates.json 피드, 개별/전부 담기)
- 지금 필터 바 (활성 필터 태그·곳수·전체 해제)
- 도장 찍은 곳은 목록에서 숨기고 [갔다온 곳] 탭에 모음
- 저장 구조 `{v:도장, c:추가장소, w:가보고 싶은 곳+날짜, r:할인율 메모}`
- 🔗 카드 바깥 링크 3종 (네이버지도 / 관광포털 검색 / 후기·정보 검색) — 전부 장소 이름 기반 검색 링크
- 📝 데이터 품질: 지도에서 검색되는 이름 표기, 시장 안 가게는 지번+시장 내 주소
- ✈️ **항공편 · 탑승권 QR 인식** (2026-08-30 추가) — 아래 상세

## ✈️ 항공편 기능 상세 (새 지역판을 만들 때 꼭 볼 것)

화면 세 개가 버튼 하나에 들어 있다: 🎫 탑승권 인식 / 🕐 항공사 운영시간 / 🧭 공항에서 어디로.

**지역마다 갈아끼워야 하는 데이터**

| 이름 | 내용 |
|---|---|
| `AIRLINES` | 그 지역 노선 항공사 10곳 + 고객센터 번호·상담시간·수속 마감(국내선 30분/국제선 60분) |
| `AIRPORTS` | 공항 코드→한글 이름. `kac`가 있으면 실시간 운항정보 링크가 자동으로 만들어짐 |
| `CJU_LIVE` | 그 지역 공항 실시간 출발·도착 페이지 주소 (변수명은 그대로 둬도 됨) |
| `AP_STEPS` | 공항 층별 구조 + 탑승까지 6단계 안내 |
| `CARRIER_ETC` | 외항사 코드→한글 이름 (표시용) |

**설계상 반드시 지킬 것**

- 탑승권 바코드(IATA BCBP)에는 **출발 시각과 탑승구가 들어 있지 않다.** 규격에 그 칸이 없다.
  시각은 사용자가 한 번 넣고, 탑승구는 실시간 조회 링크로 넘긴다. 이 전제를 바꾸려 하지 말 것
- 카운터·탑승구 번호는 **당일 배정**이라 코드에 적지 않는다. "전광판 확인"으로 안내
- 탑승객 이름·예약번호는 **공유 저장소에 올리지 않는다.** 각자 기기에만(`jeju_flights_v1`)
- 인식기는 3단계로 고른다: 기기 내장(BarcodeDetector) → ZXing(`lib/zxing.min.js`) → jsQR(`lib/jsQR.js`)

**과거에 실제로 겪은 함정 (다시 밟지 말 것)**

| 증상 | 원인 | 해결 |
|---|---|---|
| 카메라는 켜지는데 아무리 비춰도 반응 없음 | ZXing 자체 영상 기능이 `playing` 이벤트를 기다리는데 우리가 먼저 재생해 이벤트가 지나감 | ZXing 영상 기능을 쓰지 않고 프레임을 직접 떠서 넘김 (`pickEngine` 단일 루프) |
| 인식기가 프레임을 못 읽음 | ZXing의 `decode(video)`가 화면을 제대로 못 떠옴 | 캔버스로 떠서 `HTMLCanvasElementLuminanceSource`로 넘김 (`zxDecodeCanvas`) |
| 아이폰에서 카메라 권한이 조용히 거부됨 | 인식기 파일(수백 KB)을 먼저 받느라 버튼 누른 시점이 만료 | 카메라부터 열고 인식기를 나중에 고름 |
| 통신망·차단기 뒤에서 인식 불가 | 인식기를 외부 CDN에서 받아옴 | `lib/`에 넣어 저장소에서 먼저 읽음 |
| 사진에서 찾기가 QR만 겨우 읽음 | `flReader`를 카메라 켤 때만 만들어서 사진 경로에선 항상 null | `decodeImageFile`에서도 없으면 만들어 줌 |
| 인쇄된 탑승권이 안 읽힘 | 한 가지 방식으로만 봐서 놓침 | 프레임마다 여러 방식을 번갈아 시도 (`SCAN_PASSES`) |
| **안드로이드에서 아무리 비춰도 안 읽힘** | 기기 내장 인식기를 한 번 고르면 **갈아탈 방법이 없었다** | 인식기를 하나로 합쳐 **매 프레임 내장 → ZXing 을 다 돌린다** |
| **위를 고쳤는데도 여전히 안 읽힘** (같은 폰에서 두 번째) | 내장 인식기가 빈손을 주는 게 아니라 **아예 답을 안 준다.** `await det.detect(v)`가 안 끝나 루프가 첫 프레임에서 멎었다. `getSupportedFormats()`가 멎으면 스캔이 **시작조차 못 한다.** `try/catch`로는 못 잡는다 | 내장 인식기 호출을 전부 `withTimeout`으로 감쌌다. 두 번 넘기면 내장 인식기를 **아예 끈다** |
| 번들거리거나 굽은 종이 탑승권을 놓침 | 화면 **전체**의 밝기 차이만 벌려서(`boostContrast`) 한쪽만 밝은 사진을 못 잡음 | **자리마다 밝기를 따로 재서** 검정/흰색을 가른다 (`adaptiveBin` · 적분영상이라 창이 커도 픽셀당 한 번). 갈래마다 **줄이는 크기도 다르게** 한다 |

**인식 방식은 9가지를 번갈아 쓴다** (`SCAN_PASSES`). 실제 종이 탑승권으로 재보면
**촬영 거리마다 이기는 갈래가 매번 다르다.** 세 축을 섞는다:
- `adap` — 자리마다 밝기를 따로 재서 검정/흰색을 가른다 (번들거림·굽은 종이·그림자에 강하다)
- `max` — 줄이는 크기를 갈래마다 다르게 (같은 사진도 줄이는 크기에 따라 읽히고 안 읽힌다)
- `zoom` — 가운데만 확대 (코드가 멀리서 작게 잡힐 때)

ZXing 이 놓친 프레임은 같은 화면을 jsQR 로 한 번 더 본다. 사진은 멈춰 있으므로 줄인 화면·원본
화면 양쪽으로 전부 시도한다. 🔦 플래시 버튼이 있고(기기가 지원할 때만 표시),
카메라는 1920 해상도·연속 초점으로 연다.

**인식기 셋을 고르지 말고 다 돌린다.** 매 프레임 기기 내장(BarcodeDetector) → ZXing → jsQR
순으로 전부 시도한다. "하나를 고른다"는 구조가 안드로이드에서 두 번이나 사이트를 죽였다.
내장 인식기 호출은 **반드시 `withTimeout`으로 감쌀 것** — 답을 영영 안 주는 기기가 있고,
그냥 `await` 하면 스캔이 시작조차 못 한다. 두 번 넘기면 내장 인식기를 아예 끈다.

**안 읽힌다는 제보를 받으면 상태줄부터 받을 것.** 스캔 중 화면 아래에 이렇게 뜬다:
`🟢 인식기: 기기내장 + ZXing + QR전용 · 26회 · 1280×720 · 밝기 154`
확인 횟수가 안 늘면 루프가 멎은 것 · 밝기 0이면 카메라 그림이 캔버스로 안 넘어오는 것 ·
`기기내장(응답없음·끔)`이면 내장 인식기가 답을 안 준 것. 한 줄로 원인이 갈린다.

**검증 방법** (다시 손볼 일이 생기면 그대로 재현할 것): jeju 저장소의 `tools/` 를 쓴다.
```bash
pip install qrcode pillow pdf417gen
python3 tools/make-test-passes.py /tmp/passes   # 시험 이미지 20장 생성
node tools/verify-scan.mjs /tmp/passes          # 실제 스캔 경로로 확인
```
기준값 **16/20 인식 · 실시간 카메라 흐름 통과 · 내장 인식기 고장 흉내 4가지 통과**
(빈손 / 오류 / 답이 영영 없음 / 형식 조회부터 답이 없음).
남은 실패 4건은 심하게 흐린 종이 PDF417 — ZXing 의 한계이고 안드로이드 내장 인식기는 대부분 읽는다.
(카메라가 없는 컨테이너에서는 캔버스 `captureStream()` 으로 가짜 카메라를 만들어 물린다)

## 장소 하나를 추가할 때 같이 채워지는 표

`PLACES` · `TEL` · `PK` · `EFFORT` · `ZONE_OF` · `LL` — 6곳.
테마가 새로 생기면 여기에 `CHIPS` 한 줄이 더 붙는다.
(항공편 기능은 장소 데이터와 무관하므로 장소 추가 시 손댈 것 없음)

## 코드 구조 목록 (이 시점 기준)

여기 **없는 이름이 새로 나타나면 그게 새 기능**이다.
(데이터만 바뀌면 이름이 안 늘어도 파일 크기가 커진다 — 그럴 땐 반드시 실제 diff를 볼 것)

```
AIRLINES AIRLINE_OF AIRPORTS AP_STEPS BARTIER BAR_T CARRIER_ETC CAT CATS
CAT_EMOJI CHEAPG CHEAP_GROUPS CHIPS CHO_LIST CJU_LIVE COUPLE_KEY DOW
DOW_F EFF EFFORT EFF_OF EFF_ORDER FKEY FT FTYPE GLOSSARY GLO_KEYS GLO_RE
HOTELTIER HOTEL_T ICAO_IATA JEJU_AIRPORT KEY LL LOTTE LOTTE_ALL
LOTTE_IDS LOTTE_URL MUST MUSTBAR MUSTEAT MUSTHOTEL MUSTSHOP MUSTSPA
NEAR_LIMIT_KM NM PHOTO PK PKMAP PKT PK_OF PK_ORDER PLACES QR_LIBS
READ_URL SCAN_LIBS SCAN_MAX SCAN_MAX_FULL SCAN_PASSES SHOPTIER SHOP_T
SPATIER SPA_T STARS TEL TIERMAP TIMED_OUT UPD_SEEN_KEY UPD_URL VJ
WRITE_URL ZONES ZONE_KW ZONE_OF activeEff activeZone adaptiveBin
addCheapGroups addCustomPlace addEffGroups addFoodGroups addGrid
addRouteGrid addSubHead addTierGroups allPlaces apIsKR apLive apName
apOptions autoSync barNear bcbpShift boostContrast byEff byPk camError
carrierName cdText chipMatch chipsEl clearNearby closeFlight copyAddr
currentFilter customPlaces customToCard daysAway decodeImageFile
delFlight deleteCustomPlace distKm drawLotte drawUpd drawUpdFail effGrid
effOf ensureJsQR ensureZXing escHtml fetchRemote flCanvas flDraft flMsg
flPass flStream flTorchOn flightIntl flightModal flightSearch
flightTimes fmtDateF fmtDay fmtDist fmtHM frameBrightness ftOf
getNativeDetector gloDef gloInput gloModal gloSug gloWord glossify
grabCanvas grabPixels hasPlace hopKm hoursModal isWished isoDate
jsqrCanvas jsqrRead julianToISO list llOf loadFlights loadScript
lotteModal lsGet lsSet makeCard markUpdBtn matchesEff matchesSearch
mergeCustom modal myFlights nearbyBtn nearbyOn nextPass normalize
onDecoded onSelEnd online openFlight openGlo openUpd parseBCBP
parseLoose parsePass passes pathLen persistFlights pickEngine pkOf
placeText planGroup pushRemote rateOf rateSrc rates render
renderAirTable renderApSteps renderEffMenu renderFilterBar
renderFlightBar renderFlightForm renderFlightPreview renderHoursTable
renderPlan renderPlanByDate renderPlanByZone renderSavedFlights
renderZoneMenu routeNote routeOrder saveDraft saveLocal saveRate
saveWish scrollToList searchClear searchInput searchQ selBtn setAiLinks
setEngine setFlPane setTab setWishDate setupTorch showGlo sortFlights
startScan stopScan syncChips syncDraft ticketHtml toCho toggleBarNear
toggleTorch toggleVisit toggleWish torchTrack updBtn updFeed updModal
updSeen updateProgress updateSyncLabel updateVisitedTab visibleCount
visited wish withTimeout zoneGrid zoneOf zxDecodeCanvas zxHints
```
