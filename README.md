# Kishore_mpmc_SA2
## AIM
To write a assembly language program for 8051 to generate a 100 ms delay using timer 1 in mode 2 and toggle the port 2.5 continously.

## SOFTWARE REQUIRED
Keil µVision IDE
Personel computer
## ALGORITHM
Start program execution at address 0000H.

Set Timer 1 in mode 2 (8-bit auto-reload mode).

Load the timer high register (TH1) with 00H.

Initialize outer loop counter (R6) to 2.

For each outer loop:

Initialize inner loop counter (R5) to 196.
Start Timer 1 and wait until it overflows (TF1 = 1).
Stop and clear the timer, then repeat until R5 = 0.
Toggle the bit P2.5 after each full inner loop.

Decrease R6 and repeat outer loop until R6 = 0.

Jump back to the beginning to repeat the entire process continuously.

## PROGRAM
```.a51
ORG 0000H
MOV TMOD, #20H
MOV TH1, #00H
HERE:
    MOV R6, #2
OUTER:
    MOV R5, #196
INNER:
    SETB TR1
WAIT:
    JNB TF1, WAIT
    CLR TR1
    CLR TF1
    DJNZ R5, INNER
    CPL P2.5
    DJNZ R6, OUTER
    SJMP HERE
END
```
## OUTPUT


## RESULT
The 8051 program to generate a 100ms delay using timer 1 in mode 2 and toggle port 2.5 continuously is successful.
