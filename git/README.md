# Git

## Change author of all commits
See [Changing author info](https://help.github.com/articles/changing-author-info/)
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
