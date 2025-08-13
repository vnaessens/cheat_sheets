# Required softwares

* [FFmpeg](https://ffmpeg.org/download.html#build-windows)

# 

`ffmpeg -framerate 25 -start_number 1650 -i _DSF%04d.jpg -vf scale=-1:2160 -vcodec libx264 -crf 21 -r 25 -pix_fmt yuv422p10le timelapse.mp4`

where
- `-framerate 25` specifies a frame rate of 25 fps
- `-r 25`sets the GOP size to 25
- `-start_number 1650 -i _DSF%04d.jpg`specifies the pattern of the image filenames as well as the number of the first frame
- `-vf` stands for video filters
- `scale=-1:2160` resizes the video to a height of 2160 pixels; -1 automatically computes the width to maintain the original aspect ratio (see https://ffmpeg.org/ffmpeg-scaler.html to set the scaling algorithm)
- `-vcodec libx264 -crf 21` encodes using x264 codec with a CRF equal to 21
- `-pix_fmt yuv422p10le` sets the pixel format (choose among yuv420p for 8-bit 4:2:0, yuv422p for 8-bit 4:2:2, yuv420p10le for 10-bit 4:2:0 and yuv422p10le for 10-bit 4:2:2)
