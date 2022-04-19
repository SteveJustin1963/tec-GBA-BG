# tec-TEC1-Custom-BG
Tec-1 PCB with GBA cartridge system + CPLD  by Ben Grimmett

- see also https://github.com/SteveJustin1963/tec-CPLD-BG
- TEC ROM/RAM card 
- 4mbytes banked Flash
- 32 kbytes Banked NVRAM
- Just a suggestion for a proven, cheap, robust, plentiful supply of hot swappable memory cards for a future TEC.

### Memory map:
```
0x0000-3FFF fixed to Flash Address 0x0000-3FFF
0x4000-7FFF 256 banks, can be swapped by writing to address 0x2000.
0xA000-BFFF 8kbytes of NVRAM.
```

- Write protected unless `0x0A` written to `0x0000`. Protected if any other value is written to that address. 
- Bank swapped by writing to `0x4000`.
- This still gives you empty spots in the memory map for other things, and the entire cart can be disabled with a /CS signal, or just unplugged.
- These are common bootleg GameBoy Cartridges. 
- Z80-like code executes directly from them in the GB. 
- You can find them on eBay or aliexpress from $4 shipped to your door.
### How do you get code on them? 
- You can do it in system, or use any number of GB Cart flashers like the pic included. 
- The cart appears as a USB mass storage drive, you drag the firmware on, and its done.
- Not sure you can beat the bang for buck these offer. 
- Cart sockets are $1 ea and with HUGE pins, soldering won't be a problem.


### buy from us (Goulburn NSW):
- 4Mbyte Flash + 32K save (volatile) - https://bennvenn.myshopify.com/.../gb-c-flash-cart-4mbyte...
- 4Mbyte + 32K battery backed (NV) - https://bennvenn.myshopify.com/.../gb-c-flash-cart-4mbyte...
- The best cart flasher you can buy! (USB Drag and drop, no drivers, no software) - https://bennvenn.myshopify.com/.../usb-gb-c-cart-dumper...
- Cart Sockets: https://bennvenn.myshopify.com/.../32pin-gb-c-a-cart...
- https://bennvenn.myshopify.com/products/usb-gb-c-cart-dumper-the-joey-jr


### slowboat from china:
- 4M + 32K NV - https://www.aliexpress.com/item/4000589108517.html...
- AVOID CHINESE FLASHERS - they're all clones of ours or others and have adopted the nickname 'firestarters' for a good reason.
- A cheaper flasher is the GBxRW from Inside Gadgets 
- Another Aussie company. A little slower, a little more clunky but you'll save $10 or so 
- they don't support some chinese carts.
- Chinese cart socket - https://www.aliexpress.com/item/4001322498055.html...

![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/209914165_10158192426230869_8435976014097697285_n.jpg)
![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/213513900_10158192425445869_2233389688333613634_n.jpg) 
![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/215242643_10158192425970869_399779924914846978_n.jpg)



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
