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
### Challenge 5: Branch Deletion
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch
  ft/branch
  ft/new-feature
* master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/new-feature
error: Your local changes to the following files would be overwritten by checkout:
        readme.md
Please commit your changes or stash them before you switch branches.
Aborting
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "Clean"
[master 0d34880] Clean
 1 file changed, 1 deletion(-)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/new-feature
Switched to branch 'ft/new-feature'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git status
On branch ft/new-feature
nothing to commit, working tree clean
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch -D ft/new-feature
Deleted branch ft/new-feature (was 75d78fe).
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch
  ft/branch
* master
* master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 6: Creating a Branch from a Commit
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git reflog
b62e850 (HEAD -> master) HEAD@{0}: commit: readme: Part 2 Challenge 5
0d34880 HEAD@{1}: checkout: moving from ft/new-feature to master
75d78fe HEAD@{2}: checkout: moving from master to ft/new-feature
0d34880 HEAD@{3}: commit: Clean
d59ed8e HEAD@{4}: commit: Part 2: Challenge 4
827b611 (origin/master, origin/HEAD) HEAD@{5}: merge ft/new-feature: Merge made by the 'recursive' strategy.
f5c2961 HEAD@{6}: checkout: moving from ft/new-feature to master
75d78fe HEAD@{7}: checkout: moving from master to ft/new-feature
f5c2961 HEAD@{8}: commit: Part 2: Challenge 3
1cc4b94 HEAD@{9}: commit: Updated project readme
b76e1b4 HEAD@{10}: commit: Part 2: Challenge 2
ab56aa5 HEAD@{11}: checkout: moving from ft/new-feature to master
75d78fe HEAD@{12}: commit: Implemented core functionality for new feature
26152cf HEAD@{13}: checkout: moving from master to ft/new-feature
ab56aa5 HEAD@{14}: commit: Part 2: Challenge 1
26152cf HEAD@{15}: checkout: moving from ft/new-feature to master
26152cf HEAD@{16}: checkout: moving from master to ft/new-feature
26152cf HEAD@{17}: checkout: moving from ft/new-feature to master
f9f5c71 HEAD@{18}: checkout: moving from master to ft/new-feature
26152cf HEAD@{19}: checkout: moving from master to master
26152cf HEAD@{20}: checkout: moving from ft/new-feature to master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout -b ft/new-branch-from-commit d59ed8e
Switched to a new branch 'ft/new-branch-from-commit'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 7: Branch Merging
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git merge ft/new-branch-from-commit
Already up to date.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "new-branch: trial test"
[ft/new-branch-from-commit 05aa503] new-branch: trial test
 1 file changed, 1 insertion(+)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 4 commits.
  (use "git push" to publish your local commits)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git merge ft/new-branch-from-commit
Merge made by the 'recursive' strategy.
 test4.md | 1 +
 1 file changed, 1 insertion(+)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 8: Branch Rebasing
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch
  ft/branch
  ft/new-branch-from-commit
* master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git rebase master
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 7 commits.
  (use "git push" to publish your local commits)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git log --online
