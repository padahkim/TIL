
# Concept 
Version control system
# References
- [깃(?)똥차게 좋은 GIT 기초 by slowalk](http://slowalk.tistory.com/2470)
- [완전 초보를 위한 깃허브 by nolboo](https://nolboo.kim/blog/2013/10/06/github-for-beginner/)
- [A Visual Git Reference by marklodato](https://marklodato.github.io/visual-git-guide/index-ko.html)
- [ Visualizing Git Concepts with D3 by onlywei](http://onlywei.github.io/explain-git-with-d3/#/)
- [깃 명령어 실행 순서(로컬폴더 시작) by wayhome25](https://github.com/wayhome25/git_practice/blob/master/README.md#%EC%A3%BC%EC%9A%94-%EB%AA%85%EB%A0%B9%EC%96%B4)
# Terminologies

### **Snapshots**
-   Git이 코드 히스토리를 기억하는 방식.
-  사진찍기와 유사.

### **Commit**
-   Snapshot을 생성하는 행위 (즉, 기록을 남기는 행위)
-   Git 히스토리는 기본적으로 수 많은 Commit들의 집합이다.

하나의 Commit은 다음 세 가지 정보를 갖고 있습니다.

-   이전 Commit (Parent Commit)
-   이전 Commit과 비교한 수정 내역
-   Commit Hash (굉장히 복잡한 알고리즘으로 생성한 고유 아이디 값)

### **Repository**

-   줄임말로 Repo, 한국어로 저장소라 부른다.
-   모든 프로젝트 파일들과 그 파일들의 히스토리가 모여 있는 곳
-   개인 컴퓨터 혹은 Github과 같은 클라우드 서버에 저장할 수 있다.

### **HEAD**

-   현재 위치하고 있는 Commit

### **Branch**

-   모든 Commit들은 Branch 내에 존재한다.
-   하나의 커밋은 여러 Branch에 속할 수 있다.
-   일반적으로 프로젝트의 기본 브랜치는 `master` 이다.
    
    # **Commands**
    
### git clone
  클라우드에 저장된 Git 프로젝트를 다운받는 명령어
`git clone GIT_REMOTE_ADDRESS ` 

### git add
변경 사항 중, 다음 커밋에 추가할 사항들을 선별하는 명령어
`git add FILE_OR_DIRECTORY ` 

### git commit
 커밋을 생성하는 명령어
  `-m`  은 커밋 메시지를 함께 추가하는 옵션
`git commit -m "MY COMMIT MESSAGE"` 

### git branch
 브랜치 목록
`git branch `
 브랜치 생성 
`git branch BRANCH_NAME`
  브랜치 삭제 
 `git branch -d BRANCH_NAME` 

### git checkout
브랜치 이동
`git checkout BRANCH_NAME`
브랜치 생성 & 이동 
`git checkout -b BRANCH_NAME` 

### git merge
 현재 브랜치에 다른 브랜치의 수정 내역을 병합하는 명령어
`git merge OTHER_BRANCH_NAME `

### git fetch
Github과 같은 클라우드에 저장된 Git 프로젝트의 현재 상태를 다운만 받아놈(현재 프로젝트에 영향x)
`git fetch origin ` 

### git pull
 Github과 같은 클라우드에 저장된 Git 프로젝트의 현재 상태를 다운받고 현재 위치한 브랜치로 병합하는 명령어
 `git fetch`  +  `git merge`
`1git pull REMOTE_NAME  BRANCH_NAME 2` 

### git push

  Github과 같은 클라우드에 내 컴퓨터의 작업 사항을 업데이트 하는 명령어
  등록된 클라우드 주소 닉네임(`REMOTE_NAME`)과 반영하고 싶은 브랜치 이름(`BRANCH_NAME`)을 함께 사용해야 한다.
`git push REMOTE_NAME  BRANCH_NAME` 

### git remote
  클라우드 주소를 등록하는 명령(ex: gitlab->local->github)
  등록하는 주소마다 고유 닉네임을 부여해야 한다.
  
 등록 `git remote add REMOTE_NAME  REMOTE_ADDRESS `
 삭제 `git remote remove REMOTE_NAME` 

### git log
현재 위치한 브랜치의 커밋 내역을 확인하는 명령
`git log `


# Command flow (from local)
```
mkdir tic-tak-toe   // 로컬 디렉토리 만들고
cd tic-tak-toe
touch index.html 
code . //파일생성후 실행 여기서 부터 시작
git init //현재 디렉토리를 git이 관리하게끔 시작(ls -a해보면 .git이라는 숨겨진 디렉토리가 생김)
git add 파일명.확장자  // 깃 주목 리스트에 파일을 추가
git rm 파일명.확장자   //깃 주목 리스트에 파일을 삭제
git add .           // 현재 디렉토리의 모든 파일 추가.
git commit -m “Initial Commit(커밋내용)” // 커밋해서 스냅샷을 찍는다.
git log //커밋한 내용을 정보 확인(커밋해쉬값)

-----making branch------
git branch feature // feature라는 브랜치를 만듬(아직 옮기지는 않음)
git branch //브랜치 전부 확인
git log (feature브랜치이며 동시에 master브랜치- 이상태에서 수정후 커밋할시 master만 변경)
git checkout feature (feature 브랜치로 이동)
git commit // 이동 했으므로 커밋할시 branch가 변경
-----merge branch to master(마스터에 브랜치를 머지)-----
git checkout master 
git merge feature
------remote-------
git remote -v // 연결상태를 확인한다.현재 아무것도 없음
깃헙에서 repository 생성
git remote add origin(이름아무거나ㅇㅋ) https://github.com/username/myproject.git // 로컬과 원격 저장소를 등록(연결)한다.
git remote set-url origin  https://111.111.111.111/저장소.git
git push origin(위에서 등록한 이름) master // 깃허브로 푸시한다.
git pull origin(위에서 등록한 이름) master // 깃허브에서 풀한다. 

git pull origin master --allow-unrelated-histories // fatal: refusing to merge unrelated histories 오류 발생시
git stash // origin 파일과 master 파일 충돌시 명령 (error: Your local changes to the following files would be overwritten by merge)

```
