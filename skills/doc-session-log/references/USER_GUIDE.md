# doc-session-log

**Version**: 1.0
**Type**: Documentation
**Output**: Markdown
**Execution**: 2-3 minutes

---

## 🎯 Overview

오늘 세션의 Q&A 내용을 기록합니다.

### 효과
- ✅ Claude 답변 중 가치있는 설명 보존
- ✅ 아키텍처 다이어그램, 비교표 원본 유지
- ✅ 산출물 목록 자동 정리

---

## 🚀 Usage

### Quick Start
```
/doc-session-log
"세션 로그 작성해줘"
"오늘 대화 정리해줘"
```

Claude가 자동으로:
1. 대화 분석 (Q&A, 다이어그램, 산출물)
2. 기존 파일 확인 (같은 날짜 → append)
3. Markdown 형식으로 기록

---

## 📋 When to Use

다음 상황에서 이 스킬을 사용하세요:

1. **세션 마무리 시** - 대화 내용 보존
2. **중요한 설명을 받았을 때** - Claude 답변 기록
3. **산출물 정리가 필요할 때** - 생성된 파일 목록화

**빈도**: 매 세션 종료 시

---

## 📊 Output

### Primary Output
**File**: `docs/logs/SESSION_LOG_YYYYMMDD.md`

```markdown
# 프로젝트 세션 로그

**날짜**: 2026-01-07
**세션**: 1번째

---

## Q&A 로그

### Q1. 질문 제목

**요청**: 사용자 질문/요청 내용

**Claude 답변**:
{Claude의 설명 - 가치있는 내용 그대로 보존}

**산출물**:
- 파일1.md 생성
- 파일2.yaml 수정

---

## 완료 산출물

| # | 산출물 | 위치 |
|---|--------|------|
```

### Output Format
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📝 Session Log 업데이트 완료

파일: docs/logs/SESSION_LOG_YYYYMMDD.md
추가된 Q&A: N개 (Q{시작} ~ Q{끝})
총 Q&A: M개

수정할 내용 있으시면 말씀해주세요.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🔗 Related Skills

| 스킬 | 관계 |
|------|------|
| [doc-handoff](../../doc-handoff/references/USER_GUIDE.md) | AI 컨텍스트 전달 |
| [doc-lessons](../../doc-lessons/references/USER_GUIDE.md) | 배운 점 누적 |
| [doc-session-share](../../doc-session-share/references/USER_GUIDE.md) | 외부 공유용 정제 |
| [doc-retrospective](../../doc-retrospective/references/USER_GUIDE.md) | 3개 스킬 동시 호출 |
