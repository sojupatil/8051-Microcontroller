# Practical NO 3. ARITHMETIC OPERATION
## Addition 
```asm
ORG 00H
MOV A,#06H
MOV B,#04H
ADD A,B
END
```

## Subtraction 
```asm
ORG 00H
MOV A,#0AH
MOV B,#04H
SUBB A,B
END
```

## Multiplication 
```asm
ORG 00H
MOV A,#0AH
MOV B,#06H
MUL AB
END
```
## Divide Two 8 bit numbers
```asm
ORG 00H
MOV A,#28H
MOV B,#05H
DIV AB
END
```

# Practical NO 4. Data convert using Arithmetic and logical problems 
## Decimal to Hexadecimal
```asm
ORG 00H
MOV A,#225
MOV B,#16
DIV AB
MOV R5,B
MOV B,#16
DIV AB
MOV R6,B
MOV R7,A
END
```
## Hexadecimal into decimal 
```asm
ORG 00H
MOV A,#0FFH
MOV B,#10
DIV AB
MOV R5,B
MOV B,#10
DIV AB
MOV R6,B
MOV R7,A
END
```

# Practical NO 5.TO FIND LARGEST NUMBER FROM AN ARRAY OF 10 NUMBERS ALSO TO FIND SMALLEST NUMBER FROM AN ARRAY OF 10 NUMBERS
## Assume array of 10 bytes is stored in internal memory of 8051 microcontroller from memory location 50h and store largest number in Register B
```asm
ORG 00H
MOV R1,05H
MOV R0,#50H
DEC R1

MOV B,@R0
REPEAT:INC R0
MOV A,@R0

CJNE A,B,SKIP
//AJMP NEXT
SKIP:JC NEXT
MOV B,A
NEXT:DJNZ R1,REPEAT
STOP:AJMP STOP
END
```
## Assumne array of the ten byte is stored in internal memory of 8051 microcointroller from memory location 50h and store smallest number in register B

```asm
ORG 00H
MOV R1,05H
MOV R0,#50H
DEC R1
MOV B,@R0
REPEAT:INC R0
MOV A,@R0
CJNE A,B,SKIP
SKIP:JNC NEXT
MOV B,A
NEXT:DJNZ R1,REPEAT
STOP:AJMP STOP
END
```

# Practical NO 6. DATA EXCHNAGE PROGRAM 
## Transfer data from Register A to the Register B.
```asm
ORG 00H
MOV A,#0A5H
MOV B,#03CH
XCH A,B
END
```
## Exchnage dfata between Register A and memory location 60h
```asm
ORG 00H
MOV A,#55H
MOV 60H,#27H
XCH A,60H
END
```
## Exchnage the data between Register A and memory location 50h using indirect Addressing mode.
```asm
ORG 00H
MOV A,#50H
MOV 50H,#71H
MOV R0,#50H
XCH A,@R0
END
```

# Practical NO 7. INTERFACING
```asm
#include <reg51.h>
sbit LED = P1^2;
void delay(void);
int main(){				
P1 = 0x00;
while(1){
LED = 1;
delay();
LED = 0;
delay();
}
}
void delay(void){
int i,j;
for(i=0;i<100;i++){
for(j=0;j<1000;j++);
} 
}
```

# Practical NO 8.  
