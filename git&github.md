# 1. Git 시작하기

- git : 버젼 관리 시스템
- git을 쓰는 이유?  
    - 수정 사항 파악
    - backup 용이

## <a href="https://git-scm.com/downloads" target="_blank">Git download</a>

- Git 다운로드 후 `Git Bash` 를 실행해도 되지만, `VS code`에서 ``Ctrl + ` ``로 터미널을 열어 기본 쉘을 `PowerShell` 에서 `Git Bash` 로 변경하여 사용하는 것을 추천한다.

<br><br>

### a. 초기 설정

명령어 | 뜻
-------|---
config | 설정할때 사용

```bash
// 본인의 github 계정 및 이름 등록
git config --global user.email myemail@gmail.com
git config --global user.name "Go-oh"
```

<br><br>

### b. 기초 명령어

- 순서는 **`add` -> `commit` -> `push`** 순이다.

명령어 | 뜻
-------|---
`add` | 커밋 대상 지정 / 커밋 대상에 추가
`commit` | 커밋함
`commit -m` | 커밋할 때 메시지(-m, *message*) 추가
`commit -sm` | 커밋할 때 사인(-s, *signed*)과 메세지(-m, *message*) 추가
`commit --amend` | 가장 최근의 커밋을 수정. (amend : 수정하다)
`push` | 커밋된 것들을 github.com에 업로드. 에러날때가 있는데 주로 local에서 커밋 ID != Github에서의 커밋 ID여서다. 이때 강제로 푸쉬하면 이전에 푸쉬했던거 다 날라가니 주의
`push origin master -f` | 강제로 푸쉬. 참고로 `origin` 이란 리모트(git url)에 `master`란 브랜치로 `push` 한다는 의미
`init` | 해당 폴더를 git 초기화
`remote` | 현재 있는 리모트 저장소를 확인
- *`커밋한다` 는 의미는 `수정한 코드로 최신화한다` 와 같음*
- *`add`, `commit` 과 달리 `push`는 인터넷에 연결되어야 함*

```bash
$ git init

Go-oh@DESKTOP MINGW64 ~/report-card (master)
$ ls -A
.git 

$ git add exam.c
$ git commit -sm "This code is example"

//origin 부분은 본인 마음대로 네이밍하면 된다. ex)aa
$ git remote add origin https://github.com/Go-oh/git-example

//`git push`시 거절당하는 경우 `git push origin master -f'로 강제 push 한다.
$ git push origin master
To https://github.com/Go-oh/git-example.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/Go-oh/git-example.git'       
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing        
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

$ git push origin master -f
Enumerating objects: 18, done.
Counting objects: 100% (18/18), done.
Delta compression using up to 6 threads
Compressing objects: 100% (16/16), done.
Writing objects: 100% (18/18), 224.80 KiB | 14.99 MiB/s, done.
Total 18 (delta 3), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (3/3), done.
To https://github.com/Go-oh/git-example.git
 + 901907c...5e53a38 master -> master (forced update)

```

<br><br>

### c. 상태확인 명령어

명령어 | 뜻
-------|---
`status`| (주로 `git add` 이후) `commit` 가능한게 있는지 확인한다. 
`diff`| (`commit` 된 코드와 파일명이 같을 때) 이전에 `commit` 된 코드와 아직 `commit` 하지 않은 코드를 비교. 즉, 코드간 차이점을 비교함
`log`| `commit` 로그 확인
`shortlog`| `log` 보다 짧게 로그 확인
`show` | `commit` 된 코드 출력

```bash
/**git status
*/
$ git status
On branch master
nothing to commit, working tree clean

//git status - 코드가 삭제됐을 때
$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    report_card.c   //코드 삭제됨

no changes added to commit (use "git add" and/or "git commit -a")

//git status - 코드가 수정됐을 때
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   report_card.c   //코드 수정됨

no changes added to commit (use "git add" and/or "git commit -a")



/**git log
*/
$ git log
commit 019ccc20cb1b23b4683f14808003bef6bd3d10fa (HEAD -> master)
Author: Go-oh <jfknfj920@naver.com>
Date:   Sat Jun 27 17:06:26 2020 +0900

    연습용 코드3
    //Signed-off-by : `git commit` 시 `-sm` 옵션을 주면 `commit`한 사람의 이름과 이메일로 서명됨
    Signed-off-by: Go-oh <jfknfj920@naver.com>

commit 22d4abe8bf9306fcab56ddf2a1ae885237aec4d5
Author: Go-oh <jfknfj920@naver.com>
Date:   Sat Jun 27 17:01:43 2020 +0900

    연습용 코드2

