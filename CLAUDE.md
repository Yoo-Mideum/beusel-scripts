# 뷰셀 대본 보드 — 저장소 규칙 (Claude Code용)

GitHub Pages 배포. 새 회차 추가 순서:
1. `scripts/NN_제목.md` 작성 (NN 두 자리)
2. `episodes.json` 의 episodes 배열에 항목 추가 — n, title, given(YYYY-MM-DD, 반드시 수요일, 이전 회차 +7), status, hook, file, memo, sources([[제목, URL], ...])
3. `python3 build.py` 실행 → 루트 index.html + epNN/index.html 재생성
4. push (커밋 메시지 한글, 바뀐 것 목록)

## md 형식
- `## 0:00 훅` 처럼 `## 시간 구간명` 으로 구간 시작
- 낭독 문장은 한 줄에 한 호흡 · 화면 지시는 `[화면: ...]` 한 줄 · 메이브님이 채울 값은 【 】
- 인포그래픽은 `assets/epNN_이름.svg` (viewBox 900×260~300, 배경 #0F172A, 강조 #F59E0B/#FDE68A) → `![설명](assets/epNN_이름.svg)`
- 상단 `> ` 메모는 음절 계산 제외. 목표 2,800~3,100음절

## 페이지 규칙
- 각 페이지 self-contained (CSS·JS 인라인, 외부는 구글 폰트만). 수정은 build.py의 CSS/템플릿을 통째로 다시 쓴다.
- 촬영일(+2)·공개일(+7)은 build.py가 계산. status: 시작 전/대본 작성 중/대본 완료/촬영 완료/공개 완료

## 톤·구조
- 차갑게·단정문·한 문장 한 정보·감정어 금지. 실적 문구 "5개월 동안 화장품 셀러 200명" 고정. 훅 = 숫자+반전+약속. 매 회차 솔직 구간 1개. CTA 마지막 한 번.
- 숫자·연도·브랜드·수출액은 검색으로 확인된 것만, 미확인은 "확인 필요". sources에 실제 URL.

## 영상 링크
- 허브의 "영상 링크 등록" 버튼 → `upload-link` 라벨 Issue 생성. 클로드가 Issue를 읽어 `episodes.json`의 해당 회차에 `"video": "URL"`을 넣고 build·push 후 Issue 닫기.

## 주제 후보
- `topics.json`에 회차 후보(시리즈 태그·훅·공부 유도 질문·상태). `topics/index.html`로 별도 렌더, 허브 가이드 박스에서 링크. 허브는 해야 할 것(진행 중) → 예정 → 완료(드롭다운) → 가이드 박스 순. 회차로 확정되면 status를 "N화 확정"으로 바꾸고 episodes.json에 추가.
