# Git 이란 분산 버전 (변화 기록과 추적) 관리 시스템이다.

1. working directory
    - 현재 작업 영역
2. staging
    - 기록 대상
    - working directory에서 변경된 파일 중, 다음 버전에 포함시킬 파일들을 선택적으로 추가하거나 제외할 수 있는 중간 준비 영역
    - 내가 만든 부분만 변경되어 있는 임시 최종 저장소
3. repository
    - 저장소
    - 버전 (commit) 이력과 파일들이 영구적으로 저장되는 영역. 모든 버전과 변경이력이 기록됨
    - 다른 사람들과 함께 작업한 최종 저장소

### 해당 버전 작성자 지정. 이 컴퓨터 사용자이면 (--global). 

프로젝트 폴더별로 설정하려면, 해당 디렉토리 에서 --global 플래그 사용 제외하고 입력.

```bash
git config --global user.email "본인_이메일_주소"
git config --global user.name "본인_이름"
```
##### 해당 버전 작성자 확인 혹은 변경할 수 있는 파일 여는 명령
```bash
code ~/.gitconfig
```

### Exercise

1. initializing: study 라는 새 폴더를 생성해서 그 안에서 git bash의 command 로 `git init` 라고 치면, 파일 탐색기의 보기 옵션에서 숨김파일 표시가 되게 되어있으면  .git 이라는 폴더가 보임

2. Add modified files to staging area: `git add 파일_경로`
    - 현재 작업 디렉토리에 있는 모든 변경사항을 staging area 에 넣으려면 `git add .`

3. `git status` 하면, 
    - staging area에 있는 파일은 Changes to be commited: 밑에 나열되고
    - working directory 에 있는 파일들은 Untracked files: 밑에 나열됨
    - 변경했는데 staging area 에 넣디 않는 파일은 Changes not staged: 밑에 나열됨
    - stagng area 에 있는 파일중에 working directory 로 제외시키려면 `git restore --staged 파일_이름`

4. Staging area 에 있는 파일들을 master branch 로 Repository 에 최종 추가 하려면: `git commit -m "commit_이름"` 

5. commit 해서 repository 에 합친 내역을 보려면 `git log` 라고 치면 commit_이름 들이 나열됨

### 원격 저장소
- GitLab
  - private. 집단 생성 가능. 구성원만 들어갈 수 있음. repository member 가 아니면 집단 구성원들끼리도 repository 를 볼 수 없음. 
- GitHub
  - public
- BitBucket

##### 이미 만든 local 저장소 내용을 원격 저장소에 새로 만든 비어있는 repository 에 보내려면
```bash
git remote add origin 리포지토리_주소
``` 
그 리포지토리를 origin 이라고 부르겠다는거다.

주의: github이 master 를 main 으로 바꿈에 따라 `git branch -m main` 도 중간에 입력해야 한다.

```bash 
git push -u origin master
```
이제 진짜 그 원격에 upstream 이라는 방법으로 origin master 가 작업한 내용을 보냈다.

##### 원격 저장소에 저장한 작업물을 다른 컴퓨터에 이어서 작업하려면 git bash 를 열어서
```bash
git clone 리포지토리_주소
```
해서 그 컴퓨터에 모든 작업물을 다운받아서 변경작업을 수행하고 다시 push 하면 된다.

그리고 다시 원래 컴퓨터에 와서 작업할 때, 다른 컴퓨터에서 작업한 변경사항만을 가볍게 변경하고싶으면
```bash
git pull
```