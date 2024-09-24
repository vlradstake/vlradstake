## Git

Remove all merged and not mine branches
```bash
git branch -d `git for-each-ref --exclude="refs/remotes/" --format=' %(authorname) %09 %(refname)' --sort=authorname --merged | egrep -v "(^\*|main|master|accept|develop|HEAD|tags)" | egrep -v "(Vincent Radstake|vincent-)" | awk '{print $NF}' | sed 's|refs/heads/||' | awk '{print}' ORS=' '`
```

Returns all merged branches and exclude remote
```bash
git for-each-ref --exclude="refs/remotes/" --format=' %(authorname) %09 %(refname)' --sort=authorname --merged
```
Remove default branches or tags
```bash
egrep -v "(^\*|main|master|accept|develop|HEAD|tags)"
```

Remove branches owned by user
```bash
egrep -v "(Vincent Radstake|vincent-)"
```

Extracts the last field (refs/heads/...) from each line.
```bash
awk '{print $NF}'
```

Removes the refs/heads/ prefix, leaving just the branch names.
```bash
sed 's|refs/heads/||'
```

Convert to oneline so git branch -d understands it
```bash
awk '{print}' ORS=' '`
```
