# ⚡ Level 5: 역사를 편집하는 시간 여행자 - Rebase와 고급 Git 기술

## 🎯 목표
**Git의 고급 기능들을 마스터하여 프로 개발자처럼 깔끔한 커밋 히스토리를 관리하고, 복잡한 상황들을 효율적으로 해결합니다.**

---

## 🔍 핵심 개념: Rebase는 역사를 편집하는 시간 여행

### Rebase를 이해하는 현실적인 비유: "역사책 편집자"

Rebase를 **역사책을 깔끔하게 편집하는 편집자**라고 생각해보세요!

```
원본 역사 (지저분):
🎭 연극 연습 → 🍕 점심 → 🎭 연극 완성 → 🐛 오타 수정 → 🎭 최종 완성

편집된 역사 (깔끔):
🎭 연극 기획 → 🎭 연극 구현 → 🎭 연극 완성

편집자(Rebase)의 역할:
- 불필요한 중간 과정들 정리
- 논리적 순서로 재배열
- 의미있는 단위로 묶기
- 깔끔한 스토리라인 구성
```

### 🎯 Rebase vs Merge 차이점

#### Merge 방식 (전통적):
```
main     ●───●───●───●───● (히스토리가 복잡)
          \       \     /
feature    ●───●───●───●
             분기점이 그대로 남음
```

#### Rebase 방식 (깔끔):
```
main     ●───●───●───●───●───●───● (일직선)
                    feature 커밋들이 
                    main 끝에 깔끔하게 정렬
```

---

## 🔧 Interactive Rebase: 커밋 히스토리 편집 도구

### 🎨 Interactive Rebase의 마법 같은 기능들

#### 1. 커밋 메시지 수정 (reword)
```bash
# 최근 3개 커밋을 편집 모드로 열기
git rebase -i HEAD~3

# 에디터에서 나타나는 화면:
pick 1234567 첫 번째 커밋
pick 2345678 두 번째 커밋
pick 3456789 세 번째 커밋

# 'pick'을 'reword'로 변경하면 메시지 수정 가능
reword 1234567 첫 번째 커밋
pick 2345678 두 번째 커밋
pick 3456789 세 번째 커밋
```

#### 2. 커밋 합치기 (squash)
```bash
# 여러 작은 커밋들을 하나로 합치기
pick 1234567 기능 추가 시작
squash 2345678 오타 수정
squash 3456789 스타일 정리
squash 4567890 최종 완성

# 결과: 4개 커밋이 하나의 깔끔한 커밋으로 합쳐짐
```

#### 3. 커밋 삭제 (drop)
```bash
# 불필요한 커밋 제거
pick 1234567 중요한 기능 추가
drop 2345678 실수로 만든 임시 커밋
pick 3456789 또 다른 중요한 기능
```

#### 4. 커밋 순서 변경
```bash
# 커밋 순서를 논리적으로 재배열
pick 3456789 기초 설정
pick 1234567 핵심 기능 구현
pick 2345678 UI 개선
```

---

## 🎮 실습 과제: 지저분한 히스토리 정리하기

### 📋 시나리오: "급하게 작업한 기술 스택 추가를 깔끔하게 정리"

#### Step 1: 의도적으로 지저분한 커밋들 만들기
```bash
# 새 브랜치 생성
git checkout -b feature/tech-stack-messy

# 첫 번째 작업 - 기술 스택 섹션 추가
echo "" >> 자기소개.txt
echo "=== 기술 스택 ===" >> 자기소개.txt

git add 자기소개.txt
git commit -m "기술 스택 섹션 추가"

# 두 번째 작업 - 오타 있는 내용 추가
echo "Frontend: HTML, CSS, JavaScrip" >> 자기소개.txt

git add 자기소개.txt
git commit -m "프론트엔드 기술 추가"

# 세 번째 작업 - 오타 수정
sed -i 's/JavaScrip/JavaScript/' 자기소개.txt

git add 자기소개.txt
git commit -m "오타 수정"

# 네 번째 작업 - 백엔드 추가
echo "Backend: Python" >> 자기소개.txt

git add 자기소개.txt
git commit -m "백엔드 기술 추가"

# 다섯 번째 작업 - 또 다른 기술들 추가
echo "Systems: C++" >> 자기소개.txt
echo "Tools: Git, Arduino, VSCode" >> 자기소개.txt

git add 자기소개.txt
git commit -m "시스템 프로그래밍과 도구들 추가"

# 현재 히스토리 확인
git log --oneline
```

