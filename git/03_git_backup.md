# 백업

### 1 . `git remote`

원격 저장소 정보 출력

- `git remote -v` : 상세 출력(**v**erbose : 말이 많은)



### 2. `git remote add [이름] [주소]`

원격 저장소 정보 추가

- 이름 : 관례/관습(Convention) `origin`(원본)
- 주소 : Github에서 repository 만들고 주소를 복사



### 2-1 `git remote remove origin`

기존 리포지토리 remote 제거



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