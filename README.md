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

