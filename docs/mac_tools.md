# Tools

## ffmpeg video recording

```bash
ffmpeg -f avfoundation -list_devices true -i ""

ffmpeg -f avfoundation -i "<screen device index>:<audio device index>" output.mkv

ffmpeg -f avfoundation -r 30 -s "1280x720" -i "2" out.mkv

ffmpeg -f avfoundation -r 30 -i "2" out.mkv

#reduce video size

ffmpeg -i input.mp4 -vcodec libx265 -crf 28 output.mp4

ffmpeg -i input.mp4 -vcodec h264 -acodec aac output.mp4

ffmpeg -i input.mp4 -vcodec libx265 -acodec aac -crf 23 output.mp4
```

## miss_hit (here)[https://github.com/florianschanda/miss_hit]

To analyse one or more files:

```bash
mh_style my_file.m
```

It is possible to also style-check and fix code embedded inside Simulink® models. To do you need to use a special command-line flag. Once the feature is stable enough, this flag will be removed.

```bash
mh_style --fix initEnv.m
```

To analyse all files in a directory tree:
```bash
mh_style src/
```

## macOS

update all the softwares (from apple/macAppStore?)
```bash
softwareupdate --all --install --force
```
