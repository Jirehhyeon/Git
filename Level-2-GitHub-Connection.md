# 🌍 Level 2: 세상과 연결 - GitHub와 연동하기

## 🎯 목표
**내 컴퓨터의 Git 저장소를 GitHub 원격 저장소와 연결하여 백업 및 공유할 수 있습니다.**

---

## 🔗 핵심 개념: GitHub는 Git의 클라우드 서비스

### GitHub를 이해하는 쉬운 비유: "구글 드라이브 + 소셜미디어"

GitHub를 **Git 전용 클라우드 서비스**라고 생각해보세요!

```
내 컴퓨터 (로컬)          인터넷 (GitHub)
    📁 Git 저장소    ←→    ☁️ 원격 저장소
   (개인 작업실)          (전 세계 공개 전시장)
```

- **백업**: 컴퓨터가 고장나도 코드가 안전하게 보관됨
- **공유**: 전 세계 개발자들이 내 코드를 볼 수 있음  
- **협업**: 다른 사람들과 함께 프로젝트를 진행할 수 있음
- **포트폴리오**: 내 개발 실력을 증명하는 이력서 역할

---

## 🏗️ Git vs GitHub: 헷갈리기 쉬운 차이점

| 구분 | Git | GitHub |
|------|-----|--------|
| **정체성** | 버전 관리 **도구** | Git 호스팅 **서비스** |
| **위치** | 내 컴퓨터 (로컬) | 인터넷 (클라우드) |
| **비유** | 사진기 | 인스타그램 |
| **기능** | 버전 관리, 브랜치 | 저장, 공유, 협업 |
| **설치** | 컴퓨터에 설치 필요 | 웹사이트 (github.com) |

### 🎯 핵심 이해
- **Git**: 버전 관리를 하는 "도구" (카메라)
- **GitHub**: Git 저장소를 올리는 "플랫폼" (인스타그램)

---

## 🔧 GitHub 시작하기

### 1. GitHub 계정 생성
1. https://github.com 접속
2. "Sign up" 클릭
3. 계정 정보 입력
4. 이메일 인증 완료

### 2. 새로운 원격 저장소 만들기

#### GitHub 웹사이트에서:
1. 로그인 후 "+" 버튼 → "New repository" 클릭
2. **Repository name**: `Git` (이미 생성됨 ✅)
3. **Description**: "Git 학습을 위한 저장소"
4. **Public** 체크 (전체 공개)
5. "Create repository" 클릭

---

## 🚀 로컬과 원격 저장소 연결하기

### 핵심 명령어: `git remote`

```bash
# 원격 저장소 추가 (origin이라는 별명으로)
git remote add origin https://github.com/사용자명/저장소명.git

# 원격 저장소 목록 확인
git remote -v

# 예상 결과:
# origin  https://github.com/Jirehhyeon/Git.git (fetch)
# origin  https://github.com/Jirehhyeon/Git.git (push)
```

### 🔍 `origin`이란?
- GitHub 저장소의 **별명**
- "원본"이라는 뜻으로, 메인 원격 저장소를 가리킴
- 다른 이름으로도 설정 가능하지만 `origin`이 관례

---

## 📤 내 컴퓨터에서 GitHub로: `git push`

### 기본 사용법
```bash
# 현재 브랜치를 원격 저장소로 업로드
git push origin main

# 첫 번째 push 시 (업스트림 설정)
git push -u origin main
```

### 🎯 `-u` 옵션의 의미
- **Upstream 설정**: 로컬 `main` 브랜치와 원격 `origin/main` 브랜치를 연결
- 이후에는 `git push`만 입력해도 자동으로 `origin main`으로 업로드

---

## 📥 GitHub에서 내 컴퓨터로: `git pull`

### 기본 사용법
```bash
# 원격 저장소의 최신 변경사항을 로컬로 다운로드
git pull origin main

# 업스트림이 설정된 경우
git pull
```

### 🔄 언제 사용하나요?
- 다른 컴퓨터에서 작업한 내용을 가져올 때
- 팀원이 올린 변경사항을 가져올 때
- GitHub 웹사이트에서 직접 수정한 내용을 가져올 때

---

## 🎯 실습 과제: GitHub 연동 마스터하기

### 📋 과제 1: 기존 저장소 연결 확인
이미 연결되어 있지만, 다시 한 번 확인해보겠습니다.

```bash
# 1. 현재 원격 저장소 확인
git remote -v

# 2. 원격 저장소 상태 확인
git remote show origin
```

### 📋 과제 2: GitHub에서 파일 편집하고 pull 연습

#### Step 1: GitHub 웹사이트에서 README.md 편집
1. https://github.com/Jirehhyeon/Git 접속
2. README.md 파일 클릭
3. 연필 아이콘(Edit) 클릭
4. 파일 하단에 내용 추가:
   ```markdown
   
   ## 🌟 GitHub 연동 성공!
   이 내용은 GitHub 웹사이트에서 직접 편집했습니다.
   ```
