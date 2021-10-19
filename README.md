# tec-GBA-BG
Tec-1 with a GBA cartridge system 

by Ben Grimmett

TEC ROM/RAM card - 4mbytes banked Flash, 32kbytes Banked NVRAM. $4 delivered.
Just a suggestion for a proven, cheap, robust, plentiful supply of hot swappable memory cards for a future TEC.

Memory map:

`0x0000-3FFF fixed to Flash Address 0x0000-3FFF`

`0x4000-7FFF 256 banks, can be swapped by writing to address 0x2000.`

`0xA000-BFFF 8kbytes of NVRAM. `

Write protected unless 0x0A written to 0x0000. Protected if any other value is written to that address. Bank swapped by writing to 0x4000.
This still gives you empty spots in the memory map for other things, and the entire cart can be disabled with a /CS signal, or just unplugged.
These are common bootleg GameBoy Cartridges. Z80-like code executes directly from them in the GB. You can find them on eBay or aliexpress from $4 shipped to your door.
How do you get code on them? You can do it in system, or use any number of GB Cart flashers like the pic included. The cart appears as a USB mass storage drive, you drag the firmware on, and its done.
Not sure you can beat the bang for buck these offer. Cart sockets are $1 ea and with HUGE pins, soldering won't be a problem.
Thoughts?

### Links!
If you want to buy from us (Goulburn NSW):
- 4Mbyte Flash + 32K save (volatile) - https://bennvenn.myshopify.com/.../gb-c-flash-cart-4mbyte...
- 4Mbyte + 32K battery backed (NV) - https://bennvenn.myshopify.com/.../gb-c-flash-cart-4mbyte...
- The best cart flasher you can buy! (USB Drag and drop, no drivers, no software) - https://bennvenn.myshopify.com/.../usb-gb-c-cart-dumper...
- Cart Sockets: https://bennvenn.myshopify.com/.../32pin-gb-c-a-cart...

If you can wait for the slowboat from china:
- 4M + 32K NV - https://www.aliexpress.com/item/4000589108517.html...
- AVOID CHINESE FLASHERS - they're all clones of ours or others and have adopted the nickname 'firestarters' for a good reason.
- A cheaper flasher is the GBxRW from Inside Gadgets 
- Another Aussie company. A little slower, a little more clunky but you'll save $10 or so 
- they don't support some chinese carts.
- Chinese cart socket - https://www.aliexpress.com/item/4001322498055.html...

![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/209914165_10158192426230869_8435976014097697285_n.jpg)
![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/213513900_10158192425445869_2233389688333613634_n.jpg) 
![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/215242643_10158192425970869_399779924914846978_n.jpg)

- SJ 2x22 socket? thats whats i use for addons in my work. i love your suggestion. cart looks like 2x32, thats ok/better.
- BG its 1 x 32

- MJ I love it! Is that all the technical specs we have? Got a link to where we can buy them or do you have a stash?
- BG they're literally gameboy game carts - we have them in our store for like $8, I'll grab you the $4 link. 
- MJ mate I’d rather pay $8 from a local than $4 and god knows when/if it turns up!

- SJ looked on aliexpress. its like $40 usd, pls send ur link.
- BG  https://www.aliexpress.com/item/1005001774816571.html...

![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/Pokemon%20GBC%20Games%20Series%2016%20Bit%20Video%20Game%20Cartridge%20Console%20Card%20Classic%20Game%20Collect%20Colorful%20Version%20English%20Language_Game%20Collection%20Cards_%20-%20AliExpress_page-0001.jpg)

- BG now these probably don't have the battery inside, for that you'll want a cart with the game 'perfect dark', 
- these are a little more expensive at USD$4.50 ea shipped to AU, 
- or you can add your own coin cell/ holder / rechargable battery if thats the way you want to go. 
- Or, replace the SRAM with FRAM. 
- SJ this is a good solution and price, now for the how part.