commit 2ba7fffd1cc4403e351adbde95626aa91429d22f
Author: Go-oh <jfknfj920@naver.com>
Date:   Sat Jun 27 16:58:23 2020 +0900

    연습용 코드1

commit 92e3e288e7a27bbe694722d70b300b28d20fe683
Author: Go-oh <jfknfj920@naver.com>
Date:   Sat Jun 27 16:55:49 2020 +0900

 깃 연습1
(END)           //(END)를 탈출하려면 `Ctrl + c` 대신 `q` 를 입력



/**git shortlog : git log 보다 짧게 출력
*/
$ git shortlog
Go-oh (4):
      깃 연습1
      연습용 코드1
      연습용 코드2
      연습용 코드3



/**git show : 최종 수정된 코드를 보여줌
*/
$ git show
commit 019ccc20cb1b23b4683f14808003bef6bd3d10fa (HEAD -> master)
Author: Go-oh <jfknfj920@naver.com>
Date:   Sat Jun 27 17:06:26 2020 +0900

    연습용 코드3

diff --git a/report_card.c b/report_card.c
index edef60d..dba57ff 100644
--- a/report_card.c
+++ b/report_card.c
@@ -2,6 +2,16 @@

 int main()
 {
+       int kor, eng, math;
+
+       math = 80;
+       eng = 100;
+       kor = 90;
+
        printf("This program print report card.\n");
+
+       printf("Korean : %d\n", kor);
+       printf("English : %d\n", eng);
+       printf("Math : %d\n", math);
        return 0;
 }
(END)



/**git diff : 이전 코드와 차이점을 보여줌
*/
$ git diff
Go-oh@DESKTOP MINGW64 ~/report-card (master)
diff --git a/report_card.c b/report_card.c
index 8c1597f..4a729cc 100644
--- a/report_card.c
+++ b/report_card.c
@@ -16,6 +16,6 @@ int main()
        printf("English : %d\n", eng);
        printf("Math : %d\n", math);
        printf("Sum : %d\n", sum);      
-       printf("Mean : %d\n", sum/3);       //삭제된 코드
+       printf("Average : %d\n", sum/3);    //추가된 코드 
        return 0;
 }
(END)



//git diff - 아무것도 출력되지 않을 때. 코드를 `add`후 `commit`까지 했을 경우 코드가 최종 버젼으로 변경되기 때문에 `git diff`시 아무것도 출력되지 않음
Go-oh@DESKTOP MINGW64 ~/report-card (master)
$ git diff

Go-oh@DESKTOP MINGW64 ~/report-card (master)
$
```


<br><br>

### d. 기타 명령어

명령어 | 뜻
-------|---
`reset` | 방금 한 `add` 를 취소
`reset HEAD~1` | 최근 `commit` 1개를 취소. 이후 다시 `push`를 하면 `commit` 수가 줄어드는 것을 확인할 수 있음


<br><br><br>

# 2. pull-request

- pull-request : 다른 프로젝트에 내가 만든 `commit`을 제출한다.
    - 원리 : 다른 프로젝트 `fork` -> 내 계정에서 해당 프로젝트를 새로 만듬 -> 이를 토대로 `commit`한 내용을 pull-request 한다

<br><br>

명령어 | 뜻
-------|---
`checkout` | `branch` 를 전환. ex) `git checkout master`, `git checkout develop`  
`clone` | 특정 url의 repo를 받아옴. ex) `git clone https://github.com/Go-oh/git-training.git`
`branch` | `branch` 목록들을 보여줌과 동시에 현재 브랜치가 무엇인지 보여줌
`merge` | 현재 브랜치(`git status`시 나오는 브랜치)를 기준으로 다른 브랜치와 합침. 이렇게 되면 `commit` 내역이 합쳐짐

- `git push` 이후 github.com 에서 fork한 repo에 pull-request를 시도한다. 이 때, 본래 프로젝트 url에서 pull request 되었는지 확인한다.
- `branch` : 한 윈도우에 여러 계정을 쓰는 느낌...? 브랜치 마다 파일이 보여지거나 숨겨진다. `commit` 개수도 다를 수 있다.

# 3. Rebase
- rebase : 말 그대로 base(기준)을 바꿈
    - 용도 : 여러 개발자와 협업시 *history*를 간단히 하려할 때
    - 젠가에서 바꿀 블럭을 빼고 전체를 바꾼뒤(*tree*) 바꿀 블럭을 나중에 쌓아올린다는 느낌
    
<br><br>


### `merge`와 `rebase`의 차이점

