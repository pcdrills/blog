---
title: Fix Stuttering Audio in Kali Virtual Machine
date: 2026-10-10 12:25:00 +60
image: https://i.postimg.cc/8cT5ZH5V/kali-audio-problem.png
categories: [Tutorials, Windows]
tags: [kali, vm, linux]
summary: Fix Stuttering Audio in Kali Virtual Machine on windows VMWare
---

## Introduction

Normally this should not happen but is usually caused by jittery drivers. In a VM
this is most common because the device is emulated.
you can usually fix this problem by giving more headroom in the alsa device
ringbuffer.
You need to edit the WirePlumber configuration as follows (since 0.5, the older 0.4 version
uses lua scripts for configuration):

---

```bash
mkdir -p ~/.config/wireplumber/wireplumber.conf.d/
cd ~/.config/wireplumber/wireplumber.conf.d
```
Then make `~/.config/wireplumber/wireplumber.conf.d/50-alsa-config.conf` in an editor and
add:
```
monitor.alsa.rules = [
  {
    matches = [
      # This matches the value of the 'node.name' property of the node.
      {
        node.name = "~alsa_output.*"
      }
    ]
    actions = {
      # Apply all the desired node specific settings here.
      update-props = {
        api.alsa.period-size   = 1024
        api.alsa.headroom      = 8192
      }
    }
  }
]
```
Afterwards, restart everything via `systemctl --user restart wireplumber pipewire pipewire-pulse`

When running inside a VM, also disable the Firefox speech dispatch as
explained [here](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Performance-tuning#firefox).

---

## Conclusions

Source of this fix is from this [here](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Troubleshooting?anubis_answer=peach)

---

Bye for now. 

---

Follow | [Facebook Page](https://facebook.com/pcdrillsofficial/) | [Telegram Channel](https://t.me/pcdrills/) | [Twitter Handle](https://twitter.com/pc_drills) | [Youtube Channel](https://youtube.com/pcdrills)

