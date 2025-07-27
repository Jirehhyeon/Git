# 🌿 Level 3: 분신술 마스터 - 브랜치와 대안 현실

## 🎯 목표
**브랜치(Branch)를 활용하여 여러 기능을 동시에 개발하고, 안전하게 실험하며, 체계적으로 병합할 수 있습니다.**

---

## 🔮 핵심 개념: 브랜치는 평행우주 창조술

### 브랜치를 이해하는 마법같은 비유: "평행우주 이론"

브랜치를 **평행우주**라고 생각해보세요!

```
      main (메인 우주)
       │
       │  A ── B ── C ── D
       │               │
       └─ E ── F ──────┘  (feature/new-power 우주)
          │
          └─ G ── H        (feature/experiment 우주)
```

- **main 브랜치**: 안정적인 "메인 우주" (항상 동작하는 코드)
- **feature 브랜치**: 실험적인 "평행우주" (새로운 기능 개발)
- **merge**: 평행우주의 성과를 메인우주로 가져오기
- **branch**: 새로운 평행우주 창조하기

### 🎯 왜 브랜치가 필요한가?

#### 브랜치 없이 개발하면:
```
😰 문제 상황:
- 새 기능 개발 중 버그 발생
- 기존 코드도 망가짐
- 되돌릴 방법 없음
- 팀원과 코드 충돌
```

#### 브랜치를 사용하면:
```
🎉 해결책:
- 안전한 실험 공간 확보
- 실패해도 main은 안전
- 여러 기능 동시 개발
- 체계적인 코드 통합
```

---

## 🛠️ 브랜치 기본 명령어

### 1. 브랜치 조회
```bash
# 로컬 브랜치 목록 보기
git branch

# 원격 브랜치까지 모두 보기
git branch -a

# 현재 브랜치 확인 (*)
git branch
```

### 2. 브랜치 생성
```bash
# 새 브랜치 생성 (현재 위치에서)
git branch 브랜치명

# 예시
git branch feature/add-mbti
git branch hotfix/urgent-bug
git branch develop
```

### 3. 브랜치 전환
```bash
# 브랜치로 이동
git checkout 브랜치명

# 브랜치 생성과 동시에 이동 (가장 많이 사용!)
git checkout -b 브랜치명

# 예시
git checkout -b feature/add-dream
```

### 4. 브랜치 병합
```bash
# main 브랜치로 이동
git checkout main

# feature 브랜치를 main에 병합
git merge feature/브랜치명

# 예시
git merge feature/add-mbti
```

### 5. 브랜치 삭제
```bash
# 로컬 브랜치 삭제 (병합 완료된 것만)
git branch -d 브랜치명

# 강제 삭제 (병합되지 않아도)
git branch -D 브랜치명

# 원격 브랜치 삭제
git push origin --delete 브랜치명
```

---

## 🎭 브랜치 네이밍 컨벤션

### 🏷️ 브랜치명 규칙 (업계 표준)

```bash
feature/기능명     # 새로운 기능 개발
├── feature/user-login
├── feature/shopping-cart
└── feature/payment-system

bugfix/버그명      # 버그 수정
├── bugfix/login-error
└── bugfix/memory-leak

hotfix/긴급수정    # 운영 환경 긴급 수정
├── hotfix/security-patch
└── hotfix/critical-bug

release/버전       # 릴리즈 준비
├── release/v1.0.0
└── release/v2.1.0

develop           # 개발 통합 브랜치
main             # 운영/배포 브랜치
```

### 🎯 네이밍 원칙
- **소문자 + 하이픈**: `feature/user-profile`
- **의미 명확**: `feature/add-payment` (O) vs `feature/temp` (X)
- **영어 사용**: 국제적 협업 고려

---

## 🎮 실습 과제: MBTI 추가 브랜치 워크플로우

### 📋 과제 시나리오
자기소개 파일에 MBTI 정보를 추가하되, **별도 브랜치에서 작업 후 main에 병합**하겠습니다.

