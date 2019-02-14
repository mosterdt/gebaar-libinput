Gebaar
=========
[![Gitter chat](https://badges.gitter.im/gebaar-libinput/community.png)](https://gitter.im/gebaar-libinput/community)

WM Independent Touchpad Gesture Daemon for libinput

_Gebaar means Gesture in Dutch_

Run any command by simply gesturing on your touchpad!

### What makes this different over the other implementations?

[libinput-gestures](https://github.com/bulletmark/libinput-gestures) and [fusuma](https://github.com/iberianpig/fusuma) both parse the output of the shell command `libinput debug-events`.

This piece of software directly interfaces with libinput to parse the events, this is both more stable and faster.

### How to install

- Grab the [latest release!](https://github.com/Coffee2CodeNL/gebaar-libinput/releases/latest)
- Move gebaard to `/usr/bin` or `~/bin`
- Run `mkdir -p ~/.config/gebaar`
- Run `nano ~/.config/gebaar/gebaard.toml` (or vim, if you like it better)
- Add the following snippet to `gebaard.toml`

```toml
[commands.swipe.three]
up = ""
down = ""
left = ""
right = ""

[commands.swipe.four]
up = ""
down = ""
left = ""
right = ""
```
- Configure commands to run per direction
- Run it in some startup file via `gebaard -b`

### Examples

**bspwm**

_~/.config/gebaar/gebaard.toml_
```toml
[commands.swipe.three]
up = "bspc node -f north"
down = "bspc node -f south"
left = "bspc node -f west"
right = "bspc node -f east"

[commands.swipe.four]
up = "rofi -show combi"
down = ""
left = "bspc desktop -f prev"
right = "bspc desktop -f next"
```

Add `gebaard -b` to `~/.config/bspwm/bspwmrc`

### State of the project

- [x] Receiving swipe events from libinput
- [ ] Receiving pinch/zoom events from libinput
- [ ] Receiving rotation events from libinput
- [x] Converting libinput events to motions
- [x] Running commands based on motions
- [x] Refactor code to be up to Release standards, instead of testing-hell

