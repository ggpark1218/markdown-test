# 그동안 배운 Git Study 정리 :+1:
- - -
### 1. git과 github의 차이점
- **Git** : git 명령어를 칠 수 있도록 하는 소프트웨어이다.
- **GitHub** : git으로 관리하는 레포지토리들을 올리고 다운받는 웹사이트이다.

### 2. init, add, commit -m 명령어들에 대한 설명
- **git init** : 디렉토리를 git 레포지토리로 만들어 디렉토리 내의 파일을 git 이 추적하게 한다.
- **git add *<FILENAME>*** : <FILENAME> 을 스테이징 상태로 올려준다.
- **git commit -m *"커밋할내용"*** : 파일의 변동사항이 있으면 add 후 어떤 부분이 바뀌었는지 커밋해준다.

### 3. remote, clone, push, pull 명령어들에 대한 설명
- **git remote add origin *<주소>*** : 내 컴퓨터에 있는 git 이 인터넷에 연결될 수 있도록 하는 것이다.
- **git clone *<주소>***: gitHub에 있는 레포지토리를 내 로컬에 복사 할 수 있다.
- **git push -u *origin* *master*** : master 브랜치에 있는 별칭이 origin인 주소에 밀어넣는 것. 로컬 -> GitHub 로 올린다.
- **git pull *origin* *master*** : GitHub에 저장되어있던 내용을 로컬로 당겨온다.

### 4. 아래 사진을 첨부하기
![gitstudy](https://i.ytimg.com/vi/0nqJKEh3YCc/maxresdefault.jpg)
`사진 첨부는 ![gitstudy](https://i.ytimg.com/vi/0nqJKEh3YCc/maxresdefault.jpg) 이런식으로 한다.`

### 5. branch, checkout 명령어 설명
- **git branch** : 현재 상주하고 있는 브랜치를 출력
- **git branch *<branchName>*** : 새로운 브랜치 생성
- **git checkout master** : branch를 master로 변경

### 6. merge 2가지 설명 (fast-forward/Merge conflict)
- **git merge *<Name>*** : <Name>브랜치를 현재의 브랜치로 병합
#### 1. fast-forward 방식
   merge 할 브랜치의 commit이 현재 branch( 기준 브랜치, master 브랜치 )의 commit 보다 앞서가 있기 때문에, 기준 브랜치의 커밋을 대상 브랜치 commit으로 이동하겠다는 의미이다.
1. master 브랜치에서 testing 브랜치로 이동
    `git checkout -b testing`
![branch1](https://camo.githubusercontent.com/04c0b5678850c25e56df715d7393628c80e30437e27536cd4e9b2a174c8f91c8/68747470733a2f2f6769742d73636d2e636f6d2f626f6f6b2f656e2f76322f696d616765732f686561642d746f2d74657374696e672e706e67)
2. testing브랜치에서 main.c 코드 수정 후 git add, commit
![branch](https://camo.githubusercontent.com/2c4cf7d27e134aaafbc0eb2cffc99f418bd0dc72b357dc1f1e3fbb677c8af920/68747470733a2f2f6769742d73636d2e636f6d2f626f6f6b2f656e2f76322f696d616765732f616476616e63652d74657374696e672e706e67)
3. HEAD를 master로 이동: git checkout master
4. testing 브랜치에서 작업한 내용이 완전히 검증되었다고 하고, master 브랜치에서 testing 브랜치를 병합
`git merge <Name>`
5. 커밋 구조를 보면 master 브랜치가 testing 브랜치 바로 뒤에 있기 때문에 이 경우 Git 은 단순히 master 브랜치가 testing 브랜치가 포인팅하고 있는 커밋을 포인팅하게 한다. 이것을 Fast-forward 병합이라고 한다.

#### 2. Merge conflict 방식
1. 위 내용에서 3번까지 한 상황
![branch1](https://camo.githubusercontent.com/04c0b5678850c25e56df715d7393628c80e30437e27536cd4e9b2a174c8f91c8/68747470733a2f2f6769742d73636d2e636f6d2f626f6f6b2f656e2f76322f696d616765732f686561642d746f2d74657374696e672e706e67)
2. master브랜치에서 main.c 수정
3. git add, commit
![branch3](https://camo.githubusercontent.com/9d5044ac102d1a759a7b1fd06172344a3ddd7a90b109ee06cb9d4583d2a0b60a/68747470733a2f2f6769742d73636d2e636f6d2f626f6f6b2f656e2f76322f696d616765732f616476616e63652d6d61737465722e706e67)
4. main.c 확인해보면 `<<<HEAD, ===== ,>>>testing` 구역으로 나뉨
5. main.c 수정
6. 병합이 완료된 브랜치 삭제
`git branch -d <Name>` 