### 🔄 실습 순서

#### Step 1: 현재 상태 확인
```bash
# 현재 브랜치 확인
git branch

# 작업 디렉토리 상태 확인
git status
```

#### Step 2: feature 브랜치 생성 및 전환
```bash
# 새 브랜치 생성과 동시에 전환
git checkout -b feature/add-mbti

# 브랜치 전환 확인
git branch
```

#### Step 3: feature 브랜치에서 작업
```bash
# 자기소개 파일에 MBTI 추가
echo "MBTI: ENFP (브랜치에서 추가됨)" >> 자기소개.txt

# 변경사항 확인
cat 자기소개.txt

# 커밋
git add 자기소개.txt
git commit -m "feature: MBTI 정보 추가

- 자기소개.txt에 MBTI(ENFP) 정보 추가
- feature/add-mbti 브랜치에서 작업
- 성격 정보 섹션 확장

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>"
```

#### Step 4: main 브랜치로 전환 및 병합
```bash
# main 브랜치로 전환
git checkout main

# 자기소개 파일 확인 (MBTI가 없어야 정상)
cat 자기소개.txt

# feature 브랜치 병합
git merge feature/add-mbti

# 병합 후 파일 확인 (MBTI가 추가되어야 함)
cat 자기소개.txt
```

#### Step 5: 정리 및 GitHub 업로드
```bash
# 사용 완료된 브랜치 삭제
git branch -d feature/add-mbti

# GitHub에 업로드
git push origin main

# 전체 브랜치 상태 확인
git branch -a
```

---

## 🎯 고급 실습: 동시 개발 시나리오

### 📋 시나리오: "꿈과 목표를 동시에 개발"

#### 상황 설정
- 브랜치 A: 장래희망 추가
- 브랜치 B: 목표 추가  
- 두 브랜치를 순차적으로 main에 병합

#### 실습 과정

##### Phase 1: 장래희망 브랜치
```bash
# 1. 장래희망 브랜치 생성
git checkout -b feature/add-dream

# 2. 장래희망 추가
echo "장래희망: 풀스택 개발자" >> 자기소개.txt

# 3. 커밋
git add 자기소개.txt
git commit -m "feature: 장래희망 정보 추가"

# 4. GitHub에 브랜치 업로드
git push origin feature/add-dream
```

##### Phase 2: 목표 브랜치 (동시 개발)
```bash
# 1. main에서 새 브랜치 생성
git checkout main
git checkout -b feature/add-goals

# 2. 목표 추가
echo "2025년 목표: Git 마스터, React 완주" >> 자기소개.txt

# 3. 커밋
git add 자기소개.txt
git commit -m "feature: 2025년 목표 추가"

# 4. GitHub에 브랜치 업로드
git push origin feature/add-goals
```

##### Phase 3: 순차적 병합
```bash
# 1. main으로 이동
git checkout main

# 2. 장래희망 브랜치 먼저 병합
git merge feature/add-dream

# 3. 목표 브랜치 병합 
git merge feature/add-goals

# 4. 최종 결과 확인
cat 자기소개.txt

# 5. GitHub 업로드
git push origin main

# 6. 브랜치 정리
git branch -d feature/add-dream
git branch -d feature/add-goals
git push origin --delete feature/add-dream
git push origin --delete feature/add-goals
```

---

## 🚨 브랜치 충돌 해결하기

### 🔥 충돌(Conflict) 시나리오 체험

#### 의도적으로 충돌 만들기
```bash
# 1. 브랜치 A 생성
git checkout -b conflict-test-a
echo "좋아하는 색깔: 파란색" >> 자기소개.txt
git add . && git commit -m "파란색 추가"

# 2. main에서 브랜치 B 생성
git checkout main
git checkout -b conflict-test-b
echo "좋아하는 색깔: 빨간색" >> 자기소개.txt
git add . && git commit -m "빨간색 추가"

# 3. main에 A 브랜치 병합
git checkout main
git merge conflict-test-a

# 4. B 브랜치 병합 시도 (충돌 발생!)
git merge conflict-test-b
```

