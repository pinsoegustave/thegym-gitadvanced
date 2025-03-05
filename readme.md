# Git Advanced Exercises Solutions

## Part 1: Refining Git History
### Challenge 1(Missing File fix)
```Ituzes-iMac:thegym-gitadvanced gymituze$ touch test{1..4}.md
git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create thirdItuzes-iMac:thegym-gitadvanced gymituze$ git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create third and fourth files"[master 9575e39] chore: Create initial file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
Ituzes-iMac:thegym-gitadvanced gymituze$ git add test2.md && git commit -m "chore: Create another file"
[master 7209072] chore: Create another file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
Ituzes-iMac:thegym-gitadvanced gymituze$ git add test3.md && git commit -m "chore: Create third and fourth files"
[master 42ca4e1] chore: Create third and fourth files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
Ituzes-iMac:thegym-gitadvanced gymituze$ git add test4.md
Ituzes-iMac:thegym-gitadvanced gymituze$ git commit -m "chore: File 4 addition"
[master 267a47c] chore: File 4 addition
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md
Ituzes-iMac:thegym-gitadvanced gymituze$ git push origin master
Counting objects: 9, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (8/8), done.
Writing objects: 100% (9/9), 872 bytes | 872.00 KiB/s, done.
Total 9 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), done.
To https://github.com/pinsoegustave/thegym-gitadvanced.git
   dcc74b6..267a47c  master -> master
Ituzes-iMac:thegym-gitadvanced gymituze$ 
```

### Challenge 2(Editing Commit History):
```isaac2@LEXs-MacBook-Air thegym-gitadvanced % git rebase -i HEAD~2
Stopped at 267a47c...  chore: Create another file
You can amend the commit now, with

  git commit --amend 

Once you are satisfied with your changes, run

  git rebase --continue

isaac2@LEXs-MacBook-Air thegym-gitadvanced % git commit --amend  
[detached HEAD f40cb40] chore: Create another file
 Author: Gym Ituze <ntwalimudasubirag@gmail.com>
 Date: Fri Feb 28 15:28:32 2025 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md
isaac2@LEXs-MacBook-Air thegym-gitadvanced % git rebase --continue
Successfully rebased and updated refs/heads/master.
isaac2@LEXs-MacBook-Air thegym-gitadvanced % 
```

### Challenge 3(Squashing Commits)
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git rebase -i  HEAD~5
Successfully rebased and updated refs/heads/master.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git rebase -i  HEAD~6
[detached HEAD 85afe0a] chore: Create initial filee
 Author: Gym Ituze <ntwalimudasubirag@gmail.com>
 Date: Fri Feb 28 15:27:01 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/master.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git rebase -i HEAD~6
Successfully rebased and updated refs/heads/master.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 4(Splitting a Commit)
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git rebase -i 1c7c0df
The previous cherry-pick is now empty, possibly due to conflict resolution.
If you wish to commit it anyway, use:

    git commit --allow-empty

Otherwise, please use 'git rebase --skip'
interactive rebase in progress; onto 1c7c0df
Last commands done (5 commands done):
   pick 4d25669 Part 1: Challenge 3
   pick 9575e39 chore: Create initial file
  (see more in file .git/rebase-merge/done)
Next commands to do (4 remaining commands):
   pick 7209072 chore: Create another file
   edit 42ca4e1 chore: Create third and fourth files
  (use "git rebase --edit-todo" to view and edit)
You are currently rebasing branch 'master' on '1c7c0df'.
  (all conflicts fixed: run "git rebase --continue")

nothing to commit, working tree clean
Could not apply 9575e39... chore: Create initial file
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git reset --soft 1c7c0df
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git reset test4.md
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "Create third file"
[detached HEAD a0855c1] Create third file
 1 file changed, 74 insertions(+), 1 deletion(-)
 rewrite readme.md (100%)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git reset test4.md
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "Create fourth file"
interactive rebase in progress; onto 1c7c0df
Last commands done (5 commands done):
   pick 4d25669 Part 1: Challenge 3
   pick 9575e39 chore: Create initial file
  (see more in file .git/rebase-merge/done)
