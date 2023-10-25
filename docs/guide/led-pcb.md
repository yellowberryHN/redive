# Replacement LED PCBs

> WARNING:
> If you're reading this, you probably know the basics of soldering, including SMD components.
> 
> If you're totally new to soldering, SMD might be a bit tricky. I'd suggest picking up an interesting keyboard project 
> (like the corne) and studying lots of youtube videos on the matter.
> 
> Just remember to use solder with flux (Kester 63/37 .031 inch leaded solder recommended), and to use a smoke absorber 
> for your safety (Hakko FA400-04 recommended). When in doubt, flux flux flux.

So, you want to manufacture your own LED PCBs? Well, here's a good way to go about that.

1. Clone [Isola's repo](https://github.com/mnm-isola/wacca_ws2813) or download the ZIP from the Code button. 
   `wacca_ws2813_rev20221021` is the revision we want. The main difference between revisions is that the capacitor at C9
   is SMD instead of THT. If you need THT, the previous August revision will do just fine.
2. [Download KiCad](https://www.kicad.org/download/)
3. Open `wacca_ws2813.kicab_pcb`.
4. `File > Fabrication Outputs > Gerbers (.gbr)`. Set your output directory appropriately. 
5. Click `Generate Drill Files...` and ensure that the drill units are in millimeters. 
   Click `Generate Drill File` and `Generate Map File`.
6. Click `Plot`.

You should now have 13 files. Zip these files up and go to your favorite PCB manufacturer (I like JLCPCB). 

**You need 60 PCBs to do a full replacement.**

It should be as simple as uploading the zip, clicking through, and purchasing. 
I didn't change any of the default options other than making the PCB solder mask white.
It took a total of 7 days for 200 PCBs to be produced, ship, and arrive from China to California. 
YMMV. About $45 for the PCBs and $47 for shipping.

If someone has a cool WACCA-related silkscreen, please give. Maybe one of each navigator.

Now that your PCBs are being fabricated, it's time to order the parts you'll need. 
[LCSC](https://www.lcsc.com/) is the recommended shop for these, 
they ship right out of Shenzhen and it's quite quick, considering.

### BOM (for use with WS2813B-V5)

| Footprint | Parts                  | Size  | Value  | LCSC                                                                                                                                     | Remark                                    |
| --------- | ---------------------- | ----- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------- |
| C1-C8     | Not Needed             | N/A   | N/A    | N/A                                                                                                                                      | WS2813B-V5 do not require decoupling caps |
| C9        | Tantalum Capacitor     | 7343  | 220uF  | [**C8024**](https://www.lcsc.com/product-detail/Tantalum-Capacitors_Kyocera-AVX-TAJD227K010RNJ_C8024.html)                               | Optional but adds protection. 10V.        |
| CN1, CN2  | JST XA                 | 3 pin | N/A    | [**C265055**](https://www.lcsc.com/product-detail/Wire-To-Board-Wire-To-Wire-Connector_JST-Sales-America-B03B-XASK-1-LF-SN_C265055.html) | B03B-XASK-1(LF)(SN)                       |
| CN3       | JST XA                 | 4 pin | N/A    | [**C264994**](https://www.lcsc.com/product-detail/Wire-To-Board-Wire-To-Wire-Connector_JST-Sales-America-B04B-XASK-1-LF-SN_C264994.html) | B04B-XASK-1(LF)(SN)                       |
| D1-D8     | Worldsemi WS2813B-V5   | N/A   | N/A    | [**C965558**](https://www.lcsc.com/product-detail/Light-Emitting-Diodes-LED_Worldsemi-WS2813B-V5_C965558.html)                           |                                           |
| R1, R2    | 0805W8F1000T5E         | 0805  | 100R   | [**C17408**](https://www.lcsc.com/product-detail/Chip-Resistor-Surface-Mount_UNI-ROYAL-Uniroyal-Elec-0805W8F1000T5E_C17408.html)         |                                           |
| U1, U2    | MMBD1503A              | N/A   | N/A    | [**C242273**](https://www.lcsc.com/product-detail/Diodes-General-Purpose_onsemi-MMBD1503A_C242273.html)                                  |                                           |

So to do the math for you, to replace all of your lights, that's 60 PCBs you need.
```
60x  C8024   [ships in multiples of 1]
120x C265055 [ships in multiples of 10]
60x  C264994 [ships in multiples of 10]
480x C965558 [ships in multiples of 5]
120x C17408  [ships in multiples of 100, you'll have 80 extra]
120x C242273 [ships in multiples of 5]
```

The parts at the time of writing were $61.94 with $14.24 for slower shipping from China to California.

## Soldering it all together

One way to shave a lot of time off mass producing these PCBs is to use solder paste and 
order a stencil from [OSH Stencils](https://www.oshstencils.com/). Upload the gerber zip, 
select the side that has all the LEDs as the top stencil (`wacca_ws2813_f_paste.gtp`), 
and make frameless stainless steel 5mil. Should cost about $50.

Ordering the jig accessory can help as well, 
but you can just use other PCBs to hold the position of the one you're squeegeeing. 
Get some solder paste and apply it to the PCB using the stencil 
(spread over stencil and squeegee. if no stencil, careful syringing), 
apply the SMD components, put it in a modified oven or on top of a modified clothes iron 
(or maybe you can use hot air at low flow)
