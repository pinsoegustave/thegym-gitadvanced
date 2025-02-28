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