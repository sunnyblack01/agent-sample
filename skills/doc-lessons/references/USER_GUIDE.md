# doc-lessons

**Version**: 1.0
**Type**: Documentation
**Output**: Markdown
**Execution**: 1-2 minutes

---

## 🎯 Overview

세션에서 배운 점을 누적 기록합니다.

### 효과
- ✅ 배운 점 날짜별 누적 관리
- ✅ 실수 → 수정 패턴 기록
- ✅ 카테고리별 인덱스 자동 생성

---

## 🚀 Usage

### Quick Start
```
/doc-lessons
"배운 점 기록해줘"
"레슨런드 추가해줘"
```

Claude가 자동으로:
1. 세션에서 배운 점 분석
2. 기존 파일 확인 (있으면 append)
3. 카테고리별 인덱스 업데이트

---

## 📋 When to Use

다음 상황에서 이 스킬을 사용하세요:

1. **새로운 것을 배웠을 때** - 기술, 도구, 방법론
2. **실수를 수정했을 때** - 원인과 해결책 기록
3. **인사이트를 얻었을 때** - Agent 설계, 워크플로우

**빈도**: 매 세션 종료 시 또는 중요한 학습 후

---

## 📊 Output

### Primary Output
**File**: `docs/lessons/LESSONS_LEARNED_YYYYMMDD.md`

```markdown
## 2026-01-07 Session 1

### 배운 점
| # | Lesson | 상황 | 적용 |
|---|--------|------|------|
| 1 | 배운 점 | 어떤 상황에서 | 향후 어떻게 적용 |

### 실수 → 수정
| 실수 | 원인 | 수정 |
|------|------|------|
| 실수 내용 | 왜 발생 | 어떻게 고침 |

### 인사이트
| 카테고리 | 인사이트 | 향후 적용 |
|----------|----------|----------|
| Agent 설계 | 인사이트 | 적용 방법 |
```

### Output Format
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
💡 Lessons Learned 업데이트 완료

파일: docs/lessons/LESSONS_LEARNED_YYYYMMDD.md
추가된 교훈: N개
카테고리: {업데이트된 카테고리}

총 누적 교훈: M개
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🔗 Related Skills

| 스킬 | 관계 |
|------|------|
| [doc-handoff](../../doc-handoff/references/USER_GUIDE.md) | AI 컨텍스트 전달 |
| [doc-session-log](../../doc-session-log/references/USER_GUIDE.md) | 상세 Q&A 기록 |
| [doc-retrospective](../../doc-retrospective/references/USER_GUIDE.md) | 3개 스킬 동시 호출 |
| [doc-project-lessons](../../doc-project-lessons/references/USER_GUIDE.md) | 프로젝트 완료 시 종합 |
