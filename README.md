# tec-SERIAL-BG
TEC-1 Serial card by Ben Grimmett

Ben Grimmett
March 5 · TEC-1 Hardware
Due to discussions in this thread and others, the following changes have been made:

Interrupt signal on pad "PortA"

TX/RX is now "PortB"

Status/config is now "PortC"

Config(0)=Speed (0=9600, 1=115kbps)

Config(1)=Interrupt (0=Disable, 1=enable)

Status(0)=TXBusy (0=Busy, 1=ready)

Status(1)=RXrec (0=empty, 1=new data arrived)

Cold Start default is 9600bps/Int disabled.

You can tie PortB/C to any spare IO port you choose.
the first version was address mapped but it was decided to move it all to IO
Port A, B and C are on the serial board, so IO as in IO select line, not IO map, you can wire that up to whatever you like

115200bps serial port for the TEC. Fits into the exp socket and requires no soldering.

Enough logic spare to generate a custom clock for the z80 too, or interrupts when a byte arrives.

Edit: Changed a little bit here.

$1000 is the tx buffer - Auto send on write,

$1001 is the rx buffer - Reading Clears RX Full flag

$1002 is the status buffer, TX empty, RX full.

If I get these made up in bulk, I could squeeze 128k of banked sram on this thing too...

Who's up for a micro bootstrap coding competition?!?


---------------



Product available from https://bennvenn.myshopify.com/products/tec-1d-talking-electronics-z80-trainer-computer-pcb-only

Best to ask Ben thru the group https://www.facebook.com/groups/623556744820045/

Search info https://www.facebook.com/groups/623556744820045/search/?query=serial&epa=SEARCH_BOX

![](https://github.com/SteveJustin1963/tec-SERIAL-BG/blob/master/pics/49620918_10155966840465869_8317473652132020224_n.jpg)
![](https://github.com/SteveJustin1963/tec-SERIAL-BG/blob/master/pics/50416223_10155988682225869_3778409522020745216_n.jpg)
![](https://github.com/SteveJustin1963/tec-SERIAL-BG/blob/master/pics/88991858_10156960698935869_2851578841086820352_o.jpg)
