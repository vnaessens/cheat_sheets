# Required softwares

* [get_iplayer](https://github.com/get-iplayer/get_iplayer_win32/releases/)
* VPN
* [FFmpeg](https://ffmpeg.org/download.html#build-windows)

# Steps

* Turn on VPN
* Browse to BBC program and copy URL
* Retrieve program details :

`get_iplayer --ffmpeg E:\ffmpeg-4.1-win64-static\bin\ffmpeg.exe https://www.bbc.co.uk/events/evrj6q/play/ag2n6q/p08gjmtb --info --long`
* Select best qualities using --tv-quality= and --radio-quality= :

`get_iplayer --ffmpeg E:\ffmpeg-4.4.1-full_build\bin\ffmpeg.exe --tv-quality="fhd" --radio-quality="high" https://www.bbc.co.uk/iplayer/episode/p0c7bcgh/later-live-tracks-liam-gallagher-better-days-later-with-jools-holland`

Other useful options : `--raw`, `--overwrite`
