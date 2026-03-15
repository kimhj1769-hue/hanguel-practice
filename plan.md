# 펭귄 한글 타자연습 — 개발 계획 (plan.md)

## 배포 주소
- **Firebase Hosting**: https://studio-7599335063-c68f7.web.app
- **GitHub**: https://github.com/kimhj1769-hue/hanguel-practice

---

## 현재 상태 (v1.2 완료 — 2026-03-15)

### v1.0 기반
- [x] 메인 화면 — 펭귄 로고, 4가지 모드 버튼, 최고기록 표시
- [x] 난이도 선택 화면 — 쉬움 / 보통 / 어려움
- [x] 낱말 연습 모드
- [x] 문장 연습 모드
- [x] 속도 도전 모드 (떨어지는 단어)
- [x] 점수 / 타이머 / 정확도 / 콤보 HUD
- [x] 콤보 팝업 & 파티클 이펙트
- [x] 펭귄 정답/오답 애니메이션
- [x] 일시정지 기능 (ESC / ⏸ 버튼)
- [x] 결과 화면 (CPM, 정확도, 신기록)
- [x] 최고기록 localStorage 저장
- [x] 반응형 모바일 대응

### v1.1 캐릭터 & 모드 추가
- [x] 공룡 → 귀여운 펭귄 캐릭터로 교체 (전체 이모지 🐧)
- [x] 기본자리 연습 모드 추가 (홈포지션: ASDFGHJKL)
- [x] 타이핑 소리 효과 — 키 클릭 / 정답 아르페지오 / 오답 하강음
- [x] BGM 변경 — 150BPM 경쾌한 펭귄 테마 (뮤직박스 스타일)
- [x] BGM 온/오프 토글 버튼
- [x] 게임 중 처음으로 돌아가기 버튼 (🏠)
- [x] 입력창 실시간 글자별 색상 피드백 (char-box 초록/빨강)
- [x] 생명 시스템 (하트 3개)
- [x] 한글 IME 이중 제출 버그 수정 (isSubmitting / isComposing 플래그)

### v1.2 UI 개선 & 코드 품질
- [x] 손가락 가이드 — 입력창 위(타이핑 영역)로 이동, 컴팩트 디자인
- [x] 키보드 패널 — 비활성 키 음영 처리(opacity 0.28), 활성 키 강조
- [x] 단어/문장 DB 약 590개로 대폭 확장
  - WORDS.easy ~200개 / WORDS.normal ~230개 / WORDS.hard 52개
  - SENTENCES.easy 44개 / SENTENCES.normal 38개 / SENTENCES.hard 24개
  - 카테고리: 과일, 동물, 자연, 일상, 가족, 색깔, 학교, 계절, 감정, IT, 음식, 장소, 채소, 교통, 스포츠, 직업, 음악
- [x] **코드 품질 개선 (simplify 적용)**
  - `ensureAudioCtx()` — AudioContext 초기화 중복 제거
  - `getUsedFingers(word)` — 손가락 매핑 순회 로직 통합
  - `getFgEl(id)` — th 특수케이스 중복 제거
  - `resetFingerGuide()` — prepareGame 인라인 루프 함수화
  - `screenEls` 캐시 — showScreen querySelectorAll 매번 호출 제거
  - 타이머 danger/urgent 클래스 플래그로 1회만 추가
  - `updateHUD` hud-timer 이중 갱신 제거
  - result-dino 죽은 분기 수정
  - `SFX_CORRECT_NOTES` 상수 분리
  - `confirmQuitToHome` 불필요 래퍼 제거
- [x] Firebase Hosting 배포 완료

---

## v1.3 — 게임성 강화
- [ ] 레벨 시스템 (경험치 누적으로 레벨 업)
- [ ] 펭귄 스킨 잠금 해제 (점수 달성 시)
- [ ] 아이템 시스템 (시간 연장, 콤보 보너스)
- [ ] 카테고리 선택 화면 추가

## v1.4 — 기록 & 통계
- [ ] 주간/월간 통계 차트
- [ ] 자주 틀리는 단어 복습 기능
- [ ] 타수 향상 그래프

## v2.0 — 멀티 & 확장
- [ ] 대결 모드 (2인 키보드 분할)
- [ ] 온라인 랭킹 (Firebase Firestore 연동)
- [ ] 선생님 모드 — 단어 목록 직접 입력
- [ ] PWA 지원 (오프라인 실행, 앱 설치)
- [ ] 영어 타자 연습 모드 추가

---

## 기술 부채 / 리팩토링 메모
- 단어 데이터가 더 많아지면 별도 `words.js` 파일로 분리 고려
- speed 모드 낙하 단어 충돌 방지 로직 개선 필요 (겹치는 경우)
- 모바일 소프트 키보드 대응 레이아웃 추가 검토
- `spawnParticles` DOM 생성 반복 → CSS 애니메이션 방식 개선 고려
