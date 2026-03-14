---
name: doc-handoff
description: AI Handoff document (YAML). Use when user says handoff, next session, or context transfer
---

> 📖 **[사용자 가이드](references/USER_GUIDE.md)** - Quick Start, When to Use, Output 형식

# Handoff Skill

다음 세션을 위한 AI 컨텍스트 전달 문서를 생성합니다.

## 트리거

```
/doc-handoff
"핸드오프 작성해줘"
"다음 세션 준비해줘"
```

---

## 출력물

| 파일 | 형식 | 규칙 |
|------|------|------|
| `docs/handoffs/YYYY-MM-DD.yaml` | YAML | 같은 날짜 → session 추가 |

---

## 실행 지시

### Step 1: 현재 상태 분석

```
추출 항목:
- 프로젝트 현재 상태
- 완료된 작업
- 다음 할 일
- 핵심 결정사항
- 주요 파일 위치
```

### Step 2: 기존 파일 확인

```
1. docs/handoffs/YYYY-MM-DD.yaml 존재 여부 확인
2. 존재하면: 마지막 session 번호 확인 후 session_N 추가
3. 없으면: 새 파일 생성 (session_1부터)
```

### Step 3: Handoff 작성

```yaml
# 새 세션 추가
session_N:
  time: "morning/afternoon/evening"
  summary: "한 줄 요약"
  completed:
    - "완료 작업 1"
    - "완료 작업 2"

# CURRENT STATE 항상 최신으로 업데이트
project:
  name: "프로젝트명"
  status: "현재 상태"

pending_tasks:
  high:
    - "우선순위 높은 작업"
  medium:
    - "중간 우선순위"

key_decisions:
  - decision: "결정 사항"
    reason: "이유"

key_files:
  - path: "파일 경로"
    purpose: "용도"

session_start_checklist:
  - question: "다음 세션 시작 시 확인할 질문"
    context: "맥락"
```

### Step 4: 결과 출력

```
출력 형식:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 Handoff 업데이트 완료

파일: docs/handoffs/YYYY-MM-DD.yaml
세션: session_N 추가
상태: {현재 상태 요약}

다음 세션 시작 시:
"handoff 읽고 이어서 작업해줘"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 파일 구조

```yaml
# Handoff Document
# Purpose: AI context recovery
# Date: YYYY-MM-DD
# Rule: Same date = append sessions

# ============================================================
# SESSION 1
# ============================================================
session_1:
  time: "morning"
  summary: "..."
  completed: [...]

# ============================================================
# SESSION 2
# ============================================================
session_2:
  time: "afternoon"
  summary: "..."
  completed: [...]

# ============================================================
# CURRENT STATE (항상 최신)
# ============================================================
project:
  name: "..."
  status: "..."

pending_tasks:
  high: [...]
  medium: [...]

key_decisions: [...]
key_files: [...]
session_start_checklist: [...]
```
