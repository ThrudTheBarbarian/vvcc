# vvcc
Variable-VCC circuit using an RP2040

This is a test-board to try out using a variable-pot controlled by an RP2040 to 
in turn control the voltage of a voltage regulator. That voltage will then be
provided to the other side of a level-shifter to insulate an FPGA from different
voltage inputs.

The level shifter in question can run at >400 MHz, which is the max toggle frequency of
the FPGA.

Simultaneously, I wanted to test out the USB component of the RP2040 and make sure I had
the design correct before laying down the FPGA board (which is a lot more expensive). the
RP2040 will be the last bastion against a bricked FPGA, so it'd be good to know that 
worked too.

So basically a testing-ground. Enjoy.

Thrud


# Update 25/May/2022

Boards came back today, with slightly mixed results. Plugging the first board in, the leds flickered, presumably magic smoke exited stage left, and the 3.3v power rail was churning out 1.1v...

Checking everything against the schematic, it seemed ok, nothing was placed the wrong way around, and even running through the boot process for the I2C resistance looked like the voltage would be ok (4.3v by default).

I was left wondering whether the boot process did weird things, which seems vanishingly unlikely, but ... Anyway, holding down reset & boot buttons made it boot up ok, appear as RPI2_BOOT on the Mac, and none of the LEDs flashed, 3.3v rail seems ok (LED lights) etc. 

So my advice is that if you get these made, make sure you initialise it with known firmware before letting it boot on its own. There is a pullup missing on the /CS line for the flash, but it's also missing in the RP2040 hardware design guide with the comment that they found they didn't need it. I'll definitely include it in future mind.

If booting it with working firmware still results in a problem, I'll update this. It's also possible the first board was just a dud... Once I have tested out the firmware thing, I might try sacrificing another board to see if it has the same behaviour as the first.

Thrud
