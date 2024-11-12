# mpvf

<img src="https://raw.githubusercontent.com/purarue/mpvf/master/.github/demo.gif">

Interface to select a `youtube-dl` format for streaming [stuff](https://ytdl-org.github.io/youtube-dl/supportedsites.html) with `mpv`.

If you select a format with video only, automatically adds 'bestaudio' to the format.

```
Usage: mpvf URL [OPTION]...
Interface to select a youtube-dl format for streaming stuff with mpv.

Pass the URL to stream from as the first argument.
Additional options/arguments are passed onto mpv.

You can set the MPVF_DL environment variable to download
the selected format code instead, like:
MPVF_DL=1 mpvf https://... [youtube-dl OPTION...]
```

You can set the `MPVF_PICKER` environment variable to use [`dmenu`](https://tools.suckless.org/dmenu/)/[`rofi`](https://github.com/davatorium/rofi) instead of [`fzf`](https://github.com/junegunn/fzf):

```bash
export MPVF_PICKER=rofi
mpvf 'https://...'
export MPVF_PICKER=dmenu
mpvf 'https://...'
```

### Installation

Dependencies: [`mpv`](https://mpv.io/), [`youtube-dl`](https://ytdl-org.github.io/youtube-dl/index.html), [`fzf`](https://github.com/junegunn/fzf) (or specify `dmenu`/`rofi` as alternative)

Install each dependency if not already installed and then [download/copy `mpvf` to somewhere on your `$PATH`](#manual-install)

Could also use [`basher`](https://github.com/basherpm/basher):

```bash
basher install purarue/mpvf
```

### Notes

If you want to stream just the audio, you can select the audio format, or pass the `--no-video` `mpv` flag.

I've _further_ wrapped this script as well:

- bound to different keybinds:
  - [grab URL from my clipboard and stream using `mpvf`](https://purarue.xyz/d/stream-media?redirect)
  - or, grab the URL and [just stream audio](https://purarue.xyz/d/stream-audio?redirect)
  - or, grab the URL and [stream video](https://purarue.xyz/d/stream-corner?redirect), stickying the video in the bottom right of the screen ('picture in picture'-like), using [this](https://purarue.xyz/d/i3-picture-in-picture?redirect)
  - have other related variations; to grab the URL and [stream at different resolutions](https://github.com/purarue/dotfiles/blob/9da260bd6610dbbe5ff90b6bea54cfba48bd505a/.config/shortcuts.toml#L509-L562), often called from my RSS reader
- [`twitch`](https://github.com/purarue/dotfiles/blob/2cf8b8d6e5901e3a099cfafb925a72ba1e40504a/.local/share/shortcuts/twitch-stream): streams a twitch stream using `mpvf`. See [this blog post](https://purarue.xyz/x/blog/how-i-watch-twitch/) for more context.
- [`mediaproxyvideo`](https://github.com/purarue/vps/blob/11df5cba6b9d7016b42b817de48e3b16f5ce9ecb/bin/mediaproxyvideo): mostly a copy of `mpvf`, which prompts me to select a format, `ssh`'s onto my server, `youtube-dl`/`ffmpeg`'s that video onto my server, and copies the public link its hosted on onto my clipboard.

### Manual Install

```sh
wget https://github.com/purarue/mpvf/raw/refs/heads/master/mpvf
chmod +x ./mpvf
sudo mv ./mpvf /usr/bin/
```
