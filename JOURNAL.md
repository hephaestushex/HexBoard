---
title: "HexBoard"
author: "hephaestushex"
description: "A wireless split keyboard powered by the nRF52840"
created_at: "2025-06-05"
---

# Total Time Spent: 33.5 Hours (including building)

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

Since Keyboard layout editor doesn't support eight units, I have to design my own plate, which kinda sucks.

Anyway, I tried my best to create my own plate, and this is what I go before I gave up.

![image](https://github.com/user-attachments/assets/fe06e645-7113-4172-b99c-c87bd2b66af0)

This was my first time using fusion, so it took forever, dealing with constraints, rectangular patterns and so much more.

**Total time spent: 5h**

# June 15th: Case Redesign

This clearly wasn't working, so I tried KLE again. I just ignored the warnings, and came up with this plate.

![image](https://github.com/user-attachments/assets/88bf9425-6055-40a0-b776-b9af4265666a)

its so much better, and I can properly deal with this. Obviously the plate isn't meant to be a square, so thats a tomorrow problem

**Total time spent: 30min**

# June 16th: Case Design (for real this time)

I decided to start designing the case, and it looked good!

45 mins in and this is what I have

![image](https://github.com/user-attachments/assets/b0ec192a-0ee5-4e94-97fe-0b85b12de25b)

It looks good, so I designed a cross section to see how it would mount

![image](https://github.com/user-attachments/assets/6a146765-8f7d-47d5-8987-bb61cb4cd5ce)

its way too large (2 cm), so I realized i should probably use m2 bolts instead.

Back to PCB design ... sigh

It wasn't too bad, I just made two different folders for each half. 

Here's the new folder structure

![image](https://github.com/user-attachments/assets/06859964-9a5b-4877-862a-87ad5e00881f)

A quick edit in the footprint assignment tool yielded a fixed pcb.

![image](https://github.com/user-attachments/assets/825dcc2b-ff47-450a-b3c4-fe7cec1054f9).

**Total Time spent: 1h**

# June 17th: Case Done*

I started off with some research as to the dimensions of my case. It was very boring, but eventually 
I found out that the distance between the bottom of the plate and the top of the case floor should be 4.5mm

The research led me to find out that my current hardware is good, so I just went with the m3 bolts. The heads will protrude now, but that should be fine.

The fact that the heads will protrude made me have to move the bolts to the side, which ended up looking like a sandwich mount, like this, except for the fact that the bolts will come from the top instead

![image](https://github.com/user-attachments/assets/997f571b-0c2f-4e4a-a8f4-4cf4dbae7a4a)

Heres what the bottom looks like, after redoing the pcbs, schematics, and the sketch

![image](https://github.com/user-attachments/assets/51891da7-3d22-4659-bc8b-f952fbd8aff0)

As for the top, it was as simple as copying over the outline and fixing the holes in place.

![image](https://github.com/user-attachments/assets/390a27ed-23fd-4390-a9a4-a4ca3b38c043)

The plate should be 3mm thick, with 1.2mm thick rectangles for the switch to clip onto. I didn't design these yet, as I want to do it after receiving the switches, which would allow me to experiment with mounting styles.

heres how the plate looks after a quick extrusion

![image](https://github.com/user-attachments/assets/a1d7320b-0760-4c1b-85b6-97e12b767a76)

![image](https://github.com/user-attachments/assets/f725f80f-3720-435d-9522-691700013a1f)

i still need to fillet it tho

**Total time spent: 3h**

# June 18th: Case Fully Done

I started off by redoing the extrusions, so I can create a divot.

It was time consuming, but 30 mins later I got this 

![image](https://github.com/user-attachments/assets/a8ee2c16-92da-4f33-b3be-2fdaa7f2c4a0)

You can see the parts where the switch clips to.

I also took some time to fillet the entire case.

Filleted the top plate:

![image](https://github.com/user-attachments/assets/e500f005-93e1-4fb1-8149-da8420323a92)

And the bottom case:

![image](https://github.com/user-attachments/assets/e4289b90-26a6-4a12-a6b2-7a32c964691d)

That's pretty much it for the case so I exported, both left and right.

I put the cad files in the repo, and that's all I did for today.

![image](https://github.com/user-attachments/assets/e25ca271-ca1b-44c2-ba1f-8da1ecb8f183)

**Total time spent: 1h**

# Jun 19th: Firmware Done*

Since I'm using the nRF52840, my only options for firmware are ZMK and KMK. The docs for KMK say that it has to be precompiled, and a whole bunch of nonsense that made it not worth it to use KMK. ZMK isn't any easier, but at least there's a lot of documentation for it.

I started off with Joe Scotto's tutorial, but it looked out of date, plus mine is split. So, time to delve into the docs.

It took a while to find what I needed, since the actual development of shields was put in the later sections of the docs. I pretty much installed zmk, created a new repo for it, and started creating!

## Some screenshots of the code required

![image](https://github.com/user-attachments/assets/d462e658-31e8-4060-85a4-d17c49522ca2)

![image](https://github.com/user-attachments/assets/94c5a08c-e84d-4f03-932b-98fdeebf3768)

![image](https://github.com/user-attachments/assets/71147476-1967-45b2-b465-1a98b80d24e7)

![image](https://github.com/user-attachments/assets/293cf488-ec52-4375-8d05-364de9751125)

The last image is of my keymap. For now, its pretty sparse, but I plan on filling it out fully.

an hour in, its time for building!

I sure hope that no bugs will come!

**There. were. so. many. bugs.**

The terrible part is that it takes forever for these bugs to show up, since it takes time to build.

![image](https://github.com/user-attachments/assets/d501d892-ceb1-418b-a54a-08a0cb004e09)

The first two were the initial builds, but the last three are bugs in my code.

If you noticed in my keymap, I actually used a Colemak layout. I wanted to learn colemak, so I'm taking this as an opportunity to learn it.

so while it takes time to build ...

![image](https://github.com/user-attachments/assets/6d77d858-632c-4c24-ab57-696116bff750)

im learning colemak!

![image](https://github.com/user-attachments/assets/baa33a4a-5fe9-488d-85ea-d5f1834611e3)

Finally at 1:23 it built.

![image](https://github.com/user-attachments/assets/5307670b-8329-4272-8289-455bf2fe125c)

FINALLY!!!!

Here's my colemak accuracy by the way:

![image](https://github.com/user-attachments/assets/1c013c55-3a2e-4a5a-a8de-1f271b4b5346)

That's pretty much everything I think I have to do before I submit.

I pushed the two uf2 files to github

![image](https://github.com/user-attachments/assets/1133172a-4267-4528-bce7-b6a49786aa19)

I took some time to revise the README and the BOM.

AliExpress for some reason changed the prices on me, so I have to update the prices. It also allowed me to fix items that ship later.

That looked to be pretty much everything, so I checked the website to see if I'm missing anything.

I was missing a couple of images, plus some BOM formatting. It took a while to place all the switches, so in total, about 45 mins.

![image](https://github.com/user-attachments/assets/3103e7c7-cb83-4ac8-9052-db721e69d588)

This is how it looked once I placed all of them. 

That's it, so I'm going to submit this.

**Total time spent: 3.5h**

# June 23rd: Case Redesign

I already submitted this in the slack, but I realized my case didn't have much design to it. I wanted to create a design to boost my chances of getting accepted, plus, i didn't like the look of a plain pcb.

1h 30mins in, I got this:

![image](https://github.com/user-attachments/assets/8a2e6604-523f-44e5-a332-f420dfea82ba)

I took some time to design around the xiao, but I liked this look in the end.

I meant to also add some color, so I re did the appearances close to what it would look like IRL

![image](https://github.com/user-attachments/assets/bcb9ec16-e66d-418c-be16-ea54f5ee2bbd)

After doing that, I realized I didnt like the look of the xiao board, so I added some material to hide that aswell.

It allowed me to completely hide the usb-c port 

![image](https://github.com/user-attachments/assets/de415bf9-e48a-4aec-a339-039615df3202)

And this is the final design!

![image](https://github.com/user-attachments/assets/6db31906-7faa-4de5-9ce7-1342b99e130a)

I have black and red pla filament, and this is what itll probably look like.

I also decided to take a render, and I added this to the README

![image](https://hc-cdn.hel1.your-objectstorage.com/s/v3/aa89db46a0616ceec7e96bbd6a2fd4cc0817f5ea_render.png)

From there I refactored the object and exported everything. I also took the time to colorize the case in the Bambu Slicer, and saved it as a 3mf file.

![image](https://github.com/user-attachments/assets/3eb3d44a-5d7f-4bad-97b1-4c4d175c0407)

the colorized part is above all the black parts, so there is only one filament change.

Now, the assembly steps looks like solder diodes, switches, mcu, battery onto pcb, insert switches into plate, solder switches to PCB, screw plate to bottom shell. 

**Total time spent: 3h**

# July 10th: Assembly (Part One):

Note: I forgot to journal this, so this is written on july 23rd, when I finally got the batteries.

I received all the parts except for the battery, so I printed off the plate to start assembly.

![IMG_0788](https://github.com/user-attachments/assets/8fbcdbc6-fa08-4d71-8dcc-a7352295d7a0)

as you can see, the plate and pcb are touching, meaning I cant use diodes

Unfortunately, the plate ended up being too thick, and the diodes wont fit. (it would have worked if it was SMD).

So I had to reprint thinner plates. After they printed I started snapping in the switches.

![IMG_0790](https://github.com/user-attachments/assets/e4f7bd69-aaae-4b8c-b20f-373713753e08)
![IMG_0789](https://github.com/user-attachments/assets/7ecd4669-c762-4e8f-8d3c-8375d86264bb)

As you can see in the back, I also placed the diodes in the holes.

After this, I realized I had made another mistake. This time I foolishly assumed in my cad that I would SMD solder the XIAO. I had soldered on the headers, so now I had to remove them.

![IMG_0791](https://github.com/user-attachments/assets/add812c8-7434-42de-87cf-24cd739022ad)

The process was pretty simple, with using diagonal cutters to cut the black parts, remove them, and then use the soldering iron plus some tweezers to remove each pin.

I then soldered the diodes + the mcu, cut the legs off, and soldered the switches as well.

![IMG_0793](https://github.com/user-attachments/assets/8ec2c282-d24a-493e-808b-0753f37ebcb8)
![IMG_0792](https://github.com/user-attachments/assets/7f911a7a-905d-4192-b1b4-86f571544b10)

Here's how it looked.

It was undercity tomorrow, so I basically speedran everything. I had forgotten to print the bottom part, so I put it to print and fell asleep. 

**Total time spent: 4h**

# July 11th: Assembly (Part Two)

I woke up (at like 4AM), put the heatset inserts in, and finally assembeled the keyboard.
![IMG_0795](https://github.com/user-attachments/assets/a5d57f7d-e36a-4e62-a20e-2db67cf4f2e6)

![IMG_0796](https://github.com/user-attachments/assets/c527909f-a041-4040-ac35-a2cb49f8beac)

I slapped the basic firmware in, and left for undercity. In Github HQ I realized that certain keys didn't work, so I had to fix it later.

**Total time spent: 30mins**

# July 22nd: Assembly (Part Three):

I received the batteries (finally!), and realized the keyboard still doesn't work. What I did was find the keys that didn't work, replaced them with a letter (T) and tried again. Looks like middle key on the thumb cluster on the left half doesn't work, and the entire thumb cluster on the right half doesn't work. I also figured out that bridging the pins on the left half worked, but not on the right. Looks like I fried a pin. I'll have to fix that. I had to leave, so that's all I did.

**Total time spent: 30mins**

# July 25th: Done! (sorta):

I wrote the title with the Hexboard, but since my current WPM is so slow, I switched back to my regular keyboard.

Part one: Battery

I tried getting the battery working, but for some reason I never got it working on the left half. I updated the firmware, resoldered the joints, but it still doesnt work. It works on the right half though. 
I added some code to the .overlay file in the zmk, and it supposedly reports the battery level. currently this doesn't matter, as zmk only reports the left half's battery, and only the right half is wireless. (the left half is only connected for power. Overall, this isn't too bad, as its only one usb-c wire on my desk. 

Part two: missed keys.

The only key on the left half that didn't work was the modifier, but upon further inspection it appeared that I forgot to solder a diode. As for the right half, it was more complicated. I rebuilt the firmware, using another pin, and soldered a wire from that pin (pin 7) to that row. I still had one problem though. The reset button on the right half was broken, and I had to find a workaround. I ended up grabbing some tin foil and touching that to the contacts. Only one key worked, so I inspected the board even more. It appeared that I burned the contacts on the PCB, so the traces never connected to the switch. I ended up soldering a wire to replace the traces that the switch couldnt connect to. 

![WIN_20250726_16_46_26_Pro](https://github.com/user-attachments/assets/45821235-fef3-4f0b-b35c-0bc0f35dd257)

![WIN_20250726_16_46_30_Pro](https://github.com/user-attachments/assets/f248c5ea-8861-4620-bd79-90c74620ffcd)

![WIN_20250726_16_47_52_Pro](https://github.com/user-attachments/assets/857513f3-e08c-4332-b319-eede42801129)

With that, I was finished. I just had two more things that I wanted to fix/add. One was fixing the battery on the left half, but that means I would have to desolder the entire mcu and try to clean the joints up. There was also a chance that the battery board was simply fried, and I don't want to go through all that. The second one was adding ZMK studio support to my keyboard. This means that I can easily modify the keymap, without building new firmware.

It turns out that this process takes a while, as I have to define a physical layout. In the end, i got it in a web tool

<img width="1076" height="862" alt="image" src="https://github.com/user-attachments/assets/d2fac4e4-f78a-4d20-984f-3ee950d05adb" />

and the ide

<img width="665" height="899" alt="image" src="https://github.com/user-attachments/assets/dac532db-e566-4e39-b8dd-2bff28436754" />

So I pushed it to Github and let it build, while I got some more tin foil.

After I reflashed the mcus, it worked!

<img width="1919" height="1025" alt="image" src="https://github.com/user-attachments/assets/4a45c931-f238-45ec-a532-44fcccf27541" />

So that's it! It's finished! 

I'll record some footage and upload it to youtube for a demo.

**Total time spent: 3h**








