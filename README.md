# 수행평가 보고서 멀티에이전트 시스템

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![Status](https://img.shields.io/badge/status-Active-brightgreen)
![Agents](https://img.shields.io/badge/agents-7-orange)

**Version**: 1.0.0
**Date**: 2026-03-14
**Status**: ✅ Active
**Platform**: Claude Code CLI

---

## 목차

1. [Executive Summary](#1-executive-summary)
2. [Core Constraints (절대 규칙)](#2-core-constraints-절대-규칙)
3. [Agent Architecture](#3-agent-architecture)
4. [Execution Flow](#4-execution-flow)
5. [Project Structure](#5-project-structure)
6. [Quick Start](#6-quick-start)
7. [Student Profile](#7-student-profile)
8. [Current Progress](#8-current-progress)
9. [Contributing](#9-contributing)
10. [문서 참조](#10-문서-참조)

---

## 1. Executive Summary

고등학생의 수행평가 보고서 작성을 **7개 전문 에이전트**가 협업하여 지원하는 Multi-Agent System.
주제 발굴 → 자료 조사 → 실험 설계 → 보고서 작성 → 검토까지 전 프로세스를 자동화하되, **학생 본인의 사고와 어투가 반드시 살아있는** 보고서를 생산한다.

| 항목 | 수치 |
|------|------|
| 전체 Agent 수 | 7개 (Orchestrator 포함) |
| 지원 워크플로우 | 3종 (실험 포함 / 미포함 / 주제 고민) |
| 핵심 제약 조건 | 4개 (Anti-AI, Curriculum, Career, Source) |
| 문서 수 | 4개 (PRD, Agent Plan, I/O Pipeline, Hands-on Guide) |

---

## 2. Core Constraints (절대 규칙)

| # | 제약 | 설명 | 중요도 |
|---|------|------|--------|
| C1 | Anti-AI Detection | AI가 작성한 티가 나면 안 됨 (Voice Coach가 최종 검증) | ⛔ 필수 |
| C2 | Curriculum Scope | 해당 과목 교육과정 범위 내에서만 주제 선정 | ⛔ 필수 |
| C3 | Career Alignment | AI/인공지능 진로와 자연스러운 연결 (억지 금지) | ⛔ 필수 |
| C4 | Source Integrity | 참고 문헌은 실제 존재하는 것만 (WebSearch 검증) | ⛔ 필수 |

---

## 3. Agent Architecture

### 3.1 시스템 구조도

```
┌─────────────────────────────────────────────────────┐
│                  00_ORCHESTRATOR                     │
│              (전체 워크플로우 관리)                    │
└─────┬───────┬───────┬───────┬───────┬───────┬───────┘
      │       │       │       │       │       │
      ▼       ▼       ▼       ▼       ▼       ▼
   ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐
   │ 01  │ │ 02  │ │ 03  │ │ 04  │ │ 05  │ │ 06  │
   │Topic│ │Rsrch│ │Expr │ │Rprt │ │Voice│ │Topic│
   │Scout│ │Agent│ │Dsgn │ │Wrtr │ │Coach│ │Advsr│
   └─────┘ └─────┘ └─────┘ └─────┘ └─────┘ └─────┘
                                              │
                                           ┌─────┐
                                           │ 07  │
                                           │Intv │
                                           │Prep │
                                           └─────┘
```

### 3.2 Agent 상세 테이블

| # | Agent | 유형 | 정의 파일 | 역할 | Input | Output |
|---|-------|------|-----------|------|-------|--------|
| 00 | **Orchestrator** | Controller | `agents/00_orchestrator.md` | 워크플로우 관리, 단계 전환, 품질 관리 | 학생 요청 | 각 Agent 호출 |
| 01 | **Topic Scout** | Generator | `agents/01_topic_scout.md` | 과목 범위 내 AI 진로 연결 가능 주제 발굴 | 과목, 범위, 실험여부 | 주제 후보 5개+ |
| 02 | **Research Agent** | Researcher | `agents/02_research_agent.md` | 참고문헌, 도서, 논문, AI 자료 조사 | 선택 주제 | 이론+문헌 목록 |
| 03 | **Experiment Designer** | Designer | `agents/03_experiment_designer.md` | 가설, 변인, 절차, 예측-검증 설계 | 주제, 이론 | 실험 설계서 |
| 04 | **Report Writer** | Writer | `agents/04_report_writer.md` | 전체 자료 종합 → 보고서 뼈대 작성 | 전체 자료 | 보고서 초안 |
| 05 | **Voice Coach** | Validator | `agents/05_voice_coach.md` | AI스러움 검토, 수정 방향 제시 | 보고서 초안 | 검토 리포트 |
| 06 | **Topic Advisor** | Evaluator | `agents/06_topic_advisor.md` | 주제 난이도/임팩트/실현가능성 다면 평가 | 주제 후보, 학생 피드백 | 평가표+추천 |
| 07 | **Interview Prep** | Coach | `agents/07_interview_prep.md` | 면접 예상 질문, 답변 전략, 시뮬레이션 | 보고서, 프로그램 정보 | 면접 가이드 |

---

## 4. Execution Flow

### 4.1 실험 포함 보고서

```
Student ──→ [01 Topic Scout] ──→ Student 선택
                                     │
                                     ▼
                              [02 Research Agent]
                                     │
                                     ▼
                              [03 Experiment Designer]
                                     │
                                     ▼
                              Student 실험 수행 → 결과 입력
                                     │
                                     ▼
                              [04 Report Writer]
                                     │
                                     ▼
                              [05 Voice Coach]
                                     │
                                     ▼
                              Student 최종 다듬기
                                     │
                                     ▼
                              (Optional) [07 Interview Prep]
```

### 4.2 실험 미포함 보고서

```
Student → [01] → Student 선택 → [02] → [04] → [05] → Student 다듬기
```

### 4.3 주제 고민 시

```
[01 Topic Scout] → [06 Topic Advisor] → Student 최종 선택
```

---

## 5. Project Structure

```
agent-sample/
├── CLAUDE.md                              # Claude Code 프로젝트 설정
├── README.md                              # 이 문서
├── config/
│   └── profile.yaml                       # 학생 프로필 + 과목별 범위
├── agents/
│   ├── 00_orchestrator.md                 # Orchestrator
│   ├── 01_topic_scout.md                  # Topic Scout
│   ├── 02_research_agent.md               # Research Agent
│   ├── 03_experiment_designer.md          # Experiment Designer
│   ├── 04_report_writer.md                # Report Writer
│   ├── 05_voice_coach.md                  # Voice Coach
│   ├── 06_topic_advisor.md                # Topic Advisor
│   └── 07_interview_prep.md               # Interview Prep
├── docs/
│   ├── AGENT_PLAN.md                      # Agent 설계 문서
│   ├── IO_PIPELINE.md                     # I/O 데이터 흐름
│   ├── PRD.md                             # 제품 요구사항
│   └── HANDS_ON_GUIDE.md                  # 사용 가이드 (환경 설정 포함)
├── templates/
│   └── report_template.md                 # 보고서 템플릿
└── reports/
    ├── keyword_tracker.yaml               # AI 키워드 추적 (과목 간 일관성)
    └── chemistry_clock_reaction/          # 🚧 시계반응 보고서
        ├── research.md                    # 자료 조사 결과
        ├── experiment_design.md           # 실험 설계서
        ├── report_draft.md                # 보고서 초안
        ├── voice_coach_review.md          # 어투 검토 결과
        └── interview_prep.md              # 면접 준비 가이드
```

---

## 6. Quick Start

### 6.1 환경 설정

> 상세한 설치 가이드는 [docs/HANDS_ON_GUIDE.md](docs/HANDS_ON_GUIDE.md) 참고

1. VS Code 설치
2. Claude Code (CLI) 설치
3. 이 리포지토리 clone
4. `config/profile.yaml`에 본인 정보 입력

### 6.2 사용법

```
보고서 시작: {과목}, {범위}, {실험여부}
```

**예시:**
```
보고서 시작: 화학, 1학기 결합 단원, 실험 있음
```

---

## 7. Student Profile

| 항목 | 내용 |
|------|------|
| 학년 | 고2 |
| 진로 | AI/인공지능 학과 |
| 핵심 키워드 | 데이터 기반 문제 해결, 패턴 인식, 예측, 분류, 최적화 |
| 연결 전략 | 모든 과목에서 AI적 사고방식(데이터 수집 → 패턴 발견 → 예측/분류)을 일관되게 |

상세 설정: `config/profile.yaml`

---

## 8. Current Progress

| 과목 | 주제 | 유형 | 마감 | 상태 |
|------|------|------|------|------|
| 화학 (실험 프로그램) | 시계반응 반응 속도 예측 모델 | 프로그램 지원 + 면접 | 3/20 | 🚧 보고서 초안 완료 |

---

## 9. Contributing

`config/profile.yaml`에 과목별 단원 범위를 업데이트하면 새로운 과목에 바로 적용 가능합니다.

---

## 10. 문서 참조

| 문서 | 경로 | 설명 |
|------|------|------|
| 제품 요구사항 (PRD) | [docs/PRD.md](docs/PRD.md) | 시스템 목적, 범위, 요구사항 정의 |
| Agent 설계 문서 | [docs/AGENT_PLAN.md](docs/AGENT_PLAN.md) | 에이전트별 상세 설계 및 역할 정의 |
| I/O Pipeline | [docs/IO_PIPELINE.md](docs/IO_PIPELINE.md) | 에이전트 간 데이터 흐름 및 인터페이스 |
| 사용 가이드 | [docs/HANDS_ON_GUIDE.md](docs/HANDS_ON_GUIDE.md) | 환경 설정부터 실행까지 단계별 안내 |

---

*v1.0.0 | 2026-03-14*