![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/216936971_10158192456405869_8650335024998492542_n.jpg)

- BG clock isn't used on these, nor is audio_in. 
- reset can be tied to z80 reset, it just sets the banks to 00's. 
- WR and RD are for writing and reading to sram/flash/banking. 
- CS is asserted when you want to access the sram. 
- its otherwise z80 compatible in timings and all that good stuff. Just feed it 5v and gnd. 
- There's also a 9600bps modem cart for the GB, 
- IR transceiver carts, 
- ultrasonic fish finder, 
- aprilia scooter ecu interface, 
- all kinds of really odd devices.

![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/214411736_10158192478090869_7950355688786903180_n.jpg)

- MDJ Great idea. Do you have a link for the connector or a part number? 
- BG You can grab them from us at $2 a pop, or i'll grab the ali link https://www.aliexpress.com/item/1005002017281326.html  
- Thats bulk, but they're also available in singles

![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/241389135_10158286503960869_3780352322921528001_n.jpg)

- SG Other than writing to memory locations to manage it rather than using IO, these look good.
- BG No IO on the gameboy, but you could redirect IO / Address writes to make it do what you want at the hardware level

- CJ This is a pretty good idea Ben Grimmett, surely you did not just realise this crossover today?😉
- BG I may have dabbled with these carts once or twice before 
- but it was Mark Jelic's post last night with his idea of the SNES cart that got me thinking, why reinvent the wheel?
- CJ Yes, cart programmers are cheaper than EPROM programmers, 
- It solves the memory map and storage problem 
- i.e. it forces a choice!, no need to source a disappearing resource, small size EPROMs and RAMs. 
- Needs very little supporting hardware (if any?)
- and could be retro fitted. Brilliant!
- I am sure someone could write a small boot / supervisor program to page the banks, lots of software options!
- BG We've developed custom carts based around FPGA's 
- so we can set any memory map we like, even IO mapping. 
- Best to use off the shelf stuff though
- CJ Sure, but once you have the slot for the cart anything is possible.😁
- BG it takes up so little realestate on the board 
- and at a dollar it makes sense to drop one in. 
- One day we may be sharing games and code on carts!
- CJ I might just email you the card image
- I can't see any downside, is there any? 
- It's very retro that's for sure! 
- When can we have it?
- BG send over the image, unless you want the tec bootloader on there?
- CJ I do have a USB cart, I think it has LSDJ on it, another project that fell by the wayside...
- BG what brand? The dragon cart and drag'n'drop would be awesome for dev
- CJ It's the EMS one. Had it for a while, can't remember when I got it.


- AM So if this looks like 64k on the bus, and I map a bunch of them into 16M physical space, my mind boggles at the total capacity
- BG if you're after a little more room, you can also get 32mbyte Flash + 128kbyte SRAM, battery backed
- AM if you have a link that would be welcome. I might stick a few in for library routines.
- BG That's a lot of libraries!!! '22in1' gbc carts will get you what you're looking for
- AM I am wanting to try running a Z-80 as a multi user system with very high level programming functions. 
- Basically any chunk of code you can think of gets switched in and run. Will chew through a lot of memory.
- BG sounds interesting! You might want to look at implementing the GBA cart bus? It'll give you access to 256mbyte flash, 128k sram?

- JH Brilliant. An obviously flexible and proven retro technology solution. 
- Great also to hear ideas from Ben Grimmett again. This group is awesome.

- MJ Ben, are you thinking this cartridge is it, when it comes to all the RAM or ROM the TEC would address?
- Or are you still thinking of having a particular address space (like I have above) dedicated to the GB cartridge, 
- which would mean a bit of tom-fooler would be required to access all the addressable memory off the cart.
- BG My opinion is, don't build it with a fixed memory map.
- MJ OK... but I don't know what that looks like. I havn't seen a schematic from anyone that I can start designing the PCB for.
- BG it means there is no address decoding, just the bus goes to an expansion, 
- the user can add their own idea of a perfect memory map. 
- Given a GBC cart has all its own decoding, you could plug that in and have an instant system with 4MB of ROM, 32KB of RAM, decoded correctly for no bus congestion. 
- With a little re-working of the monitor it'll boot and run just fine off a cart too. 
- Are you building this system? I thought Craig Jones was?
- MJ I've been designing my own for a while, hence the TEC-2014 moniker.
- BG you should make a GBC - 2014 card! you'll shake up the 2014 industry!


