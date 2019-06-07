# Console

## Git

### Multiple github accounts

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

## Media

### concat video using ffmpeg

- 1: [How to concatenate two MP4 files using FFmpeg?](https://stackoverflow.com/questions/7333232/how-to-concatenate-two-mp4-files-using-ffmpeg)

```
# Create File List
echo file file1.mp4 >  mylist.txt
echo file file2.mp4 >> mylist.txt
echo file file3.mp4 >> mylist.txt

# Concatenate Files
ffmpeg -f concat -i mylist.txt -c copy output.mp4

# Alternative 
ffmpeg -i "concat:input1.mp4|input2.mp4|input3.mp4" -c copy output.mp4
```
