FFMPEG
======

## Config

keyint is computed as follows:

```
keyint = fps * secs (max 4 su twitch)
```

## Example

```bash
docker rm -f ffmpeg

docker run \
  --name ffmpeg \
  -v x11tmp:/tmp/.X11-unix \
  brugnara/ffmpeg \
  -y -an \
  -f x11grab \
  -video_size 1920x1080 \
  -framerate 30 \
  -i :8 \
  -preset ultrafast \
  -c:v libx264 \
  -x264-params keyint=60:scenecut=0 \
  -f flv \
  rtmp://live-mil.twitch.tv/app/$TWITCH_TOKEN
```