5. "Commit changes" 클릭
6. 커밋 메시지 입력: "GitHub 웹에서 README 업데이트"

#### Step 2: 로컬에서 변경사항 가져오기
```bash
# 1. 현재 로컬 상태 확인
git status

# 2. 원격 저장소의 변경사항 확인
git fetch origin

# 3. 변경사항을 로컬로 가져오기
git pull origin main

# 4. README.md 파일 확인
cat README.md
```

### 📋 과제 3: 로컬에서 편집하고 push 연습

#### Step 1: 로컬에서 새 파일 생성
```bash
# 새로운 파일 생성
echo "안녕하세요! GitHub와 연결된 첫 번째 메시지입니다." > github-test.txt

# 파일 내용 확인
cat github-test.txt
```

#### Step 2: GitHub에 업로드
```bash
# 1. 스테이징
git add github-test.txt

# 2. 커밋
git commit -m "GitHub 연동 테스트: github-test.txt 파일 추가

- 로컬에서 생성한 파일을 GitHub로 push 테스트
- Level 2 실습 과제 수행 중

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>"

# 3. GitHub에 업로드
git push origin main
```

#### Step 3: GitHub에서 확인
1. https://github.com/Jirehhyeon/Git 새로고침
2. `github-test.txt` 파일이 업로드되었는지 확인
3. 커밋 히스토리 확인

---

## 🎉 실습 완료 체크리스트

- [ ] GitHub 계정 생성 및 로그인
- [ ] 원격 저장소 연결 상태 확인 (`git remote -v`)
- [ ] GitHub 웹에서 README.md 편집
- [ ] `git pull`로 변경사항 로컬에 가져오기
- [ ] 로컬에서 `github-test.txt` 파일 생성
- [ ] `git push`로 GitHub에 업로드
- [ ] GitHub에서 업로드 결과 확인

---

## 🔥 추가 실습: 동기화 마스터 되기

### 🎮 실습 시나리오: "두 곳에서 작업하기"

#### 상황 설정
실제 개발자들은 회사 컴퓨터, 집 컴퓨터, 노트북 등 여러 곳에서 작업합니다. 이를 시뮬레이션해보겠습니다.

#### Step 1: GitHub에서 "회사에서 작업" 시뮬레이션
1. GitHub에서 `자기소개.txt` 파일 편집
2. 하단에 추가: `직업: 개발자`
3. 커밋 메시지: "회사에서 직업 정보 추가"

#### Step 2: 로컬에서 "집에서 작업" 시뮬레이션
```bash
# 1. 회사에서 한 작업을 집 컴퓨터로 가져오기
git pull origin main

# 2. 집에서 추가 작업
echo "좌우명: 꾸준함이 실력을 이긴다" >> 자기소개.txt

# 3. 커밋하고 업로드
git add 자기소개.txt
git commit -m "집에서 좌우명 추가"
git push origin main
```

#### Step 3: 결과 확인
```bash
# 전체 커밋 히스토리 확인
git log --oneline

# GitHub에서도 확인
```

---

## 🚨 자주 하는 실수와 해결법

### 1. push 거부당할 때
```bash
# 에러 메시지 예시:
# ! [rejected] main -> main (non-fast-forward)

# 해결법: 먼저 pull 받기
git pull origin main
git push origin main
```

### 2. 인증 문제
```bash
# GitHub 토큰 사용 (2021년 8월부터 비밀번호 대신 토큰 사용)
# Settings → Developer settings → Personal access tokens
```

### 3. 브랜치 이름 불일치
```bash
# 로컬이 master, 원격이 main인 경우
git branch -M main  # 로컬 브랜치명을 main으로 변경
```

---

## 🎯 다음 레벨 예고: Level 3

다음 레벨에서는 **브랜치(Branch)**를 활용하여:
- 🌿 여러 기능을 동시에 개발하고
- 🔀 안전하게 병합하며
- 🚀 실험적인 기능을 위험 없이 테스트하는 방법을 배웁니다!

---

## 📝 Level 2 핵심 요약

| 개념 | 명령어 | 의미 |
|------|--------|------|
| 원격 연결 | `git remote add origin URL` | GitHub 저장소와 연결 |
| 업로드 | `git push origin main` | 로컬 → GitHub |
| 다운로드 | `git pull origin main` | GitHub → 로컬 |
| 상태 확인 | `git remote -v` | 연결된 원격 저장소 보기 |
| 업스트림 설정 | `git push -u origin main` | 기본 연결 설정 |

**🎉 축하합니다! 이제 Git과 GitHub를 연동하여 전 세계와 코드를 공유할 수 있습니다!**