fatal: unrecognized argument: --online
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git log --oneline
346d1f4 (HEAD -> master, ft/new-branch-from-commit) readme: Part 2 Challenge 7
1d9a380 Test merging branches
05aa503 new-branch: trial test
5a7762d readme: Part 2 Challenge 6
b62e850 readme: Part 2 Challenge 5
0d34880 Clean
d59ed8e Part 2: Challenge 4
827b611 (origin/master, origin/HEAD) Merge branch 'ft/new-feature'
f5c2961 Part 2: Challenge 3
1cc4b94 Updated project readme
b76e1b4 Part 2: Challenge 2
75d78fe Implemented core functionality for new feature
ab56aa5 Part 2: Challenge 1
26152cf readme: Edit
f0a8088 Part 1 Challenge 10
394c1fe Part 1 Challenge 9
90799b6 Part 1 Challenge 8
3b2b55f Implemented test 5
7eb4c3f Part 1 Challenge 7
a70b082 Merge commit '0215c352'
0215c35 Part 1: Challenge 6
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git rebase ft/new-branch-from-commit
Current branch master is up to date.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$
```

### Challenge 9: Renaming Branches
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch
  ft/branch
  ft/new-branch-from-commit
* master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch -m ft/new-branch-from-commit ft/improved-branch-name
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch
  ft/branch
* ft/improved-branch-name
  master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 10: Checking Out Detached HEAD
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git reflog
993130f (HEAD -> master) HEAD@{0}: commit: readme: Part 2 Challenge 9
3228246 (origin/master, origin/HEAD) HEAD@{1}: checkout: moving from ft/improved-branch-name to master
346d1f4 (ft/improved-branch-name) HEAD@{2}: Branch: renamed refs/heads/ft/new-branch-from-commit to refs/heads/ft/improved-branch-name
346d1f4 (ft/improved-branch-name) HEAD@{4}: checkout: moving from master to ft/new-branch-from-commit
3228246 (origin/master, origin/HEAD) HEAD@{5}: commit: readme: Part 2 Challenge 8
346d1f4 (ft/improved-branch-name) HEAD@{6}: checkout: moving from ft/new-branch-from-commit to master
346d1f4 (ft/improved-branch-name) HEAD@{7}: rebase (finish): returning to refs/heads/ft/new-branch-from-commit
346d1f4 (ft/improved-branch-name) HEAD@{8}: rebase (start): checkout master
05aa503 HEAD@{9}: checkout: moving from master to ft/new-branch-from-commit
346d1f4 (ft/improved-branch-name) HEAD@{10}: commit: readme: Part 2 Challenge 7
1d9a380 HEAD@{11}: merge ft/new-branch-from-commit: Merge made by the 'recursive' strategy.
5a7762d HEAD@{12}: checkout: moving from ft/new-branch-from-commit to master
05aa503 HEAD@{13}: commit: new-branch: trial test
d59ed8e HEAD@{14}: checkout: moving from master to ft/new-branch-from-commit
5a7762d HEAD@{15}: commit: readme: Part 2 Challenge 6
b62e850 HEAD@{16}: checkout: moving from ft/new-branch-from-commit to master
d59ed8e HEAD@{17}: checkout: moving from master to ft/new-branch-from-commit
b62e850 HEAD@{18}: commit: readme: Part 2 Challenge 5
0d34880 HEAD@{19}: checkout: moving from ft/new-feature to master
75d78fe HEAD@{20}: checkout: moving from master to ft/new-feature
0d34880 HEAD@{21}: commit: Clean
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout 5a7762d
Note: switching to '5a7762d'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 5a7762d readme: Part 2 Challenge 6
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git switch --detach 5a7762d
HEAD is now at 5a7762d readme: Part 2 Challenge 6
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Previous HEAD position was 5a7762d readme: Part 2 Challenge 6
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

## Part 3: Advanced Workflows

### Challenge 1: Stashing Changes
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git stash
Saved working directory and index state WIP on master: f0ef1b2 readme: Part 2 Challenge 10
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git stash list
stash@{0}: WIP on master: f0ef1b2 readme: Part 2 Challenge 10
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

### Challenge 2: Retrieving Stashed Changes
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git stash list
stash@{0}: WIP on master: f0ef1b2 readme: Part 2 Challenge 10
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git stash pop
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   feature.txt

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (ad75991b655c9980ec9e79a96b1a62a7515254b3)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```
### Challenge 3: Branch Merging Conflicts(Continued)
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch
  ft/branch
  ft/improved-branch-name
* master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/improved-branch-name
M       feature.txt
Switched to branch 'ft/improved-branch-name'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "feature: edit line 7"
[ft/improved-branch-name 6bb28ac] feature: edit line 7
 1 file changed, 3 insertions(+), 1 deletion(-)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git merge improved-branch-name
merge: improved-branch-name - not something we can merge
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git merge improved-branch-name
merge: improved-branch-name - not something we can merge
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/improved-branch-name
Switched to branch 'ft/improved-branch-name'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git status
On branch ft/improved-branch-name
nothing to commit, working tree clean
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git push origin ft/improved-branch-name
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 1007 bytes | 1007.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'ft/improved-branch-name' on GitHub by visiting:
remote:      https://github.com/pinsoegustave/thegym-gitadvanced/pull/new/ft/improved-branch-name
remote: 
To https://github.com/pinsoegustave/thegym-gitadvanced.git
 * [new branch]      ft/improved-branch-name -> ft/improved-branch-name
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git merge ft/improved-branch-name
Merge made by the 'recursive' strategy.
 feature.txt | 4 +++-
 1 file changed, 3 insertions(+), 1 deletion(-)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$
