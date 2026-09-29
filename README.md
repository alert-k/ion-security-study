# ION Security Study

커버트 채널·사이드 채널을 중심으로 한 주간 스터디 기록.

이론에서 시작해 직접 구현·측정·재현으로 넘어가고, 마지막에 탐지·방어 관점으로 돌아오는 순서로 진행한다.
모든 실습은 **본인 소유 격리 랩** 또는 **본인이 보고해 이미 공개·수정된 취약점**으로 한정한다.

## 구조

```
weekly/
├── 2026-08/    이론 — 정보흐름 모델부터 투기실행까지
└── 2026-09/    실습 — 코드 감사·CVE 재현·채널 측정·탐지
_template/
└── weekly-format.md
```

## 진행 경과

### 2026-08 — 이론

| 주차 | 주제 |
|---|---|
| 1주 | 접근제어 vs 정보흐름 제어, Bell–LaPadula·Biba·non-interference, Lampson의 격리 문제, 커버트/사이드 채널 판별 기준, Shared Resource Matrix, Shannon 채널 용량 |
| 2주 | 커버트 채널 심화 — 로컬 저장/타이밍 채널, 네트워크 프로토콜 기반 채널, 에어갭 물리 채널, 동기화·프레이밍·오류정정, 탐지·정규화 방어 |
| 3주 | 사이드 채널 기초 — 캐시 구조와 주소 분해, 고전 타이밍 공격, Evict+Time / Prime+Probe / Flush+Reload, 상수시간 프로그래밍 |
| 4주 | 물리 사이드 채널과 투기실행 — SPA/DPA/CPA와 리키지 모델, 결함주입·Rowhammer, Meltdown·Spectre·MDS, Hertzbleed·GoFetch, 방어 체계 7층 종합 |

### 2026-09 — 실습

| 주차 | 주제 |
|---|---|
| 1주 | 이론을 실코드에 적용 — 비밀 의존 분기·인덱스·조기반환 비교 감사, 상수시간 교체 후 생성 어셈블리 확인, `dudect` 방식 t-검정, DFA 키 복구식 유도 |
| 2주 | 문헌의 사이드 채널을 격리 랩에서 실행 — Flush+Reload 수신부 재구축과 임계값 산출 절차 고정, 자체 테이블 기반 AES 취약 빌드에 T-table 키 복구, AES-NI 대조, Spectre v1(CVE-2017-5753)·Meltdown(CVE-2017-5754) 재현 시도와 완화 확인 |
| 3주 | 8월 이론의 정량 검증 — 캐시 채널 비트오류율 측정, `C = 1 − H(p)` 실측 대입, 실효 용량 곡선, Prime+Probe 재현, 측정 조건 통제 |
| 4주 | 탐지·방어 관점 전환 — 직접 만든 채널을 스스로 탐지, 탐지 한계의 규명, 9월 종합, 다음 단계(데이터 등급 경계 유출통제) |

## 기록 원칙

- **실패와 미완을 지우지 않는다.** 각 주차의 「8. 특이사항」에 남긴다.
- **AI는 도구로만 쓴다.** Tutor / Socratic Partner / Debugger / Reviewer / Interviewer / Research Assistant 역할로 쓰고, 결과는 반드시 직접 실행해 검증한다. AI 판정이 실행으로 뒤집힌 사례도 기록한다.

## 작성 형식

[`_template/weekly-format.md`](_template/weekly-format.md) 의 8개 절을 따른다.
