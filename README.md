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