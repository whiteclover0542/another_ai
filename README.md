# another_ai — T05 AI 인계 실험

한 AI가 중단되거나 다른 AI로 바뀌어도 저장소와 인계 문서만으로 같은 작업을 이어갈 수 있는지 확인하는 실험용 저장소.

- 과제 원문(동결): [ASSIGNMENT.md](ASSIGNMENT.md)
- 진행 상황·선택·체크리스트: [PROGRESS.md](PROGRESS.md)
- 공개 주소: https://whiteclover0542.github.io/another_ai/ (GitHub Pages 활성화 후 확정)

## 이 저장소의 앱

과제 4로 만든 [today_information](https://github.com/whiteclover0542/today_information)(오늘의 CVE 정보판) 앱을 그대로 복사해와 독립적으로 개선한다. 원본 저장소·배포는 건드리지 않는다 — 자세한 이유와 범위는 [PROGRESS.md](PROGRESS.md)의 "카드 1" 참고.

- 복사해온 시점의 원본 문서: [docs/original-assignment/](docs/original-assignment/)
- 이번에 추가하는 기능: 대표 CVE 목록 심각도 필터 (자세한 정의는 PROGRESS.md 참고)

## 실행

빌드 단계 없는 정적 사이트다.

```bash
npx serve .        # 또는 원하는 정적 서버로 index.html 열기
```

## 구조

```
index.html                      # 정보판 화면
assets/
├── app.js                      # fetch·렌더링·장애 시뮬레이터·비교/위험도 계산 (+ 이번에 추가할 심각도 필터)
└── style.css
data/
└── history.json                # 날짜별(KST) 기록 — Actions가 추가, 앱은 읽기 전용
scripts/
└── fetch-daily-count.mjs       # NVD 조회 → history.json 갱신 스크립트
.github/workflows/
└── daily-cve-count.yml         # 매일 09:00 KST 실행 배치
docs/original-assignment/       # 복사해온 시점의 원본 README·ASSIGNMENT·PROGRESS (참고용, 수정 안 함)
ASSIGNMENT.md                   # T05 과제 원문 (동결)
PROGRESS.md                     # T05 진행 상황·선택 기록
```