```

### Challenge 4: Resolving Merge Conflicts with a Merge Tool
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git branch
  ft/branch
  ft/improved-branch-name
* master
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/improved-branch-name
M       feature.txt
Switched to branch 'ft/improved-branch-name'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "feature: edit line 7"
[ft/improved-branch-name 6bb28ac] feature: edit line 7
 1 file changed, 3 insertions(+), 1 deletion(-)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git merge improved-branch-name
merge: improved-branch-name - not something we can merge
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git merge improved-branch-name
merge: improved-branch-name - not something we can merge
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/improved-branch-name
Switched to branch 'ft/improved-branch-name'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git status
On branch ft/improved-branch-name
nothing to commit, working tree clean
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git push origin ft/improved-branch-name
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 1007 bytes | 1007.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'ft/improved-branch-name' on GitHub by visiting:
remote:      https://github.com/pinsoegustave/thegym-gitadvanced/pull/new/ft/improved-branch-name
remote: 
To https://github.com/pinsoegustave/thegym-gitadvanced.git
 * [new branch]      ft/improved-branch-name -> ft/improved-branch-name
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 2 commits.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout ft/improved-branch-name
Switched to branch 'ft/improved-branch-name'
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "Edit in feature"
[ft/improved-branch-name c8a048f] Edit in feature
 1 file changed, 4 insertions(+), 1 deletion(-)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git push origin ft/improved-branch-name
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 421 bytes | 421.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/pinsoegustave/thegym-gitadvanced.git
   6bb28ac..c8a048f  ft/improved-branch-name -> ft/improved-branch-name
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "on master: edit feature file"
[master feb145a] on master: edit feature file
 1 file changed, 4 insertions(+), 1 deletion(-)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git merge ft/improved-branch-name
Auto-merging feature.txt
CONFLICT (content): Merge conflict in feature.txt
Automatic merge failed; fix conflicts and then commit the result.
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git mergetool

This message is displayed because 'merge.tool' is not configured.
See 'git mergetool --tool-help' or 'git help config' for more details.
'git mergetool' will now attempt to use one of the following tools:
tortoisemerge emerge vimdiff nvimdiff
Merging:
feature.txt

Normal merge conflict for 'feature.txt':
  {local}: modified file
  {remote}: modified file
Hit return to start merge resolution tool (vimdiff): 
4 files to edit
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ y
bash: y: command not found
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git git add .
git: 'git' is not a git command. See 'git --help'.

The most similar command is
        init
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git add .
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "merge using mergetool"
[master 0bd4b61] merge using mergetool
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```
### Challenge 5: Understanding Detached HEAD State
```
https://circleci.com/blog/git-detached-head-state/#:~:text=git%20checkout%20feature-,What%20does%20detached%20HEAD%20mean%3F,commit%20or%20the%20remote%20repository.
``` 

### Challenge 6: Ignoring Files/Directories
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ touch .gitignore
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ echo "/tmp" > .gitignore
LEXs-MacBook-Air:thegym-gitadvanced isaac2$
```

### Challenge 7, 8: Working with tags, listing and deleting tags
```
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git tag v1.0
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git tag
v1.0
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git show
commit 8768992a1bf0e54efcedfb98d2875123d8bbe636 (HEAD -> master, tag: v1.0, origin/master, origin/HEAD)
Author: pinsoegustave <ntwalimudasubirag@gmail.com>
Date:   Fri Mar 7 14:14:14 2025 +0200

commit 8768992a1bf0e54efcedfb98d2875123d8bbe636 (HEAD -> master, tag: v1.0, origin/master, origin/HEAD)
Author: pinsoegustave <ntwalimudasubirag@gmail.com>
Date:   Fri Mar 7 14:14:14 2025 +0200

    readme: Part 3 Challenge 5

diff --git a/readme.md b/readme.md
index c2e024e..abb2ae3 100644
--- a/readme.md
+++ b/readme.md
@@ -821,8 +821,12 @@ LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git commit -m "merge using mergetool
 [master 0bd4b61] merge using mergetool
 LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
 ```
+### Challenge 5: Understanding Detached HEAD State
+```
+https://circleci.com/blog/git-detached-head-state/#:~:text=git%20checkout%20feature-,What%20does%20detached%20HEAD%20mean%3F,commit%20or%20the%20remote%20rep
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git tag show v1.0
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git tag
show
v1.0
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git tag -d v1.0
Deleted tag 'v1.0' (was 8768992)
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ git tag
show
LEXs-MacBook-Air:thegym-gitadvanced isaac2$ 
```

