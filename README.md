# extract-mp3
Скрипт извлечения звука в mp3 из видео в текущей директории

```bash
EXT=$1
QUALITY=$2
MONO=$3

if [ -z "$1" ]; then
  EXT=mp4
fi

if [ -z "$2" ]; then
  QUALITY=4
fi

if [ "$MONO" eq 1 ]; then
  MONO=-ac 1
fi

rename " " "_" *."$EXT"
find *."$EXT" -exec ffmpeg -threads 0 -i {} $MONO -codec:a libmp3lame -qscale:a $QUALITY {}.mp3 \;
rename ."$EXT".mp3 .mp3 *.mp3
```
