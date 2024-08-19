## Git

Remove all merged and not mine branches
```bash
git branch -d `git for-each-ref --exclude="refs/remotes/" --format=' %(authorname) %09 %(refname)' --sort=authorname --merged | egrep -v "(^\*|main|master|accept|develop|HEAD|tags)" | egrep -v "(Vincent Radstake|vincent-paqt)"`
```
Return error, kan de branches niet vinden. 
