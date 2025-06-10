---
title: "HexBoard"
author: "hephaestushex"
description: "A split keyboard"
created_at: "2025-06-05"
---
# June 9th: Got some initial planning done

## Keyboard Layout

I started off by creating a keyboard layout.
Some tinkering later, this is what it looks like in Keyboard Layout Editor

![image](https://github.com/user-attachments/assets/5a9b50c7-7993-4e5d-bd34-3e296d9ea58a)

It's only one half, with no column stagger (I haven't measured my hands yet) but it would come out to a 36-key layout

![image](https://github.com/user-attachments/assets/3b07386c-ad02-4323-9ee6-886caadf7d79)

As for the keymap, I liked this one by Rico Sta. Cruz. I'll probably use QWERTY, but I like the way they navigate between layers

## Microcontroller

I initially wanted to make this keyboard wireless, considering the state of my desk

![WIN_20250609_16_52_57_Pro](https://github.com/user-attachments/assets/55d3fe5c-cc18-4169-ab99-733300c98c8e)
my desk rn... not looking good

Unfortunately, after a post on slack and some research, this isn't feasible. I could use an aliexpress clone, but apparently it's not reliable

Anyway, by this point I decided that a pi pico would be better. Ideally, usb-c, as the microUSB connectors tend to break off.

I started by looking at the Seeed Studio XIAO RP2040 board. With the split connectivity (TX/RX) pins, there is 9 more pins, which would work out for my layout.

It's tight, but it might just work.

But hold on... I found a Seeed Studio XIAO nRF52840 Board, and it is similar to the nice!nano, but so much more cheaper. The only caveat is that the battery pins are exposed by pads. A google search yielded the ergonaut one, which solves this problem by using holes and filling them with solder.

![image](https://github.com/user-attachments/assets/0204e1e2-0ba0-4668-b5dd-d3673e832baa)
location of the battery pins

![image](https://github.com/user-attachments/assets/52e0274d-b953-461a-a9d6-52d33e09bde5)
solution used in the ergonaut one

## Keyswitches

I want this keyboard to be low-profile, so I went looking for some low profile keyswitches. I ended up finding the gateron ks-33 low profile switches, which looks good.

## Miscellaneous Parts

I'll use THT diodes for the matrix, probably 1N4148 diodes.

**Total time spent: 3h**
