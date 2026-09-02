# channel1 폴더에서 작업하는 채팅창 만들기

> 사용자가 "컴퓨터에 있는 channel1 폴더에서 작업할 수 있는 채팅창 못 만드니?"라고 물어서
> 2026-09-02에 정리한 안내. 폰에서 보기 좋은 안내서:
> https://claude.ai/code/artifact/fef099d7-3809-4443-8ae0-fbb89b6cfedc

## 왜 지금 채팅창에서는 안 보이나

claude.ai/code 세션은 인터넷 저편 임대 컴퓨터(클라우드 컨테이너)에서 돈다.
사용자 컴퓨터 안의 폴더는 여기서 절대 안 보인다. 아래 셋 중 하나를 해야 보인다.

## 세 가지 길

| 길 | 폰에서 | 파일 올리기 | 큰 파일 | 조건 |
|---|---|---|---|---|
| A. 컴퓨터에서 바로 (데스크톱 앱) | 안 됨 | 필요 없음 | 됨 | 맥·윈도우 |
| B. GitHub 비공개 저장소 | 됨 | 한 번 필요 | 안 됨 | 파일당 25MB(브라우저 업로드) |
| C. Dispatch (폰 → 내 컴퓨터) | 됨 | 필요 없음 | 됨 | 컴퓨터 켜둘 것 · Pro/Max |

### A. 컴퓨터에서 바로

1. https://code.claude.com/docs/en/desktop 에서 맥·윈도우 앱 내려받기
2. **윈도우만** — https://git-scm.com/downloads/win 로 Git for Windows 먼저 설치 후 앱 재시작
3. 앱 실행 → 로그인 → 맨 위 **Code** 탭
4. 입력창 위에서 **Environment: Local**, **Project folder: channel1 폴더**
5. 말 걸면 끝

### B. GitHub에 올려두기 (폰에서 쓰려면)

1. https://github.com/new → 이름 `channel1` → **Private** → Create
2. `uploading an existing file`에 **글 파일만** 끌어다 놓기 (영상·녹음 원본 제외)
3. Commit changes
4. 폰에서 https://claude.ai/code → 새 대화 → 저장소 `channel1` 선택

### C. Dispatch — 폰에서 내 컴퓨터의 폴더를 그대로

1. A를 먼저 끝낸다 (C는 A 위에 얹는 기능)
2. 앱의 **Cowork** 탭에서 Dispatch를 켜고 폰과 연결
   (설정법: https://support.claude.com/en/articles/13947068)
3. 폰의 Claude 앱에서 "channel1 폴더에서 ○○ 해줘" → 컴퓨터에서 세션이 열려 작업 → 폰으로 알림
4. 그 세션은 컴퓨터 Code 탭에 **Dispatch** 배지를 달고 남는다

## 다음 세션이 알아야 할 것

- **`goldlucky7/channel1` 저장소는 사용자가 직접 만들어야 한다.**
  Claude의 GitHub 앱에 저장소 *생성* 권한이 없다 (`POST /user/repos` → 403).
  이미 있는 저장소에 푸시는 되지만, 새로 만드는 건 안 된다.
- 저장소가 생겼다고 하면 → `add_repo` → clone → `register_repo_root`,
  그리고 안에 `CLAUDE.md`(인수인계 문서)를 만들어 채널1이 무슨 폴더인지 적어둘 것.
- 사용자는 폴더 안에 뭐가 들었는지 "섞여 있음 / 잘 모름"이라고 답했다.
  영상 원본이 섞여 있을 수 있으니 B를 안내할 때 크기 제한을 꼭 같이 말할 것.
- 사용자가 고른 방향은 **"둘 다 해두기"** — A/C를 먼저, B는 여유 될 때.
