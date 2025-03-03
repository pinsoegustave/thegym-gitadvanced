# Git Advanced Exercises Solutions

## Part 1: Challenge 1(Missing File fix)
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

## Challenge 2(Editing Commit History):
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

## Challenge 3(Squashing Commits)
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

## Challenge 4(Splitting a Commit)
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

## Challenge 5(Advanced Squashing)
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