명령어 | 설명
-------|---  
`merge` | 변경 내용의 이력이 모두 그대로 남아 있기 때문에 이력이 복잡해짐.  
`rebase` | 이력은 단순해지지만, 원래의 커밋 이력이 변경됨. 정확한 이력을 남겨야 할 필요가 있을 경우에는 사용하면 안됨.

명령어 | 뜻
-------|---
`rebase -i --root` | -i : interactive, --root는 최초 commit 까지 수정할수 있도록 하기 위함
`rebase --continue`| commit 을 수정후 원래대로 복귀
`fetch` | 특정 `remote`의 `branch`를 가져옴 ex)`git fetch upstream dev`
`blame` | 특정 파일에서 누가 어느라인을 수정했는지 확인 가능 ex)`git blame exam.c`

```bash


//협업상황을 가정. 임의 개발자의 repo를 remote로 두고 branch를 rebase하는 상황
//$ git remote get-url upstream
//https://github.com/Taeung/git-training.git
$ git fetch upstream dev
From https://github.com/Taeung/git-training
 * branch            dev        -> FETCH_HEAD

///////////////////////////$ git rebase upstream/dev

//remote : upstream, brnach : dev
$ git status
HEAD detached at upstream/dev
nothing to commit, working tree clean


$ git remote; git branch
origin
upstream
* (HEAD detached at upstream/dev)
  branch
  c
  dev
  develop
  master
  remove
  test


$ git shortlog
Taeung Song (13):
      Add README file
      Add knapsack problem PDF
      packing knapsack: Basic code solving this question
      packing knapsack: Change basic code
      packing knapsack: Rename packing_knapsack to pack_knapsack
      packing knapsack: Input & Output
      packing knapsack: Add test script
      packing knapsack: Add test script generator
      packing knapsack: Implement code to solve this question
      test git-pull-request
      New version git-training
      Add v3 PDF


$ git rebase -i --root
Successfully rebased and updated detached HEAD.

pick 73e7acf Add README file
edit 864cf0f 수정수정수정                     //두 번째 커밋을 바꾸려 pick을 edit으로 수정
pick f9b87bb packing knapsack: Basic code solving this question
pick 91f2d24 packing knapsack: Change basic code
pick 3102e80 packing knapsack: Rename packing_knapsack to pack_knapsack
pick 1863ec4 packing knapsack: Input & Output
pick 4c744f0 packing knapsack: Add test script
pick b2218e5 packing knapsack: Add test script generator
pick f3be23d packing knapsack: Implement code to solve this question
pick 18de302 test git-pull-request
pick 32b69ec New version git-training
pick 2504a40 Add v3 PDF
pick 1b19aee Rebase test


//아랫줄에서 'REBASE-i 2/13' 를 통해 두 번째 커밋을 수정중임을 알수있다.
//기존과 달리 shortlog시 커밋수가 13 -> 2개로 줄어듬
mm@DESKTOP MINGW64 ~/Desktop/Go-oh/git-training (detached HEAD|REBASE-i 2/13)
$ git shortlog             
Taeung Song (2):
      Add README file
      수정수정수정


//기존엔 커밋할게 없다 떴는데, 지금은 status시 총 커밋수중 몇번째 커밋인지 확인가능
mm@DESKTOP MINGW64 ~/Desktop/Go-oh/git-training (detached HEAD|REBASE-i 2/13)
$ git status                
interactive rebase in progress; onto 6dd6acb
Last commands done (2 commands done):
   pick 73e7acf Add README file
   edit 864cf0f 수정수정수정
Next commands to do (11 remaining commands):
   pick f9b87bb packing knapsack: Basic code solving this question
   pick 91f2d24 packing knapsack: Change basic code
  (use "git rebase --edit-todo" to view and edit)
You are currently editing a commit during a rebase.
  (use "git commit --amend" to amend the current commit)
  (use "git rebase --continue" once you are satisfied with your changes)

nothing to commit, working tree clean


mm@DESKTOP MINGW64 ~/Desktop/Go-oh/git-training (detached HEAD|REBASE-i 2/13)
$ git rebase --continue
Successfully rebased and updated detached HEAD.


//'git rebase --continue' 시 원래대로 복귀
$ git status
HEAD detached at upstream/dev
nothing to commit, working tree clean


$ git shortlog
Taeung Song (13):
      Add README file
      수정수정수정              //이전과 달리 두 번째 커밋이 수정됨
      packing knapsack: Basic code solving this question
      packing knapsack: Change basic code
      packing knapsack: Rename packing_knapsack to pack_knapsack
      packing knapsack: Input & Output
      packing knapsack: Add test script
      packing knapsack: Add test script generator
      packing knapsack: Implement code to solve this question
      test git-pull-request
      New version git-training
      Add v3 PDF
```