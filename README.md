# WiFiflex
Wii WiFi relocation flex pcb

![Wififlex front](https://github.com/supertazon/WiFiflex/assets/49252894/52532ee0-9ff9-413e-a32b-f01b3843cfcf)
![image](https://github.com/supertazon/WiFiflex/assets/1402795/46e0e68d-764e-44ed-8664-1ff353428367)
![IMG_3469](https://github.com/supertazon/WiFiflex/assets/1402795/b5aa3793-8d84-407c-8988-c64485fead5c)

***Note: This version is specifically tailored for production through JLCPCB, as the original design did not fit within their capabilities. If you are planning on having these manufactured through a service such as PCBWay or GoldPhoenix's pool, please consider using the original version instead!***

A flex pcb to easily relocate the Wii WiFi chip for Wii portables (useless for stock Wii) by using the WiFi chip connector. The WiFi chip is notorious for being difficult to relocate by handwiring it due to wire length sensitivity. License is permissive, you are free to make, sell and distribute the flex pcb.

The flex pcb is compatible with a OMGWTF trim, it also does not overlap with the NAND relocation flex.

This version requires that you relocate RA20 from the Wii motherboard directly onto the flex, instead of the flex soldering directly to RA20. This was done since JLCPCB's castellation tolerances are not tight enough to support soldering to the 0402 resistor pack.

Repo contains the KiCad source files (needs KiCad 8.0RC2 minimum to work) and gerbers.

**BOM**

Molex connector 52991-0208: [DigiKey](https://www.digikey.com/en/products/detail/molex/0529910208/1059850) or [Mouser](https://www.mouser.com/ProductDetail/Molex/52991-0208?qs=KC2ywxza1krtfqlg7H04kw%3D%3D)

## How to order

As suggested by [YveltalGriffin](https://github.com/mackieks), the original design requires fabrication through a service that has tight tollerances with castellations, such as PCBWay. This modification allows fabrication through cheaper services such as JLCPCB.

This modification is *untested* and *highly experimental.* Things may not line up or it might not work at all. Try this at your own risk (and report your findings on the [BitBuilt forums](https://bitbuilt.net/forums/index.php?threads/wififlex-wii-wifi-relocation-flex-pcb) please!)

Through JLC, please make sure to select these settings:
  - FPC thickness: 0.11 mm
  - Surface finish:  Immersion gold (ENIG) (1U")
  - Finished copper:  1/3 oz Cu (18μm) (Ideally you'd want 0.5oz copper here but JLC does not seem to support this yet)


## How to install

  1. Populate the flex pcb, take note of the silkscreen to correctly position the connector. I highly recommend using solder paste and a hot plate or hot air, it's definitely easier than hand soldering it. Check continuity between the connector pins and the vias before moving on.
    - Also be sure to remove RA20 off the Wii motherboard and install it onto the designated spot on the flex. No need to worry about polarity here.
	- After removing RA20, remove any residual solder left on the RA20 footprint pads on the Wii motherboard with solder wick. This is to ensure the flex sits properly on the board and isn't damages by leftover solder.
  2. Scratch the two pairs of vias 3.3V and GND while making sure to scratch the space between both.
  3. Position the flex to locate where you will scratch the Wii's GND plane for the upper right via on the flex.
  4. Scratch the Wii's GND plane at the correct position.
![image](https://github.com/supertazon/WiFiflex/assets/1402795/c1d43988-1366-4a60-a345-c4a0bf6e58f1)
*Vias and GND spot scratched, could have done better but wanted to avoid scratching the surrounding traces*

  6. Add flux and pre-tin the vias and GND spot. I noticed the 3.3V vias needed more heat to be properly tinned.
  7. Position the flex and secure it with a piece of kapton tape between the GND vias and the connector.
  8. Solder the GND vias with the Wii GND vias and the 3.3V vias with the Wii's 3.3V vias. Don't forget you might need to apply more heat on the 3.3V vias.
  9. Add flux and solder to the pads on the flex that align up directly with the left over pads on the RA20 footprint.
  10. Check continuity between the these points and the vias they connect to on the Wii motherboard (follow the traces).
  11. If everything is nominal then proceed with soldering the big GND via, otherwise reflow as needed.

Now that you are done you can try putting a WiFi chip on there and see if you get signal. Be careful to not short anything on the board, you might need to add kapton tape either on the chip or on the Wii motherboard.

### Please handle the flex pcb with care! It is quite fragile, I inadvertently ripped it off the Wii while testing. Make sure you really solder that big GND via for better stability.

## Contributors

- **[supertazon](https://github.com/supertazon)**: Initial design and routing
- **[YveltalGriffin](https://github.com/mackieks)**: Via stitching, large GND via addition, silkscreen and general tips on routing
- **Y2K**: Modified design for JLCPCB specifications, with permission from supertazon.

## Acknowledgements

- [BitBuilt's Definitive Wii Trimming Guide](https://bitbuilt.net/forums/index.php?threads/the-definitive-wii-trimming-guide.198/): for info on WiFi soldering points
- [MJMT's WiFi breakout board](https://bitbuilt.net/forums/index.php?threads/wifi-breakout-board-for-relocation.4916/post-53366): for the connector reference
- [ShockSlayer's handwired WiFi relocation](https://bitbuilt.net/forums/index.php?threads/sswiit-revitalized.146/post-982): to see how it was done before
- [BitBuilt community for being awesome](https://bitbuilt.net/)
