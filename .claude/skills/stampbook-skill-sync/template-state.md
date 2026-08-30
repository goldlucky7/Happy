# 제주 템플릿 마지막 동기화 기록

이 파일은 `travel-stampbook` 스킬 문서가 **어느 시점의 템플릿까지 반영했는지** 기록한 것이다.
새로 동기화할 때 이 값들과 비교하면 무엇이 새로 생겼는지 바로 알 수 있다.

## 마지막 확인

| 항목 | 값 |
|---|---|
| 확인 날짜 | 2026-08-30 |
| 파일 | `https://raw.githubusercontent.com/goldlucky7/jeju/main/index.html` |
| 크기 | 445854 bytes |
| 지문 (sha256 앞 16자) | (아래 커밋 기준) |
| 마지막 반영 커밋 | `72b0c07` 제목 형광 주황 + 롯데렌터카 자리에 제주 공식 할인 제도 4가지 |
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

세부 카테고리 칩: **16개** (🎟 롯데렌터카 칩을 뺐다)

헤더 표기(`295 PLACES`)와 실제 PLACES 개수가 일치함. 이번 변경은 **기능만 추가**됐고 장소 수·칩 수는 그대로다.

## ✅ 밀린 작업 없음

2026-08-30 기준 제주 사이트와 스킬 문서가 모두 최신이다.

이번에 반영한 것 (`2ca1bb1` → `72b0c07`, 커밋 7개). 장소 데이터는 그대로고 **화면과 탑승권 쪽**이 크게 바뀌었다.

| 커밋 | 내용 |
|---|---|
| `eaf9a73` | 카메라 인식 2.4배 가속 (탑승권 3형식만) + 상태줄을 화면 위에 겹침 |
| `ac04ca1` | **진짜 원인은 초점이었다** — 선명화(`unsharp`)·고해상도 요청·눌러서 초점 |
| `7f29ecd` | **[📸 찍어서 읽기]** 신설 + 화면에 또렷함 점수·판정 표시 |
| `2f3fd45` | **카메라로 계속 비추는 스캔을 화면에서 뺐다** (그 폰에서 끝내 안 됨) |
| `1535426` | 「얼마나 움직여야」·「지역별로 보기」 접이식(`setupFold`) |
| `739a006` | **첫 화면 전면 정리** — 타일 격자 · 한 줄 탭 · 구역 제목 |
| `72b0c07` | 제목 형광 주황 + 롯데렌터카 → 제주 공식 할인 제도 4가지(`COUPONS`) |

> **탑승권 인식은 여섯 번 고쳐도 그 폰에서 끝내 안 됐다.** 마지막 원인은 미리보기 화면이
> 그냥 흐린 것(실측 또렷함 13.9 ≈ 2.7px 뭉개짐)이고, 이건 웹페이지가 어떻게 할 수 있는
> 영역이 아니다. 같은 폰으로 **찍은 사진은 잘 읽힌다.** 그래서 [📸 찍어서 읽기] 하나로 정리했다.
> 스캔 코드는 지우지 않고 남겨뒀다 — 다른 기기에서는 됐을 수도 있다.

## 반영 완료된 기능

- 초성 검색창, 세부 카테고리 칩 16개(카테고리+맛집종류+키워드 3중 판정)
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
- 🎟 그 지역 공식 할인 제도 안내(`COUPONS`) — 나우다·탐나는전·문화가 있는 날·무료 개방일
  (예전의 롯데렌터카 쿠폰팩은 뺐다. 데이터 `LOTTE_ALL`과 저장 칸 `r`은 병합 안전 때문에 코드에 남아 있다)
- 🅿️ 주차 정보 배지·팁·주차장 지도 링크
- 📋 주소 복사 · 📷 대표 사진 보기 · 📞 전화 걸기
- 🤖 용어 사전 (점선 밑줄 자동 + 텍스트 선택 후 AI에게 묻기)
- 🆕 요즘 뜨는 곳 (updates.json 피드, 개별/전부 담기)
- 지금 필터 바 (활성 필터 태그·곳수·전체 해제)
- 도장 찍은 곳은 목록에서 숨기고 [갔다온 곳] 탭에 모음
- 저장 구조 `{v:도장, c:추가장소, w:가보고 싶은 곳+날짜, r:할인율 메모}`
- 🔗 카드 바깥 링크 3종 (네이버지도 / 관광포털 검색 / 후기·정보 검색) — 전부 장소 이름 기반 검색 링크
- 📝 데이터 품질: 지도에서 검색되는 이름 표기, 시장 안 가게는 지번+시장 내 주소
- ✈️ **항공편 · 탑승권 읽기** (2026-08-30) — 아래 상세
- 🎟 **그 지역 공식 할인 제도 안내**(`COUPONS`) — 롯데렌터카 쿠폰팩을 대체
- 🗂 **첫 화면 타일 구조 + 접이식 메뉴** (2026-08-30 전면 정리)

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
| `COUPONS` | **그 지역**의 할인 제도(지역화폐·관광증·무료 개방일). 반드시 새로 조사할 것 |