Next commands to do (4 remaining commands):
   pick 7209072 chore: Create another file
   edit 42ca4e1 chore: Create third and fourth files
  (use "git rebase --edit-todo" to view and edit)
You are currently editing a commit while rebasing branch 'master' on '1c7c0df'.
  (use "git commit --amend" to amend the current commit)
  (use "git rebase --continue" once you are satisfied with your changes)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test4.md

nothing added to commit but untracked files present (use "git add" to track)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add test4.md
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "Create fourth file"
[detached HEAD 69a2ec9] Create fourth file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git log --onefile
fatal: unrecognized argument: --onefile
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git log --oneline
69a2ec9 (HEAD) Create fourth file
a0855c1 Create third file
1c7c0df chore: Create third and fourth files
85afe0a chore: Create initial filee
dcc74b6 add readme
f5fedd1 Delete all
5ee9077 Adding test 4 file
4061313 chore: Create third and fourth files
16129c3 chore: Create another file
4325f3e chore: Create initial file
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 5(Advanced Squashing)
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git rebase -i HEAD~6
[detached HEAD 10b3faf] Create third and fourth file
 Date: Mon Mar 3 15:50:55 2025 +0200
 2 files changed, 74 insertions(+), 1 deletion(-)
 rewrite readme.md (100%)
 create mode 100644 test4.md