#### Step 2: Interactive Rebase로 히스토리 정리
```bash
# 최근 5개 커밋을 정리
git rebase -i HEAD~5

# 에디터에서 다음과 같이 편집:
pick [hash] 기술 스택 섹션 추가
squash [hash] 프론트엔드 기술 추가
squash [hash] 오타 수정
squash [hash] 백엔드 기술 추가
squash [hash] 시스템 프로그래밍과 도구들 추가

# 커밋 메시지 편집 화면에서 다음과 같이 정리:
```

```markdown
feat: 기술 스택 섹션 추가

포트폴리오 강화를 위한 기술 역량 정보 추가:
- Frontend: HTML, CSS, JavaScript
- Backend: Python  
- Systems: C++
- Tools: Git, Arduino, VSCode

구현 내용:
- 명확한 카테고리별 분류로 가독성 향상
- 다양한 기술 영역의 경험 어필
- 체계적인 기술 스택 문서화

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

#### Step 3: 결과 확인 및 메인으로 병합
```bash
# 깔끔해진 히스토리 확인
git log --oneline

# main으로 전환 후 깔끔하게 병합
git checkout main
git merge feature/tech-stack-messy

# 브랜치 정리
git branch -d feature/tech-stack-messy
```

---

## 🚨 Git Stash: 응급 상황 대처법

### 💡 Stash 개념: "임시 서랍"

Git Stash는 **작업 중인 내용을 임시로 안전한 곳에 보관하는 서랍**입니다.

```
일상 시나리오:
🔥 갑작스러운 응급 버그 신고!
📝 하지만 현재 작업 중인 기능이 절반만 완성됨
😰 커밋하기엔 애매하고, 버리기엔 아까움

🎯 해결책: Stash 사용!
```

### 🎮 실습: 응급 상황 시뮬레이션

#### Step 1: 작업 중인 상황 만들기
```bash
# 새로운 기능 작업 시작
git checkout -b feature/new-goals

# 2025년 목표 추가 (아직 미완성)
echo "2025년 목표: Git 마스터, React 완주" >> 자기소개.txt

# 작업 상태 확인
git status
```

#### Step 2: 응급 상황 발생!
```bash
# 현재 작업을 stash에 보관
git stash push -m "2025년 목표 추가 작업 중"

# stash 목록 확인
git stash list

# 깨끗한 상태 확인
git status
```

#### Step 3: 응급 수정 처리
```bash
# main 브랜치로 이동해서 응급 수정
git checkout main

# 응급 수정 (예: 오타 수정)
sed -i 's/25세/25살/' 자기소개.txt

git add 자기소개.txt
git commit -m "hotfix: 나이 표기 방식 통일

긴급 수정 사항:
- '25세'를 '25살'로 표기 방식 통일
- 전체 문서의 일관성 향상

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>"
```

#### Step 4: 원래 작업으로 복귀
```bash
# 원래 브랜치로 돌아가기
git checkout feature/new-goals

# stash에서 작업 내용 복원
git stash pop

# 작업 계속 진행
echo "취미: 프로그래밍, 기타 연주, 게임, 독서" >> 자기소개.txt

# 완성된 작업 커밋
git add 자기소개.txt
git commit -m "feat: 2025년 목표와 취미 업데이트

추가된 내용:
- 2025년 구체적인 학습 목표 설정
- 독서 취미 추가로 학습 의지 표현

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>"

# main에 병합
git checkout main
git merge feature/new-goals
git branch -d feature/new-goals
```

---

## 🎯 고급 Git 도구들

### 🔍 Git Bisect: 버그 수사관

#### 개념: "이진 탐색으로 버그 발생 지점 찾기"
```bash
# 버그 수사 시작
git bisect start

# 현재 상태는 버그가 있음을 표시
git bisect bad

# 이전 정상 상태 표시 (예: 10커밋 전)
git bisect good HEAD~10

# Git이 자동으로 중간 지점으로 이동
# 테스트 후 good/bad 표시 반복
git bisect good  # 또는 git bisect bad

