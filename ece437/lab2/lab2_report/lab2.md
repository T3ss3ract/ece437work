---
title: "ECE 437 lab 2"
author:
- "Vassily Petrov (vassily2) / AB1"
- "Sayan Sur (spsur2) / AB1"
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
In this lab, we were tasked with further exploring the capabilities of the XEM-7310-A75 board as well as the software build tools included with the Xilinx suite. We used similar System-On-Programmable-Chip (SOPC) systems in ECE 385 to be able to run software on the hardware systems we developed. 

Most software toolchains consist of a compiler for the desired language and the board-specific files needed to ensure that the code is deployed properly on the system. Vivado and the OpalKelly Frontpanel software offer a variety of software solutions, including C, C++, C# and Python, among others. 

It should be noted that since Python is interpreted into C before runtime, so python development on these boards can be made rather easily with an existing C compiler, along with some other libraries. This allows the easily-readable python code to be used on a complicted custom hardware made with Vivado.

#Pre-lab Questions: 
>Question 1: Look over the FrontPanel online documentation. How many WireIn and WireOut registers
do you have at your disposal?
                                                
**Answer:**  According the the spec in the manual, there are 32 Input ends and 32 Output ends can be maintained between the FPGA and the PC. 
                           
>Question 2: What is the bit depth for each one of these registers?

**Answer:**      
TODO Vassily   

> Question 3: What is the maximum data bandwidth when using Block-Throttled Pipes?

**Answer:** The maximum data bandwith for our board, using the USB-3.0 interface, is variable, depending on the speed mode selected. 

There are 3 speed modes: Full speed, High speed, and Super Speed. 

Full Speed: [16, 32, 64] x Multiple of 16

High Speed: [16, 32, 64 ..., 1024] x Multiple of 16

Super Speed: [16, 32, 64 ..., 16384] x Multiple of 16

The highest bandwith available is 16384 * Multiple of 16

For this, we will cap the total length of each block to 32 bits, since most of the registers we use will be 32 bits. Higher bits are ignored buy the device if not supported. The maximum speed is therefore 16384 * 32 = around 5Gbps.

> What is the address range for WireIn and WireOut?

**Answer:** 

TODO Vassily
