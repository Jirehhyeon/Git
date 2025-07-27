# 🚀 Git 명령어 치트시트

## 📋 기본 설정

```bash
# 사용자 정보 설정
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# 설정 확인
git config --list
```

## 🏁 저장소 시작하기

```bash
# 새 저장소 초기화
git init

# 기존 저장소 복제
git clone <repository_url>

# 원격 저장소 연결
git remote add origin <repository_url>
```

## 📝 기본 워크플로우

### 1. 변경사항 확인
```bash
# 현재 상태 확인
git status

# 변경사항 자세히 보기
git diff
```

### 2. 파일 스테이징
```bash
# 특정 파일 추가
git add <filename>

# 모든 파일 추가
git add .

# 특정 확장자 파일 추가
git add *.js
```

### 3. 커밋
```bash
# 커밋 메시지와 함께 커밋
git commit -m "커밋 메시지"

# 스테이징과 커밋 한번에
git commit -am "커밋 메시지"

# 마지막 커밋 수정
git commit --amend
```

### 4. 원격 저장소와 동기화
```bash
# 원격 저장소로 업로드
git push origin main

# 원격 저장소에서 다운로드
git pull origin main

# 첫 번째 푸시 (업스트림 설정)
git push -u origin main
```

## 🌿 브랜치 관리

```bash
# 브랜치 목록 보기
git branch

# 새 브랜치 생성
git branch <branch_name>

# 브랜치 전환
git checkout <branch_name>

# 브랜치 생성과 전환 동시에
git checkout -b <branch_name>

# 브랜치 삭제
git branch -d <branch_name>

# 브랜치 강제 삭제
git branch -D <branch_name>
```

## 🔄 머지(병합)

```bash
# 브랜치 병합
git merge <branch_name>

# 브랜치 병합 (No Fast-Forward)
git merge --no-ff <branch_name>
```

## 📊 히스토리 확인

```bash
# 커밋 로그 보기
git log

# 한 줄로 로그 보기
git log --oneline

# 그래프로 로그 보기
git log --graph --oneline

# 특정 파일의 히스토리
git log --follow <filename>
```

## 🔙 되돌리기

```bash
# 스테이징 취소
git reset HEAD <filename>

# 작업 디렉토리 변경사항 취소
git checkout -- <filename>

# 마지막 커밋으로 되돌리기 (변경사항 유지)
git reset --soft HEAD~1

# 마지막 커밋으로 되돌리기 (변경사항 삭제)
git reset --hard HEAD~1
```

## 🏷️ 태그

```bash
# 태그 생성
git tag <tag_name>

# 주석이 있는 태그 생성
git tag -a <tag_name> -m "태그 메시지"

# 태그 목록 보기
git tag

# 태그 푸시
git push origin <tag_name>

# 모든 태그 푸시
git push origin --tags
```

## 🔍 유용한 명령어

```bash
# 특정 문자열 검색
git grep "search_term"

# 파일 이름 변경 추적
git mv <old_filename> <new_filename>

# 파일 삭제 추적
git rm <filename>

# 스테이지된 파일만 삭제
git rm --cached <filename>

# 현재 작업 임시 저장
git stash

# 임시 저장된 작업 복원
git stash pop
```

## 🚨 긴급 상황 해결

```bash
# 마지막 커밋 메시지 수정
git commit --amend -m "새로운 커밋 메시지"

# 잘못된 브랜치에서 작업한 경우
git stash
git checkout <correct_branch>
git stash pop

# 강제 푸시 (주의!)
git push --force-with-lease
```

## 🎯 실습 예제

### 기본 워크플로우 실습
```bash
# 1. 저장소 초기화
git init

# 2. 파일 생성 및 추가
echo "Hello Git!" > hello.txt
git add hello.txt

# 3. 첫 커밋
git commit -m "첫 번째 커밋"

# 4. 원격 저장소 연결
git remote add origin <your_repo_url>

# 5. 업로드
git push -u origin main
```

---
**💡 팁**: 
- 커밋 메시지는 명확하고 간결하게 작성하세요
- 자주 커밋하고, 의미있는 단위로 나누세요
- 브랜치를 활용해서 기능별로 개발하세요