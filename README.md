# 32ESplus
32ES+ E-ink based RPN calculator using the M5Stack Paper S3 hardware.

Features include those on the 32ES.  New features are listed first:

An enhanced version of the 32ES calculator is the 32ES+.  This adds algebraic equation capability, an off image, clock and control over the beep sound.  The 32ES+ software is currently at a beta stage.

This uses algebraic parser functions from Github user Zserge which is provided for free use with the MIT license.  Limitations are that it does not check for expression validity.  If parentheses are mismatched, it can cause a crash.  Therefore, to save equations (on a micro SD card), press Shift-Off to turn the calculator off, and turn the calculator on.  It can hold up to 10 equations of 100 characters each.  Go to the Solve/Integrate menu and press D for getEQ.  Exponents must have a plus sign after the “e” and before the number, for example, 1.5e+5.  Negative exponents are fine, such as 2.3e-3.  Supported functions are sqrt, e^x, ln, y^x, 1/x, sin, cos, tan, asin, acos, atan, x^2, 10^x, log, pi, +, -, * and /.  To evaluate an expression, press XEQ when on the expression you want to evaluate.

For solving, press Enter once you are on the equation you want to solve.  Instead of A^2+B^2=C^2, you would have A^2+B^2-C^2, which makes it equal to 0.  To solve for C, enter the values of A and B, go to the Solve/Integrate menu and select “E” SolveEq and when prompted SOLVE, choose C.  For example if A is 3 and B is 4, C would be 5.  You can also solve for A or B.

For integrating, press Enter once you are on the equation you want to integrate.  Set the FIX digits to the precision you want.  Enter on the stack first the lower limit and then the upper limit.  Go to the Solve/Integrate menu and select “F”, IntegEq.  Enter the variable to integrate, like X.  Of course this will be slower than using a program and RPN, but easier to enter.  Just enter X^2 and find that from 0 to 10 the result is 333.33  With a program, you have to do LBL A, RCL X, X^2 and RTN.

The off image is pic.bmp and the resolution is 434x212.

To set the clock time, put the time on the stack in the form of HH.MM and go to the Mode menu and select E, SETIME.

To enable or disable the beep sound, select D, Beep in the Mode menu.

Source code may be provided at a future date once further testing has been done and the code is more stable.

32ES notes:

E-ink based 32S scientific calculator (beta version). Uses the M5Stack Paper S3 hardware.

32ES Calculator Project

Advantage of C implementation is speed, but not using calculator ROM means some aspects of the calculator may seem different than original.

Features:

26 registers and 1,400 program steps 2 selectable display fonts 3 selectable display colors audible keyboard beep fast - approx. 1,000,000 loop iterations in 10 seconds internally has number range from approx. 1e-317 to 9.9e307 solver using secant method integration using Simpson’s method complex number functions Known issues / differences from 32S:

EEX implemented slightly differently - single digit exponent processed immediately Eng notation and All display mode not implemented yet XEQ currently works like GTO INPUT, SHOW, VIEW and MEM not implemented yet COMPLEX and statistics functions are not programmable Indirect register addressing and GTO not implemented yet SF, CF and FS? not implemented yet BASE menu not implemented yet for Solver and integration, known variables must be manually entered beforehand in programming mode, each number digit requires a single step programming mode does not insert lines - currently does overwrite error messages need updating Program memory organization

The 1,400 program steps are organized as follows:

0-99 general 100-149 LBL A 150-199 LBL B 200-249 LBL C … 1350-1399 LBL Z

If LBL A is over 50 steps, it can overlap over B, and so on.

Burning firmware:

This 32ES+ firmware may be used for non-commercial personal or educational purposes. No warranties are made on the use of the firmware. It is up to the user to verify the accuracy or precision of this calculator implementation.

Go to Github riker2072 32ES+ repository.

Get 32ESplus.ino.bin, 32ESplus.ino.bootloader.bin and 32ESplus.ino.partitions.bin files.

Get Windows ESP32 flash download tool at: https://www.espressif.com/en/support/download/other-tools

Make sure you are using chip type ESP32-S3

Click on … to select 32ESplus.ino.bin file directory location. Check the box to the left of the file name. In the @ box, put 0x10000 Click on … to select 32ESplus.ino.bootloader.bin file directory location. Check the box to the left of the file name. In the @ box, put 0x0000 Click on … to select 32ESplus.ino.partitions.bin file directory location. Check the box to the left of the file name. In the @ box, put 0x8000

SPI speed is 40MHz, SPI mode is DIO. Check mark in the box labeled “DoNotChgBin”. My port settings are COM4, baud 115200. Connect the M5 Paper S3 to your PC using a USB C cable. Click on START to burn the firmware.

