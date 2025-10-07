
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
MADESH.A51

ORG 00H

MOV TMOD, #20H

MOV TH1, #0FDH

MOV SCON, #50H

SETB TR1

MAIN_LOOP:

MOV SBUF, #'B'

WAIT_TI:

JNB TI, WAIT_TI

CLR TI

SJMP MAIN_LOOP

END

MADESH.C

#include <reg51.h>

void main() {

TMOD = 0x20;

TH1 = 0xFA;

SCON = 0x50;

TR1 = 1;

while(1) {

SBUF = 'A';

while (TI == 0);

TI = 0;

} }

```
### (ii) Serial Port to Transfer a Message

MADESH.C

#include<reg51.h>

void main(void)

{

unsigned char msg[]="madesh";

unsigned char i;

TMOD=0X20; //TIMER 1, MODE 2

TH1=0XFA;

SCON=0X50;

TR1=1;

for(i-0;i<=12;i++)

{

SBUF=msg[i];

while(TI==0);

TI=0;

}

while(1);

}

MADESH.A51

ORG 0000H

MOV TMOD, #20H

MOV TH1, #OFDH

MOV SCON, #50H

SETB TR1

MOV A ,#'T'

ACALL TRANS

MOV A ,#'A'

ACALL TRANS

MOV A, #'N'

ACALL TRANS

MOV A, #'U'

ACALL TRANS

MOV A , #'J'

ACALL TRANS

SJMP $

TRANS: MOV SBUF, A

WAIT: JNB T1, WAIT

CLR T1

RET

END
### OUTPUT:
<img width="791" height="787" alt="image" src="https://github.com/user-attachments/assets/271d3b00-c338-4ab3-824c-3567d1270673" />

### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
