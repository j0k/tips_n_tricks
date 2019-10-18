# Git

## Multiple github accounts

- 1: [Multiple github accounts on the same computer?](https://stackoverflow.com/questions/3860112/multiple-github-accounts-on-the-same-computer)
- 2: [Push to github without password using ssh-key](https://stackoverflow.com/questions/14762034/push-to-github-without-password-using-ssh-key)

```
# create ssh keys
ssh-keygen -t rsa -C "user1@mail.xx" -f "id_rsa_user1"
ssh-keygen -t rsa -C "user1@mail.xx" -f "id_rsa_user2"
# ... ; and then add pub rsa keys into git/settings/SSH and GPG Keys

# preparation
git clone repo
git remote set-url origin git@github.com:<username>/<project>.git
ssh-agent  # for win

# main part - choose identity
ssh-add -D
ssh-add ~/.ssh/id_rsa_user_identity

# post
git commit -a -m "message"
git push
```

## Git-Pull request blocked : conflict

- 1: [merge with master](https://github.com/githubteacher/github-for-developers-sept-2015/issues/648)
- 2: [choose branch file](https://stackoverflow.com/questions/449541/how-to-selectively-merge-or-pick-changes-from-another-branch-in-git)

```
git checkout master
git pull
git checkout <branch>
git merge master
[ ... resolve any conflicts ... ]
git add [files that were conflicted]
git commit
git push
```

If you don't want to merge `file1` and want to retain the version in the current branch:

`git checkout HEAD file1`

If you don't want to merge `file2` and only want the version in `branchX`:

`git checkout branchX file2`
