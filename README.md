Package for voice over subtitles:

* with the ability to embed in video,
* audio ducking,
* dynamic voice changer for a single track. _Add **"!: voice name"** at the beginning of the subtitle line. (Applies to
  all
  subsequent ones)_

> pip install -U [PyFastDub](https://pypi.org/project/PyFastDub/) _--force-reinstall_

# Youtube support

### Youtube argument group

> pip install PyFastDub[YT]

# Subtitles translate

### Translate subtitles argument group

> pip install PyFastDub[TR]

# Usage

> python -m FastDub --help

```
usage: FastDub [-h] [-rc] [-rf CLEANUP_LEVEL] [-l LANGUAGE] [-pc PROCESS_COUNT] [-vf VIDEO_FORMAT] [-sf SUBTITLES_FORMAT]
               [-En EXCLUDE [EXCLUDE ...]] [-Eu EXCLUDE_UNDERSCORE] [-sc | --sidechain | --no-sidechain] [-sc-msl MIN_SILENCE_LEN]
               [-sc-st SILENCE_THRESH] [-sc-gdo GAIN_DURING_OVERLAY]
               [-v {microsoft irina desktop - russian,microsoft zira desktop - english united states),microsoft david desktop - english (united sta
tes,aleksandr-hq,arina,artemiy,evgeniy-eng,evgeniy-rus,lyubov,marianna,mikhail,pavel,tatiana,victoria,vitaliy,volodymyr,yuriy}]
               [-a ALIGN] [-ll LOGLEVEL] [-y | --confirm | --no-confirm] [-yt] [-ak API_KEYS [API_KEYS ...]] [-tr]
               [--rewrite-srt | --no-rewrite-srt] [-ts {alibaba,argos,baidu,bing,caiyun,deepl,google,iciba,iflytek,sogou,tencent,yandex,youdao}]   
               input

FastDub is a tool for dubbing videos by subtitle files.

options:
  -h, --help            show this help message and exit
  -rc, --remove-cache   Remove all cache files
  -rf CLEANUP_LEVEL, --cleanup-level CLEANUP_LEVEL
                        Cleanup level   0 = No removing any files
                                > 0 remove audio from video (default)
                                > 1 = remove dubbed audio if video exists
                                > 2 = reomve dubbed cache files
  -l LANGUAGE, --language LANGUAGE
                        Subtitles language (ru)
  -pc PROCESS_COUNT, --process-count PROCESS_COUNT
                        Process count to download (pass to cpu count, < 2 to disable)

Input:
  input                 Input directory/YouTube Playlist/Video URL.
  -vf VIDEO_FORMAT, --video-format VIDEO_FORMAT
                        Video format (default .mp4).
  -sf SUBTITLES_FORMAT, --subtitles-format SUBTITLES_FORMAT
                        Subtitles format (default .srt).

Audio Ducking:
  -sc, --sidechain, --no-sidechain
                        Enable audio side chain compress (ducking) (default: True)
  -sc-msl MIN_SILENCE_LEN, --min-silence-len MIN_SILENCE_LEN, --attack MIN_SILENCE_LEN
                        Minimum silence length in ms (default 100)
  -sc-st SILENCE_THRESH, --silence-thresh SILENCE_THRESH
                        Silence threshold in dB
  -sc-gdo GAIN_DURING_OVERLAY, --gain-during-overlay GAIN_DURING_OVERLAY
                        Gain during overlay in dB

Voicer:
  -v {microsoft irina desktop - russian,microsoft zira desktop - english (united states),microsoft david desktop - english (united states),aleksand
                        Youtube API key/s

Translate subtitles:
  -tr, --translate      Translate input subtitles files
  --rewrite-srt, --no-rewrite-srt
                        Rewrite input subtitles files.
                        If not, add "_" to the beginning of the original subtitle file. (default: False)
  -ts {alibaba,argos,baidu,bing,caiyun,deepl,google,iciba,iflytek,sogou,tencent,yandex,youdao}, --translate-service {alibaba,argos,baidu,bing,caiyu
n,deepl,google,iciba,iflytek,sogou,tencent,yandex,youdao}
                        Subtitle translation service. (default google)
```

**If the voice set after !: is not selected during voiceover, clear the cache with the -rc argument**

## Example

> python -m FastDub DirToDub -v "[Yuriy](https://rhvoice.su/downloads/?voice=yuriy&type=sapi)" --no-ducking -vf mkv

name is any name.

DirToDub:

- name.srt
- name.mkv
- name2.srt
- name2.mkv
- andit.srt
- andit.mkv

Then:
_name and name2 will be announced, and the results will be saved to a folder with the appropriate name._

## YT Example

> python -m FastDub https://youtu.be/DD5UKQggXTc **-yt**
> -v "[Yuriy](https://rhvoice.su/downloads/?voice=yuriy&type=sapi)"
> -l ru

## Translate Example

> python -m FastDub DirToDub -tr -ts iciba -l ru

