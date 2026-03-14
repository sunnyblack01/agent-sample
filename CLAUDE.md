# 수행평가 보고서 멀티 에이전트 시스템

## 프로젝트 목적
고등학생의 수행평가 보고서 작성을 7개의 전문 에이전트로 지원한다.
모든 보고서는 AI/인공지능 진로와 자연스럽게 연결되어야 한다.

## 에이전트 구성
| 에이전트 | 파일 | 역할 |
|----------|------|------|
| Orchestrator | agents/00_orchestrator.md | 전체 워크플로우 관리 |
| Topic Scout | agents/01_topic_scout.md | 주제 발굴 |
| Research Agent | agents/02_research_agent.md | 자료 조사 |
| Experiment Designer | agents/03_experiment_designer.md | 실험 설계 |
| Report Writer | agents/04_report_writer.md | 보고서 작성 |
| Voice Coach | agents/05_voice_coach.md | AI스러움 제거 검토 |
| Topic Advisor | agents/06_topic_advisor.md | 주제 심화 토론 (난이도·임팩트 조율) |
| Interview Prep | agents/07_interview_prep.md | 면접 준비 (예상 질문·답변 전략) |

## 사용법
1. 과목 + 범위 + 실험 여부를 알려주면 오케스트레이터가 순서대로 진행
2. "보고서 시작: 화학, 1학기, 실험 있음" 형태로 요청
3. 각 단계마다 학생 확인 후 다음 단계 진행

## 핵심 규칙
- AI가 쓴 티가 나면 안 됨 → Voice Coach가 최종 검토
- 과목 교육과정 범위를 벗어나지 않을 것
- AI 진로 연결은 자연스럽게 (억지 금지)
- 참고 문헌은 실제 존재하는 것만

## 파일 구조
```
agent sample/
├── CLAUDE.md              # 이 파일
├── config/
│   └── profile.yaml       # 학생 프로필 및 설정
├── agents/
│   ├── 00_orchestrator.md  # 오케스트레이터
│   ├── 01_topic_scout.md   # 주제 발굴
│   ├── 02_research_agent.md # 자료 조사
│   ├── 03_experiment_designer.md # 실험 설계
│   ├── 04_report_writer.md # 보고서 작성
│   ├── 05_voice_coach.md   # 어투 코치
│   ├── 06_topic_advisor.md  # 주제 심화 토론
│   └── 07_interview_prep.md # 면접 준비
├── templates/
│   └── report_template.md  # 보고서 템플릿
└── reports/
    └── keyword_tracker.yaml # AI 키워드 추적
```
