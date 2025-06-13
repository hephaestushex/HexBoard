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

# June 10th: PCB Design

With all the hardware choices out of the way, I started designing the schematic and PCB.

I downloaded some libraries and setup the key switch matrix

![image](https://github.com/user-attachments/assets/0d92764f-4ae7-431d-a7da-f7349d7ad8c9)

my switch matrix.

I plan on making this a reversible matrix, so its only one half.

I then decided to do per key RGB, so I setup that too.

![image](https://github.com/user-attachments/assets/24aa80e7-8735-4e8a-92e7-05aad1fc42ae)

Its much simpler.

From there I wired up the microcontoller and battery

![image](https://github.com/user-attachments/assets/7d37419a-08d0-4712-98bf-d9702e920a83)

With that out of the way, I started on the PCB, which was relatively easy.

![image](https://github.com/user-attachments/assets/a6eb77c2-e36e-438c-b72a-c7d290030d14)

This is the location I settled on.

**Total time spent: 3h**

# June 11th: PCB Routing

I used @cheyao's reversible sk6812 mini LED footprint, and positioned those and the leds.

I then wired all of them up.

![image](https://github.com/user-attachments/assets/4b638ea5-9d50-4327-b50f-b55a7c366fd0)

I don't like the wiring towards the MCU, so I'll probably fix it tomorrow.

I couldn't decide on the mcu footprint, so I'm still working on it.
For now I'm using this footprint used in the ergonaut one
![image](https://github.com/user-attachments/assets/5751c0f1-2f79-4903-9072-218c6fd8a79a)

Also it appears that a reversible footprint does not exist for the ks-33 so looks like I'm making two halves.

After all of that, this is the final pcb for today.

![image](https://github.com/user-attachments/assets/7817c68c-8ab5-4d6f-bf7c-76deb19cc19d)

**Total time spent: 1.5h**

# June 12th: Rerouting + New PCB Footprint

I started off by realizing I probably can't SMD solder, so I created this footprint, using the XIAO nRF52840 DIP as a base and added the pads from the ergonaut one footprint.

![image](https://github.com/user-attachments/assets/2b36330c-b2b4-4d3a-a722-a559c852b72d)

The holes are so that I can use the soldering method used in the ergonaut one.

From, there I positioned the switch and battery connector.

![image](https://github.com/user-attachments/assets/90affe04-5129-4716-a9d5-7b28251c5b45)

The battery connector is simply two holes for two wires.

I then placed some mounting holes, two in the left half and one on the right half,
and finally one in the thumb cluster

![image](https://github.com/user-attachments/assets/d47b2d3f-4e1e-4b6d-a3db-8b8f16a62ef7)

Finally, the board outline and its time to reroute, this time beautifully.

I had to shuffle around some parts, replace a few footprints. I also decided to nix the leds, because a, I have no idea how to smd solder, and b, soldering 144 smd pins is too much.

This is the result

![image](https://github.com/user-attachments/assets/89b443ef-c9ea-4c97-8e3a-79b91d6fb3e3)

![image](https://github.com/user-attachments/assets/f0f5bb66-567c-4e7d-9d23-c1aaf050d02a)

![image](https://github.com/user-attachments/assets/56dfecd5-12ee-4ef5-8a7a-85a0fabb0381)

I exported that, then flipped it over and rerouted

![image](https://github.com/user-attachments/assets/ed8a0f7d-0960-41bd-b8ad-d7121ce3a323)

![image](https://github.com/user-attachments/assets/a2a0b1d6-158d-4293-bd3b-ddf2333659e5)

the cost comes out to $8.50 per pcb.

To check if I'm still under the limit, I decided to put together the BOM.

![image](https://github.com/user-attachments/assets/38ddc7fa-2ec7-444d-9603-c86e2df056de)

I sourced everything from aliexpress except the pcb and case (not on yet since I have no idea how much filament it needs)

I also made the BOM in table format in the README.md

**Total time spent: 4h**

# June 13th: Case Design and PCB Redesign

I started to design the case, when I realized that my ergonomic setup wouldn't work with Keyboard Layout editor, as apparently it can't handle eighth units.
So I'm stuck designing my own plate. 

When I hopped into kicad, I realized that my thumb cluster was not properly designed, so I basically redid the pcb, this time capturing the measurements necessary. This also helped me reduce the number of vias I used, making it cheaper!

## Right Half

![image](https://github.com/user-attachments/assets/23a82d75-d99d-4242-8e66-74ee17efdfb8)

## Left Half

![image](https://github.com/user-attachments/assets/2a403127-e039-4e2c-b230-db6b1c1b9b47)

I also redid the cost calculations with the new pcbs, but it didnt change.

Now, I can start with the case/plate.







