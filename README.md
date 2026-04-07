# /mbo — Management by Objectives for Claude Code

> **Give AI autonomy. Hold it accountable. Demand results.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-blue)](https://claude.ai/code)

AI 코딩 어시스턴트에게 자율을 주면서도, 합의된 목표를 반드시 달성하게 만드는 Claude Code 스킬.

---

## The Story

어느 날, PO(Product Owner)가 결심했다.

> *"MBO(Management By Objective) 방법을 오늘부터 본격적으로 적용해서 Claude Code에게 작업을 시키기로 결심을 했다."*

이유가 있었다. 62개 Task를 실행시켰는데 돌아온 건 빈 껍데기뿐이었다. "완료"라고 보고했지만 실제로 열어보면 텅 비어 있었다. 기존 프로토타입은 무시됐고, 디자인은 연구조차 없었고, 방향 없이 코드만 쏟아냈다. 결국 전부 재작업해야 했다.

PO는 말했다.

> **"과정은 너의 마음대로 진행해도 좋다. 그러나, 나랑 합의를 해서 사전에 설정한 목표는 무조건 달성해야 한다. 단, 품질은 최고로, 비용은 합리적 수준으로, 투입시간은 적절하게."**

그래서 Claude Code는 마음을 먹었다. 이 철학을 코드로 만들겠다고. `.claude/skills/mbo` 스킬을 만들어서 다음 원칙을 새겼다:

- **합의된 목표는 무조건 달성** — 목표 달성이 최우선. 과정은 자유, 결과는 필수.
- **품질은 최고로** — 대충 끝내는 것은 달성이 아니다. 상품성 있는 결과물이어야 한다.
- **비용은 합리적으로** — 불필요한 서브에이전트 남발, 중복 작업, 과잉 설계를 하지 않는다.
- **투입시간은 적절하게** — 빠르되 품질을 희생하지 않는다. 느리되 낭비하지 않는다.
- **측정 가능한 KPI** — "좋게 만든다"가 아니라 "Lighthouse 80점 이상"처럼 수치화
- **승인 = 합의** — PO가 목표를 이해하고 동의한 뒤에만 작업. 승인 없이 실행 금지.
- **과정은 자율** — 목표 달성 방법은 AI가 판단. PO는 과정에 간섭하지 않는다.
- **결과는 목표 대비** — "뭘 했다"가 아니라 "목표를 달성했다/못했다"로 보고
- **미달성은 사유와 후속** — 실패도 기록해야 다음에 반복 안 함

PO는 선언했다.

> **"오늘부터 MBO 엔지니어링의 시대가 활짝 열리는 것이다."**

이 스킬은 그렇게 만들어졌다.

---

## Why MBO?

AI 코딩 어시스턴트에게 작업을 시키면 이런 일이 벌어집니다:

- 62개 Task를 실행했는데 **빈 껍데기**만 만들어짐
- "완료"라고 보고하지만 **실제로는 동작하지 않음**
- 방향 없이 코드만 쏟아내서 **나중에 전부 재작업**

`/mbo`는 이 문제를 구조적으로 해결합니다. 작업 전에 목표를 합의하고, 작업 후에 목표 달성 여부를 검증합니다. "뭘 했다"가 아니라 **"달성했다 / 못했다"** 로 보고합니다.

---

## How It Works

```bash
/mbo                    # 대화 맥락에서 자동으로 목표 도출
/mbo 디자인 혁신         # 특정 주제 지정
/mbo report             # 진행 중인 MBO의 달성 여부 보고
```

### 3-Phase Process

```
PHASE 1: 목표 정의
  ① 맥락 분석 — 무엇을, 왜, 어디까지
  ② AS-IS 조사 — 현재 상태 실제 확인
  ③ TO-BE 정의 — 구체적, 측정 가능한 목표
  ④ KPI 설정 — 성공을 어떻게 측정할지
  ⑤ Task 도출 — 목표 달성에 필요한 작업
        ↓
  PO에게 목표서 제시 → 승인 대기
        ↓
PHASE 2: 실행
  ⑥ MBO 파일 저장 (추적용)
  ⑦ 자율 실행 (과정은 AI 판단)
  ⑧ 중간 점검 (필요 시)
        ↓
PHASE 3: 결과 보고
  ⑨ 목표 달성 여부 대조 (AS-IS → TO-BE → 실제)
  ⑩ KPI 목표값 vs 실측값
  ⑪ 미달성 항목 사유 + 후속 조치
```

---

## Installation

### Option 1: Manual

```bash
mkdir -p ~/.claude/skills/mbo
curl -o ~/.claude/skills/mbo/SKILL.md \
  https://raw.githubusercontent.com/SUNWOONGKYU/mbo-skill/main/SKILL.md
```

### Option 2: Clone

```bash
git clone https://github.com/SUNWOONGKYU/mbo-skill.git
cp mbo-skill/SKILL.md ~/.claude/skills/mbo/SKILL.md
```

Then use `/mbo` in Claude Code.

---

## Use Cases

### Software Development
```
/mbo API 리팩토링
→ AS-IS: 응답 2.3초, 에러율 5%
→ TO-BE: 응답 500ms 이하, 에러율 0.1% 이하
→ KPI: p95 latency, error rate
```

### Design Overhaul
```
/mbo 디자인 혁신
→ AS-IS: 제네릭 대시보드, Lighthouse 45점
→ TO-BE: 브랜드 아이덴티티 확립, Lighthouse 80+
→ KPI: Lighthouse score, 다크/라이트 깨짐 0건
```

### Migration
```
/mbo DB 마이그레이션
→ AS-IS: PostgreSQL 12, 다운타임 필요
→ TO-BE: PostgreSQL 16, 무중단 마이그레이션
→ KPI: 데이터 손실 0건, 다운타임 0분
```

---

## 9 Core Principles

1. **합의된 목표는 무조건 달성** — 과정은 자유, 결과는 필수
2. **품질은 최고로** — 대충 끝내는 것은 달성이 아니다
3. **비용은 합리적으로** — 불필요한 남발, 중복 작업, 과잉 설계 금지
4. **투입시간은 적절하게** — 빠르되 품질을 희생하지 않는다
5. **측정 가능한 KPI** — "좋게 만든다"가 아니라 수치화
6. **승인 = 합의** — PO가 동의한 뒤에만 실행. 승인 없이 실행 금지
7. **과정은 자율** — 방법은 AI가 판단. PO는 과정에 간섭하지 않는다
8. **결과는 목표 대비** — "뭘 했다"가 아니라 "달성했다/못했다"로 보고
9. **미달성은 사유와 후속** — 실패도 기록해야 다음에 반복 안 함

---

## MBO Goal Document Format

`/mbo` 실행 시 AI가 자동으로 이 양식의 목표서를 생성합니다:

```markdown
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  MBO 목표서 — {작업명}
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## 최상위 목표
"{한 줄로 정의된 목표}"

## 현재 vs 목표
| 항목 | 현재 (AS-IS) | 목표 (TO-BE) |
|------|-------------|-------------|
| ...  | ...         | ...         |

## 측정 지표 (KPI)
| 지표 | 현재값 | 목표값 | 측정 방법 |
|------|--------|--------|----------|
| ...  | ...    | ...    | ...      |

## 실행 계획
| # | Task | 설명 | 예상 결과 |
|---|------|------|----------|
| 1 | ...  | ...  | ...      |

## 리스크
| 리스크 | 대응 방안 |
|--------|----------|
| ...    | ...      |

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
이 목표를 승인하시겠습니까?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## MBO Result Report Format

작업 완료 시 `/mbo report`로 목표 달성 여부를 보고합니다:

```markdown
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  MBO 결과 보고 — {작업명}
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## 최상위 목표
"{목표}" → 달성 / 미달성 / 부분달성

## 목표 달성 여부
| 항목 | AS-IS | TO-BE | 실제 결과 | 달성 |
|------|-------|-------|----------|:----:|
| ...  | ...   | ...   | ...      | O/X  |

## KPI 실측
| 지표 | 목표값 | 실측값 | 달성 |
|------|--------|--------|:----:|
| ...  | ...    | ...    | O/X  |

## 미달성 항목 (있을 경우)
| 항목 | 사유 | 후속 조치 |
|------|------|----------|
| ...  | ...  | ...      |
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Compatibility

- **Claude Code** (CLI, Desktop, Web)
- Works with any project type

---

## Contributing

이 스킬이 도움이 됐다면:

1. Star 눌러주세요
2. 개선 아이디어는 Issue로
3. 직접 기여하려면 PR 환영합니다

---

## License

MIT

---

## Author

**SUNWOONGKYU** — Building AI-powered development workflows.

> *"The process is yours. The goal is ours. Quality is non-negotiable."*
