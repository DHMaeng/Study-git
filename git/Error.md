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

