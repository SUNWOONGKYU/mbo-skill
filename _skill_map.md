# mbo-천상 — 통솔 색인 (Skill Map)

> 본 색인은 mbo-천상의 **부록**이다. SKILL.md 본문은 외부 스킬 이름에 의존하지 않고 자기완결적으로 작성된다. 이 파일은 mbo-천상이 통솔하는 전체 스킬 카탈로그와, 본문에서 일반화한 동작(다관점 토론·소대 편제·구조화 개발 등)이 가리키는 정형 스킬을 *별도*로 정리한다 — 본문 동작을 이해하는 데 필요하지 않지만, 카탈로그·매핑이 필요할 때 펼쳐본다.

---

## 1. 통솔 카탈로그 — 46 스킬

| 계층 | 수 | 스킬 |
|---|---|---|
| 천상 | 1 | mbo-천상 |
| 4 사신 | 4 | 청룡 sal-grid-dev · 백호 platoon-formation · 주작 sal-da · 현무 buzzlab-simulation |
| 코어 | 4 | review-evaluate-코어1 · slideshow-web-코어2 · 5times-debug-loop-코어3 · pro-persona-debate-코어6 |
| 기본 | 26 | 팀 편성 3 · 개발·인프라 4 · 콘텐츠·생성 3 · 영상 2 · 품질·테스트 6 · 배포·한국·협력 3 · Obsidian/MD 도구 5 |
| 메타 제작 | 2 | skill-create-코어5 · 에신-llm-dependent-agent-create |
| 도메인 특화 | 9 | CPC 인프라 3 · 정치·평가 4 · 여론 1 · Obsidian Vault 디렉터 1 |

총: 1 + 4 + 4 + 26 + 2 + 9 = **46** (`~/.claude/skills/` 실측 일치, 2026-05-30 기준)

### 기본 26 상세
- **팀 편성 (3)**: deploy-subagent-기본 · deploy-skill-기본 · find-skills-기본
- **개발·인프라 (4)**: api-builder-기본 · ui-ux-builder-기본 · db-schema-기본 · cicd-setup-기본
- **콘텐츠·생성 (3)**: ai-image-기본 · diagram-기본 · doc-generator-기본
- **영상 (2)**: youtube-기본 · video-frames-기본(Deprecated, 호환 포인터)
- **품질·테스트 (6)**: security-audit-기본 · e2e-test-기본 · api-test-기본 · troubleshoot-기본 · performance-check-기본 · n8n-workflow-test
- **배포·한국·협력 (3)**: vercel-private-url-배포 · 공공양식-기본 · 용병소집-기본
- **Obsidian/MD 도구 (5)**: defuddle · json-canvas · obsidian-bases · obsidian-cli · obsidian-markdown

### 도메인 특화 9 상세
- **CPC 인프라 (3)**: cpc-setup · cpc-add-project · cpc-engage
- **정치·평가 (4)**: buzzlab-politician-winning-strategy · campaign-route-strategy · evaluate-politician-platoon · evaluate-politician-v50
- **여론 (1)**: weekly-opinion-report
- **Obsidian Vault 디렉터 (1)**: 옵신-claude-wiki-obsidian-vault

---

## 2. SKILL.md 본문 동작 ↔ 정형 스킬 매핑

본문에서 일반 명칭으로 설명한 동작은 다음 정형 스킬을 가리킨다 (필요 시 호출).

| SKILL.md 본문 동작 | 정형 스킬 |
|---|---|
| 다관점 토론 (3 전문가 + DA, s1~s5 5단계) | pro-persona-debate-코어6 |
| 소대 편제 (소대장 + 분대 N개 + 용병 4 = 45명+) | 백호 platoon-formation |
| 구조화 개발 (Stage·Area·Level 좌표, 6단계 Stage 루프) | 청룡 sal-grid-dev |
| 다차원 진단·감사 (SAL Grid 역방향 적용) | 주작 sal-da |
| 구조화 토론 BPI 예측 (s1~s5) | 현무 buzzlab-simulation |

---

## 3. 4 방위 ↔ 4 사신 ↔ 4 방법론 매핑

본문 위상 다이어그램의 4 방위가 가리키는 4 사신과 그 방법론.

| 방위 | 사신 | 방법론 | 정형 스킬 |
|---|---|---|---|
| 東 | 청룡 | 개발방법론 | sal-grid-dev |
| 西 | 백호 | 소대 편제 | platoon-formation |
| 南 | 주작 | 진단·감사 | sal-da |
| 北 | 현무 | 토론 예측 | buzzlab-simulation |

---

## 4. 갱신 규칙

스킬을 추가·삭제·개명할 때 이 색인과 총수를 갱신한다. SKILL.md 본문은 외부 스킬 이름에 의존하지 않으므로 색인 갱신만으로 종합 허브가 유지된다.

### 갱신 트리거 (자가검사 체크리스트)
1. `~/.claude/skills/` 폴더 변경(추가/삭제/개명)이 있었는가?
2. 코어 계열 명칭 변경(예: `skill-create` → `skill-create-코어5`)이 있었는가?
3. 별칭 부여(예: `llm-dependent-agent-create` → `에신-llm-dependent-agent-create`)가 있었는가?
4. 신규 카테고리가 필요한 도메인 신설(예: Obsidian/MD, Vault 디렉터)이 있었는가?

→ 위 중 하나라도 해당하면 §1 카탈로그·계층별 수·총수를 즉시 갱신한다.

### 권장 운영
- mbo-천상이 호출될 때마다 §1 총수와 `~/.claude/skills/` 실측 폴더 수를 가볍게 대조 (실측이 다르면 PO에게 알림)
- 정기 audit: 월 1회 색인 정합성 점검