# 버그 지점 발견 후 종료
git bisect reset
```

### 🍒 Cherry-pick: 선별적 커밋 가져오기

#### 개념: "다른 브랜치에서 특정 커밋만 가져오기"
```bash
# 다른 브랜치의 특정 커밋을 현재 브랜치로 가져오기
git cherry-pick <commit-hash>

# 여러 커밋을 한번에 가져오기
git cherry-pick <commit1> <commit2> <commit3>

# 커밋 가져오기만 하고 자동 커밋은 하지 않기
git cherry-pick --no-commit <commit-hash>
```

### 📊 Git Reflog: 잃어버린 커밋 복구

#### 개념: "Git의 블랙박스, 모든 작업 기록"
```bash
# 최근 Git 작업 이력 확인
git reflog

# 특정 시점으로 복구
git reset --hard HEAD@{2}

# 브랜치 복구 (실수로 삭제한 브랜치)
git branch recovered-branch HEAD@{3}
```

---

## 🚀 실무 워크플로우 최적화

### 🔄 효율적인 Rebase 워크플로우

#### 1. Feature 브랜치 개발 패턴
```bash
# 1. main에서 최신 코드 가져오기
git checkout main
git pull origin main

# 2. feature 브랜치 생성
git checkout -b feature/awesome-feature

# 3. 작업 및 여러 커밋들...
# (개발 과정에서 많은 작은 커밋들 생성)

# 4. PR 전에 커밋 히스토리 정리
git rebase -i main

# 5. main의 최신 변경사항 반영
git rebase main

# 6. 깔끔한 상태로 push
git push origin feature/awesome-feature
```

#### 2. 팀 협업 시 Rebase 규칙
```bash
# ✅ 개인 브랜치에서는 자유롭게 rebase
git rebase -i HEAD~5

# ❌ 공유 브랜치에서는 rebase 금지
# (이미 다른 사람이 pull한 커밋은 rebase 하지 않기)

# ✅ main 브랜치 업데이트 반영
git rebase main

# ✅ PR 전 마지막 정리
git rebase -i main
```

---

## 🎮 종합 실습: 프로젝트 히스토리 완전 정리

### 📋 시나리오: "Git 학습 프로젝트의 최종 정리"

#### Step 1: 현재 상태 분석
```bash
# 전체 커밋 히스토리 분석
git log --oneline --graph

# 각 파일의 변경 이력 확인
git log --follow 자기소개.txt
```

#### Step 2: 최종 프로젝트 완성도 높이기
```bash
# 프로젝트 완성을 위한 마지막 브랜치
git checkout -b final/project-completion

# Git 학습 완료 표시
sed -i 's/Git 학습 프로젝트 (진행중)/Git 학습 프로젝트 (완료)/' 자기소개.txt

# 학습 성과 추가
echo "" >> 자기소개.txt
echo "=== Git 학습 성과 ===" >> 자기소개.txt
echo "✅ 기본 Git 명령어 마스터" >> 자기소개.txt
echo "✅ GitHub 협업 워크플로우 완전 이해" >> 자기소개.txt
echo "✅ 브랜치 전략과 충돌 해결 능력" >> 자기소개.txt
echo "✅ Pull Request 기반 코드 리뷰 문화" >> 자기소개.txt
echo "✅ Rebase와 고급 Git 기술 활용" >> 자기소개.txt

# 프로젝트 통계 추가
echo "" >> 자기소개.txt
echo "📊 프로젝트 통계:" >> 자기소개.txt
echo "- 총 커밋 수: 25+" >> 자기소개.txt
echo "- 브랜치 생성: 8개" >> 자기소개.txt
echo "- 충돌 해결: 2회" >> 자기소개.txt
echo "- Pull Request: 2개" >> 자기소개.txt
echo "- 학습 문서: 5개" >> 자기소개.txt

git add 자기소개.txt
git commit -m "feat: Git 학습 프로젝트 완료 및 성과 정리

프로젝트 완료 표시:
- 진행중 → 완료 상태 변경
- 상세한 학습 성과 목록 추가
- 프로젝트 통계 데이터 포함

학습 성과:
- 5개 레벨 완전 정복
- 실무 중심 Git 워크플로우 마스터
- 체계적인 버전 관리 역량 확보

🎉 Level 5 완료: Rebase와 고급 Git 기술 마스터

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>"
```

#### Step 3: main 브랜치에 최종 병합
```bash
# main으로 전환
git checkout main

