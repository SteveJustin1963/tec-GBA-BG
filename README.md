# tec-GBA-BG
tec1 to GBA cartridge system


Ben Grimmett
tt1 hSponsogidretrd  · 
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



