[TOC]

# LI

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



![image-20210425195323023](https://user-images.githubusercontent.com/80496345/116241056-75a02400-a79f-11eb-891b-2a85235e7645.png)

​					작업폴더



# Branch & conflict

### 1. `git branch`

> 현재 브랜치 출력



### 2. `git branch [이름]`

> `[이름]` 브랜치 생성

![git branch  이름](https://user-images.githubusercontent.com/80496345/116816029-4e7c9480-ab9b-11eb-90bd-60d4e5868f1d.jpg)

### 3. `git checkout [이름]`

> [이름] 상태로 갈수있다.

- apple로 들어가 `nano work.txt`를 통해 수정하고 커밋을 한뒤 그래프 출력하면 이렇게 나온다.

![branch apple](https://user-images.githubusercontent.com/80496345/116816030-4e7c9480-ab9b-11eb-871c-3a4afcb94580.jpg)

- google, ms 모두 커밋한 상태

![image-20210502195459931](https://user-images.githubusercontent.com/80496345/116816358-8df7b080-ab9c-11eb-9c85-ce441b85bf2f.png)



### 4. merge(병합) 

> master를 apple, google branch로 분리한 것을 필요에 의해 apple과 master를 합치는 것이 merge이다.

- base : 브랜치가 쪼개져  나갈때 공통의 조상을 말한다. 브랜치 이름이 아니다

![image-20210502200000620](https://user-images.githubusercontent.com/80496345/116816306-64d72000-ab9c-11eb-8d38-d6a27278c235.png)

#### 1. `o2 -> master`  : `o2 branch`를 `master`에 병합 

![o2 master 병합전](https://user-images.githubusercontent.com/80496345/116816035-4fadc180-ab9b-11eb-8d7d-f5f934f7f0e3.jpg)

이 상황에서 진행할 때 

1. `git checkout master` : 우선 master branch 상태가 되야한다.

2. `git merge o2` : master와 o2를 병합한다. 커밋메시지를 적을 수 있다.

   그리고 log를 보면 다음과 같이 head는 새로운 commit을 가리키고  o2의 최신 커밋과 master의 이전 커밋을 공통의 조상으로 하는 그래프를 보여준다.

![o2 master 병합후](https://user-images.githubusercontent.com/80496345/116816036-4fadc180-ab9b-11eb-86fb-03f94e764f9a.jpg)



#### 2. 같은 파일에서 다른 부분 수정시 merge

잘 병합 되었다.

![같은 파일 다른 부분 수정 merge](https://user-images.githubusercontent.com/80496345/116816037-50465800-ab9b-11eb-9c59-12e46be670a6.jpg)



#### 3. 같은 파일에서 같은 부분 수정시 merge

다음과 같이 충돌이 난다.

![같은 파일 같은 부분 수정 merge](https://user-images.githubusercontent.com/80496345/116816040-50deee80-ab9b-11eb-8665-ab76c114ea43.jpg)

`nano work.txt` 로 해당 파일 들어가보면 다음과 같이 나온다.

![conflict 난 부분 해석](https://user-images.githubusercontent.com/80496345/116816038-50465800-ab9b-11eb-8dda-679ef581666d.jpg)![conflic 수정 후](https://user-images.githubusercontent.com/80496345/116816044-52101b80-ab9b-11eb-8e6a-299f2274b37d.jpg)

​		<수정전>										<수정후>

그런다음 `git add work.txt ` , `git commit`하면 충돌해결!  



#### 4. 3 way merge

3 way merge를 이용하면 2 way merge가 해결하지 못한 두번째 세번째 부분을 자동화 하여 병합해 줄 수 있다.

2번째 부분은 here브랜치에서 수정된 H를 채택하고 3번째 부분은 there branch에서 수정된 T를 채택한다.

![3 way merge](https://user-images.githubusercontent.com/80496345/116816045-52101b80-ab9b-11eb-8fba-a070ebb7ce00.jpg)

다음과 같이 branch there과 here을 만든 뒤 here에서 there을 병합

![3 way merge2](https://user-images.githubusercontent.com/80496345/116816047-52a8b200-ab9b-11eb-8dd2-ce4ff631c94b.jpg)

- Download P4merge 

  ![p4merge](https://user-images.githubusercontent.com/80496345/116816026-4cb2d100-ab9b-11eb-905b-8d1c4ac9e780.jpg)

- https://gist.github.com/dgoguerra/8258007 : 환경셋팅

  ![p4merge 환경셋팅](https://user-images.githubusercontent.com/80496345/116816027-4de3fe00-ab9b-11eb-8be1-4b7b5da2787e.jpg)

- `git mergetool` : merge tool 실행
- 수정하고 저장하면 `git status` : work.txt , work.txt.orig(빽업) 생성

- `rm work.txt.orig` 지우기

- `git commit` 후 log를 보면 잘 병합된다.

  ![3 way merge3](https://user-images.githubusercontent.com/80496345/116816028-4de3fe00-ab9b-11eb-9b62-beb2479d4430.jpg)



# 백업

### 1 . `git remote`

원격 저장소 정보 출력

- `git remote -v` : 상세 출력(**v**erbose : 말이 많은)



### 2. `git remote add [이름] [주소]`

원격 저장소 정보 추가

- 이름 : 관례/관습(Convention) `origin`(원본)
- 주소 : Github에서 repository 만들고 주소를 복사



### 3. `git push [이름] [브랜치]`

- git push -u origin master

  지역 저장소 마스터와 원격저장소 마스터라는 브랜치를 직접 페어링 하는 작업(한번만)

원격 저장소에 코드 업로드

- `git push origin master`

```
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (8/8), 668 bytes | 668.00 KiB/s, done.
Total 8 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/hphk-john/git_review.git
* [new branch] master -> master
```



### 4. `git clone [주소] [파일 이름]`



원격 저장소에 저장되어있는 디렉토리 복제. 파일이름을 적지 않으면  디렉토리에 이름으로 자동으로 저장

```
Cloning into 'my-repo'...
remote: Enumerating objects: 13, done.
remote: Counting objects: 100% (13/13), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 13 (delta 1), reused 13 (delta 1), pack-reused 0
Receiving objects: 100% (13/13), done.
Resolving deltas: 100% (1/1), done.
```

![image-20210426001039765](https://user-images.githubusercontent.com/80496345/116241059-7638ba80-a79f-11eb-8e36-6605373952f5.png)



#### 참고

\### git l 설정방법 ###
1) git cmd 창에서 nano ~/.gitconfig 를 입력하셔서 설정 파일을 엽니다.
2) 아래 내용을 입력하면, git l 단축명령어를 사용할 수 있습니다.
[alias]
l = log --all --graph --oneline





# 협업

> 디렉토리 -> 세팅 -> Manage access -> invite a collaborator -> git clone해서 받는다.



- git pull vs fetch
  - git pull -> commit -> push 
  - git fetch ->git fetch; git merge FETCH_HEAD -> commit -> push

> 리모트 브랜치만 가져옴 -> 리모트 브랜치를 지역브랜치랑 머지 함으로써 신중하게 깃의 데이터를 가져오기 싶을때 이렇게 하면 된다.



# 오류

```bash
aodeh@Maeng MINGW64 ~/git/springRepo/spring (master)
$ git push origin master
To https://github.com/DHMaeng/Study-Spring.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/DHMaeng/Study-Spring.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.


aodeh@Maeng MINGW64 ~/git/springRepo (master)
$ git fetch origin


aodeh@Maeng MINGW64 ~/git/springRepo (master)
$ git log origin/master


aodeh@Maeng MINGW64 ~/git/springRepo (master)
$ git pull origin master
From https://github.com/DHMaeng/Study-Spring
 * branch            master     -> FETCH_HEAD
CONFLICT (rename/delete): spring/02. 커넥션 풀.md deleted in 6c2597be8d8bb7a44f0a6da24b3ad4583f262a3f and renamed to spring/04.커넥션풀.md in HEAD. Version HEAD of spring/04.커넥션풀.md left in tree.
Automatic merge failed; fix conflicts and then commit the result.

aodeh@Maeng MINGW64 ~/git/springRepo (master|MERGING)
$ git config merge.tool vimdiff

aodeh@Maeng MINGW64 ~/git/springRepo (master|MERGING)
$ git config merge.conflictstyle diff3

aodeh@Maeng MINGW64 ~/git/springRepo (master|MERGING)
$ git config mergetool.prompt false

aodeh@Maeng MINGW64 ~/git/springRepo (master|MERGING)
$ git mergetool
Merging:
spring/04.커넥션풀.md

Deleted merge conflict for 'spring/04.커넥션풀.md':
  {local}: created file
  {remote}: deleted
Use (c)reated or (d)eleted file, or (a)bort? c


https://stackoverflow.com/questions/161813/how-to-resolve-merge-conflicts-in-git-repository
```