# 깔끔한 병합
git merge final/project-completion

# 브랜치 정리
git branch -d final/project-completion

# 최종 결과 확인
cat 자기소개.txt
```

---

## 🎉 실습 완료 체크리스트

### Interactive Rebase 마스터
- [ ] 지저분한 커밋 히스토리 생성
- [ ] `git rebase -i` 명령어로 히스토리 정리
- [ ] 커밋 squash, reword, drop 활용
- [ ] 깔끔한 단일 커밋으로 정리 완료

### Git Stash 활용
- [ ] 작업 중 상황에서 stash 생성
- [ ] 응급 수정 작업 처리
- [ ] stash에서 작업 내용 복원
- [ ] stash 목록 관리 및 정리

### 고급 Git 도구 체험
- [ ] Git bisect로 버그 수사 이해
- [ ] Cherry-pick으로 선별적 커밋 가져오기
- [ ] Reflog로 작업 이력 추적

### 프로젝트 완성
- [ ] 최종 프로젝트 상태 정리
- [ ] 학습 성과 및 통계 추가
- [ ] 전체 Git 학습 과정 완료

---

## 💡 실무에서의 고급 Git 활용 패턴

### 🎯 깔끔한 히스토리 관리 전략

#### 커밋 분류 체계
```bash
# 기능 개발
feat: 새로운 기능 추가

# 버그 수정  
fix: 기존 기능의 오류 수정

# 문서 작업
docs: 문서 업데이트 또는 추가

# 코드 정리
refactor: 기능 변경 없이 코드 구조 개선

# 성능 향상
perf: 성능 개선 관련 변경사항

# 테스트
test: 테스트 코드 추가 또는 수정
```

### 🔄 팀 워크플로우 최적화

#### 효율적인 브랜치 전략
- **main**: 항상 배포 가능한 안정적인 코드
- **develop**: 개발 중인 기능들이 통합되는 브랜치  
- **feature/***: 개별 기능 개발 브랜치
- **hotfix/***: 긴급 수정 브랜치

#### Rebase vs Merge 선택 기준
- **Rebase 사용**: 개인 브랜치, 히스토리 정리 필요
- **Merge 사용**: 공유 브랜치, 협업 이력 보존 필요

---

## 🎯 전체 Git 학습 여정 완성!

### 📊 5레벨 학습 성과 요약

| 레벨 | 핵심 기술 | 실무 활용도 | 마스터 정도 |
|------|-----------|-------------|-------------|
| Level 1 | Git 기초 | ⭐⭐⭐⭐⭐ | ✅ 완료 |
| Level 2 | GitHub 연동 | ⭐⭐⭐⭐⭐ | ✅ 완료 |
| Level 3 | 브랜치 관리 | ⭐⭐⭐⭐ | ✅ 완료 |
| Level 4 | PR 워크플로우 | ⭐⭐⭐⭐⭐ | ✅ 완료 |
| Level 5 | 고급 Git 기술 | ⭐⭐⭐ | ✅ 완료 |

### 🚀 다음 단계 추천

#### 실무 프로젝트 적용
- 개인 프로젝트에 배운 Git 워크플로우 적용
- 오픈소스 프로젝트 기여 도전
- 팀 프로젝트에서 Git 리더 역할 수행

#### 심화 학습 영역
- GitHub Actions (CI/CD 자동화)
- Git Hooks (자동화 스크립트)
- 대규모 프로젝트 Git 전략 (Monorepo, Multi-repo)

---

## 📝 Level 5 핵심 요약

| 기술 | 용도 | 실무 중요도 |
|------|------|-------------|
| Interactive Rebase | 커밋 히스토리 정리 | ⭐⭐⭐⭐ |
| Git Stash | 임시 작업 보관 | ⭐⭐⭐⭐⭐ |
| Git Bisect | 버그 원인 추적 | ⭐⭐⭐ |
| Cherry-pick | 선별적 커밋 적용 | ⭐⭐⭐ |
| Reflog | 작업 복구 | ⭐⭐⭐⭐ |

**🎉 축하합니다! Git 마스터가 되셨습니다!**

이제 어떤 복잡한 버전 관리 상황도 자신있게 해결할 수 있는 진정한 Git 전문가입니다! 🚀