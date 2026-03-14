---
name: doc-session-log
description: Session log (Q&A format). Use when user wants to record session conversation or daily summary
---

> 📖 **[사용자 가이드](references/USER_GUIDE.md)** - Quick Start, When to Use, Output 형식

# Session Log Skill

오늘 세션의 Q&A 내용을 기록합니다.

## 트리거

```
/doc-session-log
"세션 로그 작성해줘"
"오늘 대화 정리해줘"
```

---

## 출력물

| 파일 | 형식 | 규칙 |
|------|------|------|
| `docs/session-logs/YYYY-MM-DD.md` | Markdown | 같은 날짜 → append |

---

## 실행 지시

### Step 1: 대화 분석

```
추출 항목:
- Q&A 목록: 사용자 질문 + Claude 답변 (상세)
- Claude가 제안한 아키텍처, 다이어그램, 비교표
- 생성/수정된 파일 목록
- 결정된 사항

중요: Claude 답변 중 가치있는 설명은 그대로 보존
- ASCII 다이어그램
- 비교표/분석표
- 워크플로우 설명
- 구조 제안
```

### Step 2: 기존 파일 확인

```
1. docs/session-logs/YYYY-MM-DD.md 존재 여부 확인
2. 존재하면: 마지막 Q 번호 확인 후 이어서 append
3. 없으면: 새 파일 생성
```

### Step 3: 세션 로그 작성

```
추가할 내용:

### QN. {질문 제목}

**요청**: {사용자가 요청한 내용}

**Claude 답변**:
{Claude가 설명한 내용 - 가치있는 부분 그대로 보존}

예시:
- 아키텍처 다이어그램 (ASCII)
- 비교표
- 워크플로우 설명
- 구조 제안
- 핵심 개념 설명

**산출물**:
- {생성/수정된 파일 1}
- {생성/수정된 파일 2}

---
```

**기록 원칙**:
1. Claude 답변 중 **이해하기 좋은 설명**은 축약하지 말고 그대로 포함
2. 다이어그램, 표는 원본 유지
3. 단순 작업 결과만 있으면 짧게 기록

### Step 4: 산출물 테이블 업데이트

```
## 완료 산출물

| # | 산출물 | 위치 |
|---|--------|------|
| 1 | ... | ... |
```

### Step 5: 결과 출력

```
출력 형식:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📝 Session Log 업데이트 완료

파일: docs/session-logs/YYYY-MM-DD.md
추가된 Q&A: N개 (Q{시작} ~ Q{끝})
총 Q&A: M개

수정할 내용 있으시면 말씀해주세요.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 파일 구조

```markdown
# {프로젝트명} 세션 로그

**날짜**: YYYY-MM-DD
**세션**: N번째

---

## Q&A 로그

### Q1. {제목}

**요청**: 사용자 질문/요청 내용

**Claude 답변**:

{Claude의 설명 - 가치있는 내용 그대로 보존}

예시:
\`\`\`
세션 작업
    │
    ▼
doc-retrospective
    ├── doc-session-log
    ├── doc-handoff
    └── doc-lessons
\`\`\`

| 비교 항목 | A | B |
|----------|---|---|
| ... | ... | ... |

**산출물**:
- 파일1.md 생성
- 파일2.yaml 수정

---

### Q2. {제목}
...

---

## 완료 산출물

| # | 산출물 | 위치 |
|---|--------|------|

---

## 다음 작업 예정

- [ ] ...
```
