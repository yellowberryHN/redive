# Replacing LED boards on the touch panel

Wacca LEDs are notorious for being burnt out, you've likely received your machine in a state where some panels are not getting color data, are dim, or are straight up not lit up. This is partly due to the design of WS2812.

There's a few good options for replacements.

[SpeedyLabs](https://www.speedylabs.us/product/wacca-ws2813-led-pcb/) is selling their revision of the PCB, you'll need 60 of them to replace all your touch units.
[CensoredUsername](https://docs.google.com/forms/d/e/1FAIpQLSfETDKtABUGxhhcBXFDWuHlz1cwHNNozOXztCPOOsENcN5KxA/viewform) is another source for the EU.

Or alternatively, you can [make your own](./led-pcb.html)

## Instructions

Remove the control panel with single screw on the left and right side. 

![](https://cdn.discordapp.com/attachments/780283383069540393/1054935055333605457/PXL_20221221_013513863.jpg){ style="height:500px;" }

You don't need to remove the acrylic, just unplug the harnesses. Unplug, feed them up, slide the control panel out.

![](https://cdn.discordapp.com/attachments/780283383069540393/1054948737845301338/PXL_20221221_022911966.jpg){ style="height:500px;" }

After you have the outside plastic pieces taken off, disconnect the led data only wires, LED power on the middle LED board, and the touch board cable.  Then remove the two outside screws for the panel and pull it straight out

![](https://cdn.discordapp.com/attachments/780283383069540393/1054930972799414382/image.png){ style="height:500px;" }

Remove the ribbon from the pentel touch pcb and unscrew and remove the pcb. You can try to get away with not removing the touch PCB by loosening the screws on the touch board enough to get clearance to pull the LED board out, but this is risky and not recommended.

Unscrew each LED PCB and pull them out

Place in the new PCB and screw everything back together

Tip: You can "grip" the ribbon to feed it back through the hole to get it back into the pcb by using painter's tape. 
Be gentle here though, broken ribbons are no fun.

Note: You may need to remove the pop / marquee to get to the touch panels on the top of the machine. This may require security torx bits (not all cabs have security torx for some reason)
 
If the cab is powered on you will need to go to "connection test of touch devices " and "reconnect touch devices" in the test menu after re-connecting the touch board

Video instructions: [https://youtu.be/iyhxQFl7XyE](https://youtu.be/iyhxQFl7XyE)