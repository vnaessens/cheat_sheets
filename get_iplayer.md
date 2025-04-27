# Required softwares

* [get_iplayer](https://github.com/get-iplayer/get_iplayer_win32/releases/)
* VPN
* [FFmpeg](https://ffmpeg.org/download.html#build-windows)
* [yt-dlp](https://github.com/yt-dlp/yt-dlp)

# Steps

* Turn on VPN
* Browse to BBC program and copy URL
* Retrieve program details :

`get_iplayer --ffmpeg E:\ffmpeg-4.1-win64-static\bin\ffmpeg.exe https://www.bbc.co.uk/events/evrj6q/play/ag2n6q/p08gjmtb --info --long`
* Select best qualities using --tv-quality= or --radio-quality= depending on the program type :
* Set attempts number in case of an invalid or incomplete fragment using --attempts NUMBER

`get_iplayer --ffmpeg E:\ffmpeg-4.4.1-full_build\bin\ffmpeg.exe --tv-quality="fhd" --radio-quality="high" --attempts 10 -https://www.bbc.co.uk/iplayer/episode/p0c7bcgh/later-live-tracks-liam-gallagher-better-days-later-with-jools-holland`

Other useful options : `--raw`, `--overwrite`, `--force`

**Update 03/07/2024** : Use yt-dlp.

`yt-dlp.exe -F --list-subs https://www.bbc.co.uk/iplayer/episode/m001zqvz/close`

`yt-dlp.exe --ffmpeg-location E:\ffmpeg-7.1.1-full_build\bin\ffmpeg.exe --windows-filenames --merge-output-format "mp4/mkv" --write-subs --sub-langs all --abort-on-unavailable-fragments https://www.bbc.co.uk/iplayer/episode/p0j3kydm/glastonbury-kasabian`
