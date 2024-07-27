# Required softwares

* [FFmpeg](https://ffmpeg.org/download.html#build-windows)
* [VirtualDub2](https://sourceforge.net/projects/vdfiltermod/) (optional).

# Steps

* Add ffmpeg to path
* Browse to folder containing the video file and the external subtitle file

It takes too long to create directly in 1 pass a GIF with optimized palette and subtitles.

## Lossless H264

`ffmpeg.exe -i "The.Office.US.S01E01.Pilot.720p.mkv" -ss 00:13:33 -to 00:13:49 -vf fps=10,scale=640:-1:flags=lanczos,subtitles="The.Office.US.S01E01.Pilot.720p_track3_\[eng\].srt" -acodec copy -vcodec libx264 -preset veryslow -qp 0 "mixed_berry(truely lossless).mp4"`

where
- `-ss` seeks to the specified timestamp start, `-t` specifies the duration, `-to` defines the end of the segment
For example, "-ss 60 -t 10" is equivalent to "ss 60 -to 70" to ut the input video from 60s to 70s.
See [FFmpeg documentation](https://trac.ffmpeg.org/wiki/Seeking) for a reason to put seeking options after -i (basically, the seeking is more accurate and the timestamps in the subtitle file do not need to be changed).
- `-vf` stands for video filters
- `fps=10` changes the framerate to 10 frames per second
- `scale=640:-1:flags=lanczos` resizes the video to a width of 640 pixels; -1 automatically computes the height to maintain the original aspect ratio and flags specifies the scaling algorithm (see https://ffmpeg.org/ffmpeg-scaler.html for scaler algorithms).
- `subtitles` takes an external .srt file and draw its subtitles on the output video

## Visually lossless H264 (gives decent .mp4 file size)

`ffmpeg.exe -i "The.Office.US.S01E01.Pilot.720p.mkv" -ss 00:13:33 -to 00:13:49.5 -vf fps=10,scale=640:-1:flags=lanczos,subtitles="The.Office.US.S01E01.Pilot.720p_track3_\[eng\].srt" -acodec copy -vcodec libx264 -preset veryslow -crf 17 "mixed_berry(visually lossless).mp4"`

## Gif (using one of the .mp4 files created above as input)

`ffmpeg.exe -i "mixed_berry(visually lossless).mp4" -vf split[s0][s1];[s0]palettegen=stats_mode=single[p];[s1][p]paletteuse=new=1 "mixed berry (with palettes).gif"`

# Reference links

* [GIPHY Engineering - How to make GIFs with FFmpeg](https://engineering.giphy.com/how-to-make-gifs-with-ffmpeg/)
* [Superuser - How do I convert a video to GIF using ffmpeg, with reasonable quality?](https://superuser.com/questions/556029/how-do-i-convert-a-video-to-gif-using-ffmpeg-with-reasonable-quality)
* [FFmpeg filters](https://ffmpeg.org/ffmpeg-filters.html#crop)
* [Baeldung - How to crop and Resize a Video Using FFmegp](https://www.baeldung.com/linux/ffmpeg-crop-resize-video)
* [High quality GIF with FFmpeg](https://blog.pkh.me/p/21-high-quality-gif-with-ffmpeg.html)
* [Stackoverflow - FFmpeg: high quality animated GIF?](https://stackoverflow.com/questions/42980663/ffmpeg-high-quality-animated-gif)