Successfully rebased and updated detached HEAD.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 6(Dropping a Commit)
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "Unwanted commit"
[master 1915a89] Unwanted commit
 1 file changed, 14 insertions(+)
 create mode 100644 unwanted.txt
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git rebase -i
Successfully rebased and updated refs/heads/master.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git log --oneline
1915a89 (HEAD -> master) Unwanted commit
6481c5f (origin/master, origin/HEAD) Merge branch 'master' of https://github.com/pinsoegustave/thegym-gitadvanced
4d25669 Part 1: Challenge 3
9068135 Part 1: Challenge 2
1601f3e readme: part 1 challenge
db28a96 chore: Create another file
1c7c0df chore: Create third and fourth files
85afe0a chore: Create initial filee
b11d68c readme: part 1 challenge
267a47c chore: File 4 addition
42ca4e1 chore: Create third and fourth files
7209072 chore: Create another file
9575e39 chore: Create initial file
dcc74b6 add readme
f5fedd1 Delete all
5ee9077 Adding test 4 file
4061313 chore: Create third and fourth files
16129c3 chore: Create another file
4325f3e chore: Create initial file
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git reset --hard 1915a89
HEAD is now at 1915a89 Unwanted commit
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git reset --hard HEAD~1
HEAD is now at 1d77f33 Part 1: Challenge 5
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 7(Reordering Commits)
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git rebase -i
Successfully rebased and updated refs/heads/master.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 8(Cherry-Picking Commits)
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch ft/branch
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/branch
Switched to branch 'ft/branch'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ touch test5.md
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "Implemented test 5"
[ft/branch 32f9ccc] Implemented test 5
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git log --oneline
32f9ccc (HEAD -> ft/branch) Implemented test 5
7eb4c3f (master) Part 1 Challenge 7
a70b082 (origin/master, origin/HEAD) Merge commit '0215c352'
0215c35 Part 1: Challenge 6
1d77f33 Part 1: Challenge 5
ae9c95f : Create third and fourth files
18cf29d Part 1: Challenge 4
10b3faf Create third and fourth file
6481c5f Merge branch 'master' of https://github.com/pinsoegustave/thegym-gitadvanced
4d25669 Part 1: Challenge 3
1c7c0df chore: Create third and fourth files
9068135 Part 1: Challenge 2
1601f3e readme: part 1 challenge
db28a96 chore: Create another file
85afe0a chore: Create initial filee
b11d68c readme: part 1 challenge
267a47c chore: File 4 addition
42ca4e1 chore: Create third and fourth files
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git cherry-pick 32f9ccc
[master 3b2b55f] Implemented test 5
 Date: Mon Mar 3 17:05:39 2025 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 9(Visualizing Commit History<Bonus>)
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git log --graph
* commit 90799b6b5ce1800508e5b810b410e0990a51e3af (HEAD -> master)
| Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| Date:   Mon Mar 3 17:11:48 2025 +0200
| 
|     Part 1 Challenge 8
| 
* commit 3b2b55f740ccfc74e588ffbb9b22270361785f13
| Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| Date:   Mon Mar 3 17:05:39 2025 +0200
| 
|     Implemented test 5
| 
* commit 7eb4c3fab0e2da6b3d2d3c6946ccccf6c0e14aaf
| Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| Date:   Mon Mar 3 16:49:13 2025 +0200
| 
|     Part 1 Challenge 7
|   
*   commit a70b08284f40cb009f6e1fde21a08df9056188ce (origin/master, origin/HEAD)
|\  Merge: 6481c5f 0215c35
| | Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| | Date:   Mon Mar 3 16:46:03 2025 +0200
| | 
| |     Merge commit '0215c352'
| | 
| * commit 0215c352d201ac8924f6b1997c0a8835cdfd0f2f
| | Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| | Date:   Mon Mar 3 16:36:40 2025 +0200
| | 
| |     Part 1: Challenge 6
| | 
| * commit 1d77f33a597e61c2aa5d90c67ff402765ec8daf8
| | Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| | Date:   Mon Mar 3 16:10:20 2025 +0200
| | 
| |     Part 1: Challenge 5
| | 
| * commit ae9c95ff4bf083eaab033204dd0dca5c3244223a
| | Author: Gym Ituze <ntwalimudasubirag@gmail.com>
| | Date:   Fri Feb 28 15:27:11 2025 +0200
| | 
| |     : Create third and fourth files
| | 
| * commit 18cf29deb9bf6bd9137fa76bcf6be4c76cb10904
| | Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| | Date:   Mon Mar 3 15:54:08 2025 +0200
| | 
| |     Part 1: Challenge 4
| | 
| * commit 10b3fafa91eb17d1030d7f992908ab50ac489c01
| | Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| | Date:   Mon Mar 3 15:50:55 2025 +0200
| | 
| |     Create third and fourth file
| |   
* |   commit 6481c5f8f471b33ce09ac5eec49af4e759868097
|\ \  Merge: 4d25669 b11d68c
| | | Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| | | Date:   Mon Mar 3 15:13:02 2025 +0200
| | | 
| | |     Merge branch 'master' of https://github.com/pinsoegustave/thegym-gitadvanced
| | | 
| * | commit b11d68c4bb29c15ed488332f44eeb70aea07427c
| | | Author: Gym Ituze <ntwalimudasubirag@gmail.com>
| | | Date:   Fri Feb 28 15:30:21 2025 +0200
| | | 
| | |     readme: part 1 challenge
| | | 
| | Date:   Mon Mar 3 16:10:20 2025 +0200
| | 
| |     Part 1: Challenge 5
| | 
| * commit ae9c95ff4bf083eaab033204dd0dca5c3244223a
| | Author: Gym Ituze <ntwalimudasubirag@gmail.com>
| | Date:   Fri Feb 28 15:27:11 2025 +0200
| | 
| |     : Create third and fourth files
| | 
| * commit 18cf29deb9bf6bd9137fa76bcf6be4c76cb10904
| | Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| | Date:   Mon Mar 3 15:54:08 2025 +0200
| | 
| |     Part 1: Challenge 4
| | 
| * commit 10b3fafa91eb17d1030d7f992908ab50ac489c01
| | Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| | Date:   Mon Mar 3 15:50:55 2025 +0200
| | 
| |     Create third and fourth file
| |   
* |   commit 6481c5f8f471b33ce09ac5eec49af4e759868097
|\ \  Merge: 4d25669 b11d68c
| | | Author: pinsoegustave <ntwalimudasubirag@gmail.com>
| | | Date:   Mon Mar 3 15:13:02 2025 +0200
| | | 
| | |     Merge branch 'master' of https://github.com/pinsoegustave/thegym-gitadvanced
| | | 
| * | commit b11d68c4bb29c15ed488332f44eeb70aea07427c
| | | Author: Gym Ituze <ntwalimudasubirag@gmail.com>
| | | Date:   Fri Feb 28 15:30:21 2025 +0200
| | | 
| | |     readme: part 1 challenge
| | | 
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 10(Understanding Reflogs <Bonus>);
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git reflog
394c1fe (HEAD -> master) HEAD@{0}: commit: Part 1 Challenge 9
90799b6 HEAD@{1}: commit: Part 1 Challenge 8
3b2b55f HEAD@{2}: cherry-pick: Implemented test 5
7eb4c3f HEAD@{3}: checkout: moving from ft/branch to master
32f9ccc (ft/branch) HEAD@{4}: commit: Implemented test 5
7eb4c3f HEAD@{5}: checkout: moving from master to ft/branch
7eb4c3f HEAD@{6}: commit: Part 1 Challenge 7
a70b082 (origin/master, origin/HEAD) HEAD@{7}: rebase (finish): returning to refs/heads/master
a70b082 (origin/master, origin/HEAD) HEAD@{8}: rebase (start): checkout refs/remotes/origin/master
a70b082 (origin/master, origin/HEAD) HEAD@{9}: commit (merge): Merge commit '0215c352'
6481c5f HEAD@{10}: checkout: moving from 0215c352d201ac8924f6b1997c0a8835cdfd0f2f to master
0215c35 HEAD@{11}: checkout: moving from master to 0215c35
6481c5f HEAD@{12}: checkout: moving from 6481c5f8f471b33ce09ac5eec49af4e759868097 to master
6481c5f HEAD@{13}: checkout: moving from master to 6481c5f8f471b33ce09ac5eec49af4e759868097
6481c5f HEAD@{14}: checkout: moving from 0215c352d201ac8924f6b1997c0a8835cdfd0f2f to master
0215c35 HEAD@{15}: checkout: moving from master to 0215c35
6481c5f HEAD@{16}: checkout: moving from master to master
6481c5f HEAD@{17}: checkout: moving from 6481c5f8f471b33ce09ac5eec49af4e759868097 to master
6481c5f HEAD@{18}: checkout: moving from master to 6481c5f8f471b33ce09ac5eec49af4e759868097
6481c5f HEAD@{19}: checkout: moving from 0215c352d201ac8924f6b1997c0a8835cdfd0f2f to master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

