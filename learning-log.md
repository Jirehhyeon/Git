# 📖 Git 학습 일지

## 🗓️ 2025-01-27 - Git 기초 학습

### ✅ 완료한 학습 내용

#### 1. Git 기본 개념 이해
- **Repository (저장소)**: 프로젝트의 모든 파일과 변경 이력을 저장하는 공간
- **Working Directory**: 실제 작업하는 폴더
- **Staging Area**: 커밋할 파일들을 임시로 저장하는 공간
- **Commit**: 변경사항을 저장소에 영구적으로 기록

#### 2. 실습한 Git 명령어

##### 저장소 초기화
```bash
git init                    # 새 Git 저장소 생성
git remote add origin URL   # 원격 저장소 연결
```

##### 기본 워크플로우
```bash
git status                  # 현재 상태 확인
git add README.md          # 파일 스테이징
git commit -m "메시지"     # 커밋 생성
git push origin main       # 원격 저장소에 업로드
```

##### 브랜치 관리
```bash
git checkout -b feature/learning-materials  # 새 브랜치 생성 및 전환
git checkout main                           # main 브랜치로 전환
git merge feature/learning-materials        # 브랜치 병합
```

#### 3. 실제 성과물
- ✅ Git 학습 저장소 생성: https://github.com/Jirehhyeon/Git.git
- ✅ README.md 파일 작성 및 업로드
- ✅ Git 명령어 치트시트 작성
- ✅ 브랜치 생성 및 머지 실습 완료

#### 4. 학습한 브랜치 워크플로우
1. `feature/learning-materials` 브랜치 생성
2. 새 브랜치에서 치트시트 파일 작성
3. 변경사항 커밋
4. `main` 브랜치로 전환
5. `feature` 브랜치를 `main`으로 머지

### 🎯 다음 학습 계획

#### 즉시 실습할 내용
- [ ] 현재 학습 내용을 GitHub에 업로드
- [ ] .gitignore 파일 생성 및 활용
- [ ] 실제 Arduino 프로젝트에 Git 적용

#### 중급 학습 목표
- [ ] Git 충돌 해결 방법 학습
- [ ] GitHub Issues 및 Pull Request 활용
- [ ] Git Flow 워크플로우 이해

#### 고급 학습 목표
- [ ] Git Hooks 활용
- [ ] 대용량 파일 관리 (Git LFS)
- [ ] 협업 시나리오 실습

### 📝 오늘의 배운 점

1. **Git은 단순한 백업이 아닌 협업 도구**: 브랜치를 통해 여러 기능을 동시에 개발할 수 있음
2. **커밋 메시지의 중요성**: 명확한 메시지로 작업 내용을 기록하는 것이 중요
3. **브랜치 워크플로우**: 기능별로 브랜치를 나누어 작업하면 안전하고 체계적
4. **원격 저장소 연동**: 로컬과 GitHub를 연결하여 어디서나 작업 가능

### 🚀 실제 적용 계획

#### Arduino 프로젝트에 Git 적용
- Desktop의 Arduino 프로젝트들을 Git으로 관리
- 각 프로젝트별로 브랜치를 만들어 체계적 관리
- GitHub에 업로드하여 포트폴리오로 활용

#### 협업 연습
- GitHub Issues로 개선사항 관리
- Pull Request를 통한 코드 리뷰 연습
- 오픈소스 프로젝트 기여 경험

### 💡 메모
- Git Bash에서 한글 경로 처리 시 주의사항 확인 필요
- CRLF 경고는 Windows 환경에서 자동 변환되는 것으로 정상
- 브랜치명은 `feature/`, `bugfix/`, `hotfix/` 등 prefix 사용 권장

---
*이 일지는 Git 학습 과정을 기록하고 복습하기 위한 문서입니다.*