- CJ I sure am going to have a go at this! Got what I need on order, I already have a few bits and pieces. 
- Sorry I didn't recognise the Joey Jr V2cc Cart Flasher in the top right of your picture above! 
- Maybe a better pic and a link may help others who want to have a go at this find it.
- BG edited the post with links to ours, chinese and competitors products

- MJ For those interested, here are some website I found that discuss the memory map of the Gameboy. 
- Pretty interesting the way the implemented it.
- http://gameboy.mongenel.com/dmg/asmmemmap.html
- https://raphaelstaebler.medium.com/memory-and-memory...
- https://b13rg.github.io/Gameboy-MBC-Analysis/
- DuoDreamer's Dreamscape   https://GAMEBOY.MONGENEL.COM
-BG just fyi, all chinese carts use the mbc5 memory mapper


### BG; Finished!

- 0x0000-07FF EPROM
- 0x0800-0FFF SRAM
- 0x1000-17FF expansion dip
- 0x4000-7FFF 4mbytes of flash
- 0xA000-BFFF 32kbytes nvram

- Reproduced the keypad IC in VHDL with debounce filtering.
- Errors: silkscreen Rom and ram locations are swapped. 
- Fixed in CPLD but a wr wire added. If I didn't solder the sram in I could have swapped sockets.
- Keypad matrix pull-ups needed, the max3000 family of CPLD don't support internal pull-ups. 
- Fitted in the column pads instead. Could use a network resistor for a neater finish.
- And jtag #2 and jtag #3 ports are swapped.
- Need to add resistors to satisfy MonB code or fix the routine.
- Can execute code from gameboy cart!
- 4 PCBs up for grabs. $25plus post and I'll solder in the CPLDs and 3.3v reg and flash the code to them.  


- JRH Looks great. What can it do? Do you have a video demo?
- It can run GB firmware/software, but not play GB games, right?
- BG It is a tec-compatible computer with a GB cart slot to make use of a GB carts huge ROM and nvRAM capacity. It won't play GB games.
- The idea behind this is to help you learn how to code CPLD's
- JEH will you sell a complete kit?
- are CPLDs as complicated to program as FPGAs?
- BG I don't have that many spare Z80's or other bits and pieces for full kits. They will include the CPLD's though, pre soldered and programmed.
- A cpld is a fpga, just a different name (and other differences). Programming needs a $10 usb programmer from ebay (USB Blaster). As for the code, you can use the visual designer where you just drag logic chips and draw wires, or you can code in a specific language. I'll upload all the code here
- Using a CPLD for address decoding for example means you can fully reconfigure the memory map in seconds and it doesn't have the same issues the original TEC did with address decoding.
- You can also change how the 7seg driver works, the TEC must constantly refresh the LED's, you *could* code a driver in the CPLD to do that for you to free up the z80 for more important things.
- And finally, the keypad CPLD - it emulates the original chip but it can also be expanded to hundreds of keys, or even a ps2 keyboard

-JEH can a FPGA be made to emulate a 74C923? If so, can u get FPGAs in 20 pin DIP (or SOIC) packages ?
- BG yes, the second CPLD on the board emulates the '923 and heaps of room to spare. I've got some dip PCBs coming in a week that'll convert the qfp package to dip 28

- SJ Ben is the circuit private? if not will u release it ? Id like to buy the next version of the pcb when its ready. awsome work.
- BG 'll upload it in files
