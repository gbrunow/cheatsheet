# Git

## Change author of all commits
See [Changing author info](https://help.github.com/articles/changing-author-info/)
Run:
```
git filter-branch --env-filter -f '
CORRECT_NAME="Guilherme Brunow"
CORRECT_EMAIL="gbrunow@outlook.com"
export GIT_COMMITTER_NAME="$CORRECT_NAME"
export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
export GIT_AUTHOR_NAME="$CORRECT_NAME"
export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
' --tag-name-filter cat -- --branches --tags
```
Then:
```
git push --force --tags origin 'refs/heads/*'
```
