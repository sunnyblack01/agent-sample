# doc-handoff

**Version**: 1.0
**Type**: Documentation
**Output**: YAML
**Execution**: 1-2 minutes

---

## 🎯 Overview

다음 세션을 위한 AI 컨텍스트 전달 문서를 생성합니다.

### 효과
- ✅ 세션 간 컨텍스트 100% 유지
- ✅ "handoff 읽고 이어서" 한 마디로 복구
- ✅ 같은 날 여러 세션 → 자동 session_N 추가

---

## 🚀 Usage

### Quick Start
```
/doc-handoff
"핸드오프 작성해줘"
"다음 세션 준비해줘"
```

Claude가 자동으로:
1. 현재 세션 분석 (완료 작업, 결정사항, 다음 할 일)
2. 기존 handoff 파일 확인
3. YAML 형식으로 생성/업데이트

### 다음 세션 시작 시
```
"handoff 읽고 이어서 작업해줘"
```

---

## 📋 When to Use

다음 상황에서 이 스킬을 사용하세요:

1. **세션 마무리 시** - 작업 내용 저장
2. **다음 날 이어서 할 때** - 컨텍스트 전달
3. **긴 작업 중간 저장** - 진행 상황 기록

**빈도**: 매 세션 종료 시

---

## 📊 Output

### Primary Output
**File**: `docs/handoff/HANDOFF_YYYYMMDD.yaml`

```yaml
session_1:
  time: "morning"
  summary: "한 줄 요약"
  completed:
    - "완료 작업 1"
    - "완료 작업 2"

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
```

### Output Format
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 Handoff 업데이트 완료

파일: docs/handoff/HANDOFF_YYYYMMDD.yaml
세션: session_N 추가
상태: {현재 상태 요약}

다음 세션 시작 시:
"handoff 읽고 이어서 작업해줘"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🔗 Related Skills

| 스킬 | 관계 |
|------|------|
| [doc-session-log](../../doc-session-log/references/USER_GUIDE.md) | 상세 Q&A 기록 (사람용) |
| [doc-lessons](../../doc-lessons/references/USER_GUIDE.md) | 배운 점 누적 |
| [doc-retrospective](../../doc-retrospective/references/USER_GUIDE.md) | 3개 스킬 동시 호출 |
