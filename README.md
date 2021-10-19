# tec-GBA-BG
tec1 to GBA cartridge system


Ben Grimmett

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

![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/209914165_10158192426230869_8435976014097697285_n.jpg)
![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/213513900_10158192425445869_2233389688333613634_n.jpg) 
![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/215242643_10158192425970869_399779924914846978_n.jpg)


Stephen Justin 2x22 socket? thats whats i use for addons in my work. i love your suggestion. cart looks like 2x32, thats ok/better
Ben Grimmett 1 x 32
Mark Jelic I love it! Is that all the technical specs we have? Got a link to where we can buy them or do you have a stash?
Ben Grimmett they're literally gameboy game carts - we have them in our store for like $8, I'll grab you the $4 link
Mark Jelic mate I’d rather pay $8 from a local than $4 and god knows when/if it turns up!
Stephen Justin lookedon aliexpress like $40 usd, send ur link
Ben Grimmett https://www.aliexpress.com/item/1005001774816571.html...

![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/Pokemon%20GBC%20Games%20Series%2016%20Bit%20Video%20Game%20Cartridge%20Console%20Card%20Classic%20Game%20Collect%20Colorful%20Version%20English%20Language_Game%20Collection%20Cards_%20-%20AliExpress_page-0001.jpg)

Ben Grimmett now these probably don't have the battery inside, for that you'll want a cart with the game 'perfect dark', these are a little more expensive at USD$4.50 ea shipped to AU, or you can add your own coin cell/ holder / rechargable battery if thats the way you want to go. Or, replace the sram with FRAM Stephen Justin this is a good solution and price, now for the how part.

Ben Grimmett

![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/216936971_10158192456405869_8650335024998492542_n.jpg)

- clock isn't used on these, nor is audio_in. 
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

Maurice de Jersey Great idea. Do you have a link for the connector or a part number? Ben Grimmett You can grab them from us at $2 a pop, or i'll grab the ali link https://www.aliexpress.com/item/1005002017281326.html  Thats bulk, but they're also available in singles

![](https://github.com/SteveJustin1963/tec-GBA-BG/blob/main/pics/241389135_10158286503960869_3780352322921528001_n.jpg)



Ben Grimmett

Finished!

- 0x0000-07FF EPROM
- 0x0800-0FFF SRAM
- 0x1000-17FF expansion dip
- 0x4000-7FFF 4mbytes of flash
- 0xA000-BFFF 32kbytes nvram

Reproduced the keypad IC in VHDL with debounce filtering.

Errors: silkscreen Rom and ram locations are swapped. Fixed in CPLD but a wr wire added. If I didn't solder the sram in I could have swapped sockets.

Keypad matrix pull-ups needed, the max3000 family of CPLD don't support internal pull-ups. Fitted in the column pads instead. Could use a network resistor for a neater finish.

And jtag #2 and jtag #3 ports are swapped.

Need to add resistors to satisfy MonB code or fix the routine.

Can execute code from gameboy cart!

4 PCBs up for grabs. $25plus post and I'll solder in the CPLDs and 3.3v reg and flash the code to them. See Less
Comments
Scott Faulkner
Sure. I'll take one. Let me know postage and I'll paypal.
 · Reply · Share · 5w
Ben Grimmett
Scott Faulkner I'll solder them up tonight after dinner and pm you
 · Reply · Share · 5w
Scott Faulkner
Ben Grimmett Great mate, muchly appreciated. If you could also point me to the cart socket and what gb cartridgbe to buy that'd be greatly appreciated too.
 · Reply · Share · 5w
Ben Grimmett
Scott Faulkner no problem
 · Reply · Share · 5w
Joshua E. Hrouda
Looks great. What can it do? Do you have a video demo?
It can run GB firmware/software, but not play GB games, right?
 · Reply · Share · 5w
Ben Grimmett
Joshua E. Hrouda It is a tec-compatible computer with a GB cart slot to make use of a GB carts huge ROM and nvRAM capacity. It won't play GB games.
The idea behind this is to help you learn how to code CPLD's
 · Reply · Share · 5w
Ben Grimmett
Using a CPLD for address decoding for example means you can fully reconfigure the memory map in seconds and it doesn't have the same issues the original TEC did with address decoding.
You can also change how the 7seg driver works, the TEC must constantly refresh the LED's, you *could* code a driver in the CPLD to do that for you to free up the z80 for more important things.
And finally, the keypad CPLD - it emulates the original chip but it can also be expanded to hundreds of keys, or even a ps2 keyboard
 · Reply · Share · 5w
Joshua E. Hrouda
Nope, I have been soldering for 38 years. I solder microscopic SMDs with the help of my digital microscope and a steady pair of hands. I built a TEC-1B around 1990. Sadly I don't think I have it anymore. Not sure what happened to it 😥😔😡
 · Reply · Share · 5w
Joshua E. Hrouda
No photo description available.
 · Reply · Share · 5w
Joshua E. Hrouda
May be a closeup
 · Reply · Share · 5w
Joshua E. Hrouda
No photo description available.
 · Reply · Share · 5w


Sean Williams
I'll take one if it's still available. PM me the payment details - postage to Melbourne.
 · Reply · Share · 5w
Joshua E. Hrouda
Once those 4 PCBs are sold in the future, let's say 5 or 10 years later, if I decide I'd really like one, will you be able to assist then ?
 · Reply · Share · 5w
Ben Grimmett
Joshua E. Hrouda 10yrs is a long time!
 · Reply · Share · 5w
Joshua E. Hrouda
Just saying. I dunno if or when I'll need one
 · Reply · Share · 4w
Joshua E. Hrouda
Ben, can a FPGA be made to emulate a 74C923? If so, can u get FPGAs in 20 pin DIP (or SOIC) packages ?
 · Reply · Share · 4w
Ben Grimmett
Joshua E. Hrouda yes, the second CPLD on the board emulates the '923 and heaps of room to spare. I've got some dip PCBs coming in a week that'll convert the qfp package to dip 28
 · Reply · Share · 4w
Joshua E. Hrouda
Ben Grimmett nice!! Is it less power hungry than the original? Are there any disadvantages in using a CPLD as a keyboard encoder? What's the price of one?
 · Reply · Share · 4w
Joshua E. Hrouda
Ben Grimmett sorry. It's been a while (1 week) since I read your post. I'd forgotten.


