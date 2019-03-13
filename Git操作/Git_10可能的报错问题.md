## 一、git push报错
    
- 如果遇到以下错误，先git pull 在git push
```
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```



- git push 如果出现以下报错，则用git push -u origin 分支名
```
fatal: The current branch dev has no upstream branch.
       To push the current branch and set the remote as upstream, use
                git push --set-upstream origin dev
```