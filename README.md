# tec-SERIAL-BG
TEC-1 Serial card by Ben Grimmett

Ben Grimmett
March 5 · TEC-1 Hardware

- "You can tie PortB/C to any spare IO port you choose.
- the first version was address mapped 
- but it was decided to move it all to IO Port A, B and C are on the serial board, 
- so IO as in IO select line, not IO map, you can wire that up to whatever you like
- Due to discussions in this thread and others, the following changes have been made:
- Interrupt signal on pad "PortA"
- TX/RX is now "PortB"
- Status/config is now "PortC"
- Config(0)=Speed (0=9600, 1=115kbps)
- Config(1)=Interrupt (0=Disable, 1=enable)
- Status(0)=TXBusy (0=Busy, 1=ready)
- Status(1)=RXrec (0=empty, 1=new data arrived)
- Cold Start default is 9600bps/Int disabled.
- 115200bps serial port for the TEC. Fits into the exp socket and requires no soldering.
- Enough logic spare to generate a custom clock for the z80 too, or interrupts when a byte arrives.
- Edit: Changed a little bit here.
- $1000 is the tx buffer - Auto send on write,
- $1001 is the rx buffer - Reading Clears RX Full flag
- $1002 is the status buffer, TX empty, RX full.
- If I get these made up in bulk, I could squeeze 128k of banked sram on this thing too...
- Who's up for a micro bootstrap coding competition?!?"

### more
- "There are two ports of your choosing/wiring
- One is a data in and out, The other is settings.
- By default, it's 9600bps 1 start bit, no parity, 2 stop bits
- The settings register selects 115200bps 
- and also if you want an interrupt triggered on rx

- Just write to the port
- It'll auto send the byte
- Or read the last bite received
- There's also bits to indicate if a new byte has arrived
- The bit settings should be in one of the posts and whatever you solder to. ie if you solder to 4 and 5, then 4 and 5
- so its all through two ports
- the group wanted to keep address space for rom and ram and use ports for IO
- after a fresh power up, writing to port C (IIRC) will send out whatever you write to that port
- send an ascii 'U' and an ascii U will appear in the terminal 
- if terminal sends a byte back, it'll be in port C ready to be read
- port B is the status and control register. 
- In here you can test if a bit is sent, a bit has arrived and the baud rate
- correction, looking at the code:
- DataWrite <= '0' when PortB='0'and WR='0' else '1'; 
- RXRead <= '0' when PortB='0' and WR='1' else '1'; 
- StatRead <= '0' when PortC='0' and WR='1' else '1'; 
- StatWrite <= '0' when PortC='0' and WR='0' else '1';

- reading the status register, port C: Statread='0' then D(0)<=TXBUSY; 
- 1 = buffer ready, 
- 0 = in use D(1)<=RXFull;
- 1 = byte ready to be read, 
- 0 = no new data

- writing to the status register:
- CLKslowFast<=D(0); IntEn <=D(1);

- Ok, so there is no address space mapped to the serial board its all through ports 
- as in, IN A,(xx) and Out (xx),A

- the first version was address mapped 
- but it was decided to move it all to IO Port A, B and C are on the serial board
- you can wire that up to whatever you like."

## Product available 
- from https://bennvenn.myshopify.com/products/tec-1d-talking-electronics-z80-trainer-computer-pcb-only
- Best to ask Ben thru the group https://www.facebook.com/groups/623556744820045/
- Search info https://www.facebook.com/groups/623556744820045/search/?query=serial&epa=SEARCH_BOX

![](https://github.com/SteveJustin1963/tec-SERIAL-BG/blob/master/pics/49620918_10155966840465869_8317473652132020224_n.jpg)
![](https://github.com/SteveJustin1963/tec-SERIAL-BG/blob/master/pics/50416223_10155988682225869_3778409522020745216_n.jpg)
![](https://github.com/SteveJustin1963/tec-SERIAL-BG/blob/master/pics/88991858_10156960698935869_2851578841086820352_o.jpg)
