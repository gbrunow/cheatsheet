# Git

## Save user and password

```bash
git config credential.helper store
```

## Change author of all commits
See [Changing author info](https://help.github.com/articles/changing-author-info/)
(You may need to [remove previous backups](#remove-original-backup) before hand)
1. Run:
```shell
git filter-branch --env-filter '
CORRECT_NAME="Guilherme Brunow"
CORRECT_EMAIL="gbrunow@outlook.com"
export GIT_COMMITTER_NAME="$CORRECT_NAME"
export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
export GIT_AUTHOR_NAME="$CORRECT_NAME"
export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
' --tag-name-filter cat -- --branches --tags
```

2. Then:
```
git push --force --tags origin 'refs/heads/*'
```

## Change author of all commits based on commiter e-mail
See [Changing author info](https://help.github.com/articles/changing-author-info/)
(You may need to [remove previous backups](#remove-original-backup) before hand)
1. Run:
```shell
git filter-branch --env-filter '

OLD_EMAIL="gbrunow@outlook.com"
CORRECT_NAME="Guilherme Brunow Gomes"
CORRECT_EMAIL="gbrunowgomes@ua.edu"

if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```

2. Then:
```
git push --force --tags origin 'refs/heads/*'
```

## Remove Original Backup
```shell
git update-ref -d refs/original/refs/heads/master
```
