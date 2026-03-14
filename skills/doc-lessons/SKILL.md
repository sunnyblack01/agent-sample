---
name: doc-lessons
description: Lessons learned log. Use when user wants to record learnings, mistakes, or improvements
---

> 📖 **[사용자 가이드](references/USER_GUIDE.md)** - Quick Start, When to Use, Output 형식

# Lessons Skill

세션에서 배운 점을 누적 기록합니다.

## 트리거

```
/doc-lessons
"배운 점 기록해줘"
"레슨런드 추가해줘"
```

---

## 출력물

| 파일 | 형식 | 규칙 |
|------|------|------|
| `docs/lessons/LESSONS_LEARNED_YYYYMMDD.md` | Markdown | 같은 날짜 → append |

---

## 실행 지시

### Step 1: 학습 내용 분석

```
추출 항목:
- 배운 점: 새로 알게 된 것
- 실수 → 수정: 잘못한 것과 어떻게 고쳤는지
- 인사이트: Agent 설계, 워크플로우, 도구 활용 등
```

### Step 2: 기존 파일 확인

```
1. docs/lessons/LESSONS_LEARNED_YYYYMMDD.md 존재 여부 확인
2. 존재하면: 파일 끝에 append
3. 없으면: 새 파일 생성 (템플릿 포함)
```

### Step 3: Lessons Learned 추가

```markdown
---

## YYYY-MM-DD Session N

### 배운 점
| # | Lesson | 상황 | 적용 |
|---|--------|------|------|
| 1 | {배운 점} | {어떤 상황에서} | {향후 어떻게 적용} |

### 실수 → 수정
| 실수 | 원인 | 수정 |
|------|------|------|
| {실수 내용} | {왜 발생} | {어떻게 고침} |

### 인사이트
| 카테고리 | 인사이트 | 향후 적용 |
|----------|----------|----------|
| Agent 설계 | {인사이트} | {적용 방법} |
```

### Step 4: 카테고리 인덱스 업데이트

```
파일 상단의 카테고리별 인덱스에 새 항목 추가:

### Agent 설계
- [YYYY-MM-DD] {요약}

### 워크플로우
- [YYYY-MM-DD] {요약}
```

### Step 5: 결과 출력

```
출력 형식:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
💡 Lessons Learned 업데이트 완료

파일: docs/lessons/LESSONS_LEARNED_YYYYMMDD.md
추가된 교훈: N개
카테고리: {업데이트된 카테고리}

총 누적 교훈: M개
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 파일 구조

```markdown
# {프로젝트명} - Lessons Learned

프로젝트 진행 중 배운 점들을 누적 기록합니다.

---

## 카테고리별 인덱스

### Agent 설계
- [YYYY-MM-DD] ...

### 워크플로우
- [YYYY-MM-DD] ...

### 도구 활용
- [YYYY-MM-DD] ...

### 프롬프트 엔지니어링
- [YYYY-MM-DD] ...

---

## 세션별 기록

## YYYY-MM-DD Session 1

### 배운 점
| # | Lesson | 상황 | 적용 |
|---|--------|------|------|

### 실수 → 수정
| 실수 | 원인 | 수정 |
|------|------|------|

---
```