**설계상 반드시 지킬 것**

- 탑승권 바코드(IATA BCBP)에는 **출발 시각과 탑승구가 들어 있지 않다.** 규격에 그 칸이 없다.
  시각은 사용자가 한 번 넣고, 탑승구는 실시간 조회 링크로 넘긴다. 이 전제를 바꾸려 하지 말 것
- 카운터·탑승구 번호는 **당일 배정**이라 코드에 적지 않는다. "전광판 확인"으로 안내
- 탑승객 이름·예약번호는 **공유 저장소에 올리지 않는다.** 각자 기기에만(`jeju_flights_v1`)
- 인식기는 셋을 **고르지 말고 다 돌린다**: 기기 내장(BarcodeDetector) → ZXing → jsQR.
  내장 인식기 호출은 **반드시 `withTimeout`** — 답을 영영 안 주는 기기가 있다

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
| **초점이 조금만 나가면 QR 이 통째로 안 읽힘** | 실측: 또렷하면 QR 150px 로도 읽히는데, **2px만 뭉개지면 500px 이어도 전부 실패**. 해상도를 올려도 소용없다 | 선명화(`unsharp`)를 갈래에 넣고, 카메라를 3840×2160으로 요청하고, 화면을 누르면 초점을 다시 잡게 했다(`refocus`). 줄이기보다 **잘라내기**를 앞세운다 |
| 그래도 그 폰에서는 끝내 안 읽힘 | 미리보기 화질은 웹페이지가 어떻게 할 수 없다 | **[📸 찍어서 읽기]**(`capture="environment"`)로 폰 사진 앱을 열어 찍게 한다. 사진 앱은 초점을 제대로 잡는다 |
| 화면이 정신없다 | 큰 그라데이션 버튼 4개 + 떠다니는 버튼 2개가 겹치고, 탭 12개가 여러 줄로 흩어지고, 머리말이 화면 한 장을 먹었다 | 타일 격자로 통일 + 탭은 한 줄 스크롤 + 머리말은 두 줄, 긴 설명은 접이식으로 |
| 접이식 메뉴를 눌러도 안 열림 | 여는 연결이 `render()` 안에 있어 다시 그릴 때마다 중복 등록됐다 | 시작할 때 한 번만 걸고 `dataset` 표식으로 막는다 |
| 번들거리거나 굽은 종이 탑승권을 놓침 | 화면 **전체**의 밝기 차이만 벌려서(`boostContrast`) 한쪽만 밝은 사진을 못 잡음 | **자리마다 밝기를 따로 재서** 검정/흰색을 가른다 (`adaptiveBin` · 적분영상이라 창이 커도 픽셀당 한 번). 갈래마다 **줄이는 크기도 다르게** 한다 |

**지금 탑승권을 읽는 방법은 [📸 찍어서 읽기] 하나다.** `capture="environment"` 로 폰 사진 앱을
열어 찍게 하고, 그 사진을 `decodeImageFile` 에 태운다. 사진 앱은 초점을 제대로 잡으므로 확실하다.
[🖼 저장된 사진에서 찾기]·[⌨️ 직접 입력]도 함께 있다.

**카메라로 계속 비추는 스캔은 화면에서 뺐다** (2026-08-30 · 여섯 번 고쳐도 그 폰에서 끝내 안 됨).
코드(`startScan`·`pickEngine`·`#flScan`·또렷함 표시)는 **지우지 않았다.** 되살리려면
버튼 하나와 연결 한 줄만 넣으면 된다. 다시 넣자는 얘기가 나오면 **먼저 재보게 할 것.**

**인식 갈래는 10가지**(`SCAN_PASSES`)를 번갈아 쓴다. 실제 종이 탑승권으로 재보면
**촬영 거리마다 이기는 갈래가 매번 다르다.** 네 축을 섞는다:
- `sharp` — 선명화(언샤프 마스크). **초점이 조금만 나가도 QR 은 통째로 안 읽힌다.** 이게 진짜 원인이었다
- `adap` — 자리마다 밝기를 따로 재서 검정/흰색을 가른다 (번들거림·굽은 종이·그림자)
- `zoom` — 가운데만 잘라낸다. **줄이기(`max`)보다 잘라내기를 앞세울 것** — 줄이면 QR 한 칸의 픽셀이 같이 준다
- `max` — 줄이는 크기를 갈래마다 다르게 (같은 사진도 크기에 따라 읽히고 안 읽힌다)

**실측한 한계** (다시 손볼 때 기준으로 쓸 것):

| 화면 상태 | 읽히는 한계 |
|---|---|
| 또렷함 | QR 150px(모듈당 2.5px)로도 읽힘 |
| 1px 뭉개짐 | 260px 아래로 실패 |
| **2px 뭉개짐** | **500px 이어도 전부 실패** (해상도로는 못 이긴다) |

