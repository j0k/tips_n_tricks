# Console

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
ffmpeg -i "concat:input1.mp4|input2.mp4|input3.mp4" -c copy output.mp4  ## as a result you will get only you first file

# Alternative way
ffmpeg -i myfile1.mp4 -c copy -bsf:v h264_mp4toannexb -f mpegts temp1.ts
ffmpeg -i myfile2.mp4 -c copy -bsf:v h264_mp4toannexb -f mpegts temp2.ts
# - now join
ffmpeg -i "concat:temp1.ts|temp2.ts" -c copy -bsf:a aac_adtstoasc output.mp4
```
