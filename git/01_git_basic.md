# CLI

Command Line Interface



# GUI vs CLI

- GUI : Graphic User Interface
- CLI : Command Line Interface(명령행 인터페이스)
- Interface : Inter(사이에) + Face(접면)



# CLI 명령어

Unix(Linux) 기반 명령어 (Linux, Mac)

- `pwd` (print working directory) : 현재 위치 출력

- `ls` (list) : 현재 폴더의 내용물 출력

- `cd [폴더명]` (change directory) : 폴더 변경

  - `cd ..` : 상위 폴더 이동
  - `cd ~` : 홈 폴더 이동

- `mkdir [폴더명]` (make directory) : 폴더 생성

- `rm [파일명]` (remove) : 파일 삭제

- `rm -r [폴더명]` : 폴더 삭제

  - `recursively` : 재귀적
  - `rm -rf [폴더명]` : (확인 X) 폴더 삭제
    - `rm -rf /`: `/` (폴더) 

- `mv [기존폴더명] [새로운폴더명]` : 폴더 변경 

- `touch [파일명]` : 파일 생성 

  cf) `nano [파일명]` : 파일생성

- `echo [문자열]` : command line 출력
  
  - `echo 'hello'` : hello 출력
  
- `echo [문자열] > [파일명]` : 특정 파일에 출력(기록)
  - `echo 'hello' > a.txt`  : hello가 a.txt 에 출력(기록)
  - `echo 'world' >> a.txt` :  world가 world 뒤에 출력(기록)
  
- `cat [파일명]` : 파일의 내용을 출력

# Git

Source Code Management(SCM) Tool : 코드 관리 도구

Version Control System(VCS) : 버전 관리 시스템

>버전을 통해 코드를 관리하는 도구

![image-20210425195323023](https://user-images.githubusercontent.com/80496345/116241056-75a02400-a79f-11eb-891b-2a85235e7645.png)

​					작업폴더

### 버전 관리를 하는 이유

1. 언제든 과거로 돌아갈 수 있음
2. 수정 이력을 확인할 수 있음



# Git 명령어

### 0. 폴더 생성

> git 저장소로 만들 폴더 생성

### 1. `git init`

> git 프로젝트(저장소)를 시작(폴더단위)

```
Initialized empty Git repositroy in C:/Users/student/git_basic/.git/
```

	1. (`master`)
	2. `.git` 폴더 생성

#### (중요) git 프로젝트를 종료

- `.git`  폴더 삭제

### 2. `git status`

> git의 현재 상태를 출력

- 최초 상태

```
on branch master : master라는 브랜치에 있음

No commits yet : 아직 commit이 없음

nothing to commit (create/copy files and use "git add" to track) : commit 할 게 없음
```

- 파일/폴더 추가시(`touch a.txt`)

```
​```
Untracked files: (추적되지 않은 파일)
(use "git add <file>..." to include in what will be committed)
	a.txt (빨강)
nothing added to commit but untracked files present (use "git add" to track)
: commit하기 위해 추가된 파일이 없음, 그러나 추적되지 않은 파일은 있음
```



- add 이후 (`git add a.txt`)

```
​```
Changes to be committed:
commit할 변화들
(use "git rm --cached <file>..." to unstage)
	new file: a.txt (초록)
```



- commit 이후 (`git commit -m "first commit"`)

```
On branch master
nothing to commit, working tree clean
```



### 3. `git add [파일명]`

> commit 하기 위한 stage에 파일 추가 

- `git add -u` : 삭제한 파일 stage에 올리기( u : update tracked files)



### 4. `git commit -m "커밋메시지"`

> 스냅샷 & 버전 생성

- `git commit --amend [파일명]` : (주의) 최종 커밋 메시지 변경

> add와 commit을 한번에

- `git commit -am "커밋 메시지"`
- 새로 만든 파일일 경우 add를 한번 해줘야 동작이 가능

##### commit 의 구성요소

- committer(author) : commit을 찍은 사람
- commit datetime(date) : commit을 찍은 시간
- commit message : commit에 대한 내용(필수)



### 5. `git config`

- `git config --global user.email "이메일"` : 사용자 이메일 설정
- `git config --global user.name "이름"` : 사용자 이름 설정
- `git config --global user.email` : 사용자 이메일 출력
- `git config --global user.name` : 사용자 이름 출력



### 6. `git log`

> commit 목록(log) 출력

- `git log --oneline` : 한줄 출력
- `git log -1` : 출력 개수 한정
- `git log -p` : 저장해 놓은 버전들의 기록들을 달라진점과 함께 보여줌

- `git log --all --graph --oneline` : 목록을 graph적으로 한줄 출력 

### 7. `git restore --staged [파일명]`

> unstage : stage 상태 해제



### 8. `git restore [파일명]`

> 최종 커밋 시점으로 파일 상태를 복원(restore)



### 9. `git diff [파일명]`

> 변경 내역 출력



## Checkout VS Reset

> checkout은 change와 비슷,  reset은 delete와 비슷

- Checkout  Checkout은 head의 값을 바꾸는 거
  - `Checkout 브랜치`
- Reset은 head가 가리키는 branch가 가리키는 버전을 바꾸는거다. 즉, branch를 바꾼다. 
  - `reset commid id`
- cf) Head가 브랜치를 가리키지 않고 commit을 가리키는 것을 detached라고 한다



### 10. `git checkout [commit id]`

> 돌아가고 싶은 commit id를 적으면 그때로 돌아가게 해준다(상상해서 가서 보는거다)



### 11. `git checkout master`

> 다시 원래 상태로 돌아가게 해준다



### 12. `git reset --hard [commit id]`

> (주의)달라 진 점을 지우고 **commit id 버전**으로 돌려줌

협업을 하기 때문에 사용하지 마라 일단



### 13. `git revert ` [commit id]

> commit id를 지우고 **그 id의 전 버전**으로 돌아간다

그런데 revert는 최신 id의 버전만 지우는것이기 때문에 여러 버전을 한번에 지울경우 충돌이 나서 다 지울 수 는 없다.



### 14. `git config --global core.editor "nano"`

> git의 설정을 바꾸는 것으로 global은 이 컴퓨터 전체에 설정을 바꾸는 것을 말하고 코어 editor를 "nano"로 바꾸겠다는 의미이다.



### 15. `git reset --hard [commit id` ]

> commit id로 리셋 하겠다. 이 아이디의 버전이 되겠다