#### 충돌 해결 과정
```bash
# 1. 충돌 파일 확인
git status

# 2. 충돌 파일 열어서 수동 편집
# <<<<<<< HEAD
# 좋아하는 색깔: 파란색
# =======
# 좋아하는 색깔: 빨간색
# >>>>>>> conflict-test-b

# 3. 원하는 대로 수정 후 저장
# 예: "좋아하는 색깔: 파란색과 빨간색"

# 4. 충돌 해결 완료 표시
git add 자기소개.txt
git commit -m "충돌 해결: 두 색깔 모두 선택"
```

---

## 📊 브랜치 시각화 도구

### 명령어로 브랜치 그래프 보기
```bash
# 예쁜 브랜치 그래프
git log --graph --oneline --all

# 더 자세한 그래프
git log --graph --pretty=format:'%h -%d %s (%cr) <%an>' --abbrev-commit --all
```

### GUI 도구 추천
- **VS Code**: Git Graph 확장
- **GitKraken**: 시각적 Git 클라이언트
- **SourceTree**: Atlassian의 무료 Git GUI

---

## 🎉 실습 완료 체크리스트

### 기본 브랜치 작업
- [ ] `git branch`로 브랜치 목록 확인
- [ ] `git checkout -b feature/add-mbti` 브랜치 생성
- [ ] feature 브랜치에서 MBTI 정보 추가
- [ ] `git merge`로 main에 병합
- [ ] `git branch -d`로 브랜치 삭제

### 고급 브랜치 작업
- [ ] 동시에 2개 브랜치 생성 (dream, goals)
- [ ] 각 브랜치에서 다른 내용 추가
- [ ] 순차적으로 main에 병합
- [ ] GitHub에 브랜치 push/delete

### 충돌 해결
- [ ] 의도적으로 충돌 상황 생성
- [ ] 충돌 파일 수동 편집
- [ ] 충돌 해결 후 커밋

---

## 💡 브랜치 전략: Git Flow 맛보기

### 🌊 Git Flow 브랜치 전략
```
main ────────────────────────── (항상 배포 가능)
  │
develop ─────────────────────── (개발 통합)
  │        │              │
  │    feature/A     feature/B  (기능 개발)
  │        │              │
  └── release/v1.0 ─────────── (릴리즈 준비)
           │
      hotfix/urgent ──────────── (긴급 수정)
```

### 🎯 각 브랜치의 역할
- **main**: 운영 환경, 항상 안정적
- **develop**: 개발 통합, 다음 릴리즈 준비
- **feature/**: 새 기능 개발
- **release/**: 릴리즈 준비 및 테스트
- **hotfix/**: 운영 환경 긴급 수정

---

## 🎯 다음 레벨 예고: Level 4

다음 레벨에서는 **Pull Request**를 통해:
- 🔍 코드 리뷰를 주고받고
- 💬 팀원과 소통하며
- 🚀 체계적으로 협업하는 현대적인 개발 워크플로우를 배웁니다!

---

## 📝 Level 3 핵심 요약

| 개념 | 명령어 | 의미 |
|------|--------|------|
| 브랜치 생성 | `git checkout -b 브랜치명` | 새 브랜치 만들고 이동 |
| 브랜치 전환 | `git checkout 브랜치명` | 다른 브랜치로 이동 |
| 브랜치 병합 | `git merge 브랜치명` | 다른 브랜치를 현재 브랜치에 합치기 |
| 브랜치 삭제 | `git branch -d 브랜치명` | 완료된 브랜치 정리 |
| 브랜치 확인 | `git branch` | 모든 브랜치 목록 보기 |

**🎉 축하합니다! 이제 브랜치를 자유자재로 다루는 Git 마법사가 되었습니다!**