## Part 2: Branching Basics
### Challenge 1: Feature Branch Creation
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch ft/new-feature
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/new-feature
Switched to branch 'ft/new-feature'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 2: Working on the Feature Branch
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/new-feature
Switched to branch 'ft/new-feature'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "Implemented core functionality for new feature"
[ft/new-feature 75d78fe] Implemented core functionality for new feature
 1 file changed, 5 insertions(+)
 create mode 100644 feature.txt
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 3: Switching Back and Making More Changes
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "Updated project readme"
[master 1cc4b94] Updated project readme
 1 file changed, 14 insertions(+)
 create mode 100644 read.txt
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 4: Local vs. Remote Branches
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git reflog
f9f5c71 (HEAD -> ft/new-feature) HEAD@{0}: checkout: moving from master to ft/new-feature
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git remote -v
origin  https://github.com/pinsoegustave/thegym-gitadvanced.git (fetch)
origin  https://github.com/pinsoegustave/thegym-gitadvanced.git (push)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch
  ft/branch
  ft/new-feature
* master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/new-feature
Switched to branch 'ft/new-feature'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git status
On branch ft/new-feature
nothing to commit, working tree clean
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 4 commits.
  (use "git push" to publish your local commits)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git merge ft/new-feature
Merge made by the 'recursive' strategy.
 feature.txt | 5 +++++
 1 file changed, 5 insertions(+)
 create mode 100644 feature.txt
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git push origin master
Enumerating objects: 19, done.
Counting objects: 100% (19/19), done.
Delta compression using up to 4 threads
Compressing objects: 100% (17/17), done.
Writing objects: 100% (17/17), 5.18 KiB | 2.59 MiB/s, done.
Total 17 (delta 9), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (9/9), completed with 1 local object.
To https://github.com/pinsoegustave/thegym-gitadvanced.git
   26152cf..827b611  master -> master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$
```

