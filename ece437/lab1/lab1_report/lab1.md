---
title: "ECE 437 lab 1"
author:
- "Vassily Petrov (vassily2) / AB8"
- "Sayan Sur (spsur2) / AB8"
date: 1 Dec 2018
header-includes: |
    \usepackage{jeffe,handout,graphicx}
    \usepackage[utf8]{inputenc}
    \usepackage{fourier-orns}
    \usepackage{enumerate}
    \usepackage{stmaryrd}
    \usepackage{amsmath}
    \usepackage{float}
    \let\origfigure\figure
    \let\endorigfigure\endfigure
    \renewenvironment{figure}[1][2] {
        \expandafter\origfigure\expandafter[H]
    } {
        \endorigfigure
    }
---


\def\Cdot{\mathbin{\text{\normalfont \textbullet}}}

\newpage

#Introduction:

In this lab, we were introduced to the Xilinx Vivado IDE and explored the basics of this software. Vivado is similar to the Altera Quartus IDE used in ECE 385. Since the board in this lab is an OpalKelly XEM7310-A75, A Xilinx Toolchain and Development Kit is needed, since these boards are not compatible with Intel's systems. 

This lab consists of making a counter and using the buttons on our board platform. 

It should be noted that the FPGA board we use is only one part of the system. The board itself is mounted on another custom-made circuit board with sensors and buttons built into it. 




#Postlab Questions:

1. How many pins does the XEM7310-A75 Board have? 

Answer: According to the board spec from OpalKelly, All XEM7310 type boards have 126 IO pins, including 4 MRCC pins (MRCC means **M**ulti-**R**egion **C**lock **C**apable), 4 SRCC (**S**ingle **R**egion **C**lock **C**apable) pairs, and one pair of XADC ()

2. What is the maximum clocking speed of the XEM 7310-A75 board? 

Answer: The on-board crystal oscillator is 200Mhz, but this can be increased up to 800Mhz with the use of a PLL on the XC7A75T-1 FPGA.

3. How does the XEM 6002 board compare to XEM 7310- A75 in terms of logic gate  count,  transfer  speeds  between  the  board  and  PC,  external  memory,  and
 clocking speed of digital logic?
 
Answer: 

These two boards are both FPGA boards but serve different purposes in the field. The XEM6002 is a barebones fpgs system designed to interface with peripheral devices. 

6002 is a modular and low-cost platform that has countless applications in the field. It is significantly less powerful than the 7310-A75. In terms of PC connection speed, the 6002 has a maximum transfer rate of 36 mbps. The 7310-A75 has a usb-c port, allowing transfers of up to 340 mbps through the faster usb 3.0 standard. 

In terms of memory, the 6002 has a 32 megabyte serial peripheral interface (SPI) memory. This board has several ports on it and can be hooked up to a variety of other devices. This board has 4 external ports that can be used with external devices, while the 7310-A75 board is a pure FPGA board that can be hooked up to other boards (often custom boards) via SAMTEC expansion connectors. These are the 63 pin rectangular ports on the bottom of the board that connect to the mount on the custom board. 

The clock on the 7310-A75 and the clock on the 6002 chip differ in design. The 6002 strictly has a fully programmable pll (phase locked loop) clock, where the user can set the clock of the device. 

The 7310 board has a crystal oscillator clock that runs at 200MHz and can be linked to a PLL on the board to increase the clock speed. 

4. Why is the  clkdiv register 24-bit long?

Answer: The smallest number of bits that can hold a value of 10 million is 24, e.g. 2^23 < 10 million.

5.If clkdiv is  declared  as  an  8-bit  register,  what  is  the  minimum  frequency  you  can  achieve for the slow_clk signal using these FSMs? 

Answer: 200 Mhz / 2^8 = 781.25 Khz.

6. Look at the Project Summary window. In the Utilization section, you will find out the number of look up tables (LUT), flip flops (FF), input/output pins (IO) and buffers 
(BUFG)  are  used  for  your  design. How  many  resources  on  the  FPGA  are  used  to implement your code?

Answer: 

LUT: 1%

Flip-Flop: 1%

IO: 4%

Buffers: 3% 

7. Include a printout of your Verilog code with your report

 