**아직 안 해본 마지막 수단**: `ImageCapture.takePhoto()` — 카메라를 연 채로 "사진 품질" 프레임을
받아오는 것. 되면 자동 인식이 살아나지만 기기마다 지원이 들쭉날쭉하고 느리다.
**사용자와 상의 없이 시도하지 말 것** (이미 여섯 번 헛수고했다).

**검증 방법**: jeju 저장소의 `tools/` 를 쓴다.
```bash
pip install qrcode pillow pdf417gen
python3 tools/make-test-passes.py /tmp/passes
node tools/verify-scan.mjs /tmp/passes
```
기준값 **16/20 인식 · 실시간 카메라 흐름 통과 · 내장 인식기 고장 흉내 4가지 통과**.

## 장소 하나를 추가할 때 같이 채워지는 표

`PLACES` · `TEL` · `PK` · `EFFORT` · `ZONE_OF` · `LL` — 6곳.
테마가 새로 생기면 여기에 `CHIPS` 한 줄이 더 붙는다.
(항공편 기능은 장소 데이터와 무관하므로 장소 추가 시 손댈 것 없음)

## 코드 구조 목록 (이 시점 기준)

여기 **없는 이름이 새로 나타나면 그게 새 기능**이다.
(데이터만 바뀌면 이름이 안 늘어도 파일 크기가 커진다 — 그럴 땐 반드시 실제 diff를 볼 것)

```
AIRLINES AIRLINE_OF AIRPORTS AP_STEPS BARTIER BAR_T CARRIER_ETC CAT CATS
CAT_EMOJI CHEAPG CHEAP_GROUPS CHIPS CHO_LIST CJU_LIVE COUPLE_KEY COUPONS
DOW DOW_F EFF EFFORT EFF_OF EFF_ORDER FKEY FT FTYPE GLOSSARY GLO_KEYS
GLO_RE HOTELTIER HOTEL_T ICAO_IATA JEJU_AIRPORT KEY LL LOTTE LOTTE_ALL
LOTTE_IDS LOTTE_URL MUST MUSTBAR MUSTEAT MUSTHOTEL MUSTSHOP MUSTSPA
NEAR_LIMIT_KM NM PHOTO PK PKMAP PKT PK_OF PK_ORDER PLACES QR_LIBS
READ_URL SCAN_CAP_LIVE SCAN_LIBS SCAN_MAX SCAN_MAX_FULL SCAN_PASSES
SHOPTIER SHOP_T SPATIER SPA_T STARS TEL TIERMAP TIMED_OUT UPD_SEEN_KEY
UPD_URL VJ WRITE_URL ZONES ZONE_KW ZONE_OF activeEff activeZone
adaptiveBin addCheapGroups addCustomPlace addEffGroups addFoodGroups
addGrid addRouteGrid addSubHead addTierGroups allPlaces apIsKR apLive
apName apOptions autoSync barNear bcbpShift boostContrast byEff byPk
camError carrierName cdText chipMatch chipsEl clearNearby closeFlight
copyAddr couponModal currentFilter customPlaces customToCard daysAway
decodeImageFile delFlight deleteCustomPlace distKm drawCoupons drawUpd
drawUpdFail effGrid effOf ensureJsQR ensureZXing escHtml fetchRemote
flCanvas flDraft flMsg flPass flStream flTorchOn flightIntl flightModal
flightSearch flightTimes fmtDateF fmtDay fmtDist fmtHM foldNow
frameBrightness ftOf getNativeDetector gloDef gloInput gloModal gloSug
gloWord glossify grabCanvas grabPixels handlePhoto hasPlace hopKm
hoursModal isWished isoDate jsqrCanvas jsqrRead julianToISO list llOf
loadFlights loadScript lsGet lsSet makeCard markUpdBtn matchesEff
matchesSearch mergeCustom modal myFlights nearbyBtn nearbyOn nextPass
normalize onDecoded onSelEnd online openFlight openGlo openShot openUpd
parseBCBP parseLoose parsePass passes pathLen persistFlights pickEngine
pkOf placeText planGroup pushRemote rateOf rateSrc rates refocus render
renderAirTable renderApSteps renderEffMenu renderFilterBar
renderFlightBar renderFlightForm renderFlightPreview renderHoursTable
renderPlan renderPlanByDate renderPlanByZone renderSavedFlights
renderZoneMenu routeNote routeOrder saveDraft saveLocal saveRate
saveWish scanCap scrollToList searchClear searchInput searchQ selBtn
setAiLinks setEngine setFlPane setTab setWishDate setupFold setupTorch
shBuf shCache sharpness showGlo sortFlights startScan stopScan syncChips
syncDraft ticketHtml toCho toggleBarNear toggleTorch toggleVisit
toggleWish torchTrack unsharp updBtn updFeed updModal updSeen
updateProgress updateSyncLabel updateVisitedTab visibleCount visited
wish withTimeout zoneGrid zoneOf zxDecodeCanvas zxHints
```
