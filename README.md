# PAL SNES RGB Amplifier

This describes a circuit I made to improve the picture quality on PAL SNES that doesn't requre any internal mod.

## Disclamier

AliExpress product links are affiliate links. By using them you support me to make more projects. Keep in mind that only a few project end up good, most are complety useless. Thats how evolotion works :)

I take no resonisibilty for damages of equpment. The design has been tesed by me on two different PAL SNES and by a friend on his. In all cases the picture quality was improved. You may get a diffrent result. I have not tested this on a NTSC SNES or with a unit with an internal RGB bypass mod.

Please let me know if you make your own device! If you make derivatives of this design please link back to this page.  eel free to contact me with qustions. I you want to make a comercial product please ask for permission first. All rights are reseved to me.

Contact me by Sending a message on [Instagram](https://www.instagram.com/patriksretrotech/), [X](https://x.com/patriksretrotec) or [Facebook](https://www.facebook.com/patriksretrotech).

Donation using [Ko-Fi](https://ko-fi.com/patriksretrotech) or [PayPal](https://www.paypal.com/donate/?business=UCTJFD6L7UYFL&no_recurring=0&item_name=Please+support+me%21&currency_code=SEK) are highly appreciated!

## Background

My PAL "2 CHIP" SNES had petty bad RGB output and it became even worse when using it with a [Scart switch](https://s.click.aliexpress.com/e/_mM7z2ac) and other consoles. I knew that it's possible to make an internal RGB bypass mod, but I wanted to try to make somthing that didn't require an internal mod. I started with making a model of the output stage in LTSpice from the [schematics of the PAL SNES](docs/PAL-SNES_Schematic.pdf). I tried many diffrent circuits to make a buffer that isolates the signal and finaly came up with a farly simple design.


## Solution

The image was dim and had ghosting. This how it initialy looked with a standard scart cable with [240P Test Suite](https://artemiourbina.itch.io/240p-test-suite) running on SNES. The images have be capture uing a home made GBS Control ([you can buy one also](https://s.click.aliexpress.com/e/_DmrSpE7)) and a [MS2130 True USB 3.0 Capture Card](https://s.click.aliexpress.com/e/_Debguux). (Be aware of cheap fake USB 2 imitaions!)

<img src="images/before.png"> 

This is the reslut using the same setup but with my circuit. I'm pretty happy with this!

<img src="images/after.png">

This is the model of the SNES and my design. It also have a model of astandard cabel for reference. You find the [project file here](sim/).

<img src="images/schematics.png">

The interesting parameters are Ra and Rb that sets the behaviour. I adjusted them to get about the same peak to peak voltage as the original cable. I also tried a few diffrent values on a real SNES. It seemed like the image got a huge improvement by making the impdance a bit higer seen from the SNES output (this also means lower current). The final values was determind by trial and error to get a good signal level and good image quality.

<img src="images/plots.png"> 

I asumed that putting the buffer as close as possible to the port is benfitial so made a module that i pluggs in to the back of the console. But my guess is that it should also work pretty well if it is place in a regualar Scart cable housing with a (short) cable.

<img src="images/front.jpg">

<img src="images/back.jpg">

<img src="images/final.jpg"> 

I used surface mounted BC817 transistors but any small signal NPN transistor like BC547B, BC337 or 2N3906 should also work fine.

You can get the needed connectors from AliExpress:
[The connector for SNES](https://s.click.aliexpress.com/e/_mL0Ws24) 
[Scart connector Scart](https://s.click.aliexpress.com/e/_mOZbAYg)

As the multi out connector provides 5 Volt on pin 10 so there is no need to use a power supply. The connections are the same as for a normal PAL Scart Cabel but with the buffers instead of the 75 ohm resistor to ground. You need three identical buffers one for each of R, G and B.

<img src="images/scart.png"> 




