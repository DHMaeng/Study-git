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

