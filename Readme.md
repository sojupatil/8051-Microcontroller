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
## TRAFFFIC LIGHT
 ```c
#include<reg51.h>
sbit NR = P2^0;
sbit NY = P2^1;
sbit NG	= P2^2;

sbit ER = P2^3;
sbit EY = P2^4;
sbit EG = P2^5;

sbit WR1 = P3^0;
sbit WY = P3^1;
sbit WG = P3^2;

sbit SR = P3^3;
sbit SY = P3^4;
sbit SG = P3^5;

void ydelay(void);
void gdelay(void);
void main(void)
{
P0 = 0x00;
P2 = 0x00;
//north green//
NG = 1;
ER = 1;
SR = 1;
WR1 = 1;
NY = 0;
NR = 0;
EG = 0;
EY = 0;
SG = 0;
SY = 0;
WG = 0;
WY = 0;
gdelay();
//north yellow//
NY = 1;
ER = 1;
SR = 1;
WR1 = 1;
NG = 0;	 
NR = 0;	
EG = 0;	   
EY = 0;
SG = 0;	  	
SY = 0;		
WG = 0;		 
WY = 0;			

ydelay();

//EAST GREEN//
EG = 1;
NR = 1;
SR = 1;
WR1 = 1;
NY = 0;
NG = 0;
ER = 0;
EY = 0;
SG = 0;
SY = 0;
WG = 0;
WY = 0;
gdelay();

//east yellow//

EY = 1;
NR = 1;
SR = 1;
WR1 = 1;
NY = 0;
NG = 0;
ER = 0;
EG = 0;
SG = 0;
SY = 0;
WG = 0;
WY = 0;
ydelay();

//south green//
SG = 1;
ER = 1;
NR = 1;
WR1 = 1;
NY = 0;
NG = 0;
EG = 0;
EY = 0;
SR = 0;
SY = 0;
WG = 0;
WY = 0;
gdelay();

//south yellow//
SY = 1;
ER = 1;
NR = 1;
WR1 = 1;
NY = 0;
NG = 0;
EG = 0;
EY = 0;
SG = 0;
SR = 0;
WG = 0;
WY = 0;
ydelay();

//west green//
WG = 1;
ER = 1;
SR = 1;
NR = 1;
NY = 0;
NG = 0;
EG = 0;
EY = 0;
SG = 0;
SY = 0;
WY = 0;
WR1 = 0;
gdelay();

//west yellow//
WY = 1;
ER = 1;
SR = 1;
NR = 1;
NY = 0;
NG = 0;
EG = 0;
EY = 0;
SG = 0;
SY = 0;
WG = 0;
WR1 = 0;
ydelay();
}
void ydelay(void)
{
int i,j;
for(i=0;i<400;i++)
{
for(j=0;j<1000;j++);
}
}
void gdelay(void)
{
int i,j;
for(i=0;i<600;i++)
{
for(j=0;j<1000;j++);
}
}
```

# Practical NO 9.
## LCD 
```c
 #include<reg51.h>
sbit rs=P1^0;
sbit rw=P1^1;
sbit en=P1^2;
void lcd_cmd(char c);
void lcd_data(char d);
void lcd_string(char*s);
void delay(void);
void main(void)
{
P2=0x00;
while(1)
{
lcd_cmd(0x38);
lcd_cmd(0x0c);
lcd_cmd(0x01);
lcd_cmd(0x80);
lcd_string("Hello Students!");
lcd_cmd(0xc0);
lcd_string("!!welcome");
}
}
void lcd_cmd(char c)
{
rw=0;
P2=c;
delay();
rs=0;
en=1;
en=0;
}
void lcd_data(char d)
{
rw=0;
P2=d;
delay();
rs=1;
en=1;
en=0;
}
void lcd_string(char*s)
{
while(*s)
{
lcd_data(*s++);
}
}
void delay(void)
{
int i,j;
for(i=0;i<100;i++)
{
for(j=0;j<1000;j++);
}
}
```

# Practical NO 10.
## LED WITH SWITCH 
```C
  #include <reg51.h>

sbit LED = P2^0;      
sbit switch_pin = P0^1; 

void delay(void) 
{
    unsigned int i, j;
    for(i = 0; i <100; i++)
        for(j = 0; j < 1275; j++);  
}

void main(void)
 {
    switch_pin = 0;  
    LED = 0;        
    while(1) 
    {
        if (switch_pin == 0) 
        { 
            delay();       
          
               // Confirm press
                LED = 0;        
            
        }
         else 
        {
            LED = 1;            
        }
    }
}
```
# Practical NO 11.
## STEPPER MOTOR 
```c
#include<reg51.h>
void ms_delay(unsigned int t) 
{
unsigned i,j ;
for(i=0;i<t;i++)	
}
void main()
{
while(1) 
{
P2=0x0C;	
P2=0x06;	
P2=0x03;	
P2=0x09;	
}
```

# Practical NO 12.
## Interfacing of Dc motor 

```c
#include <reg51.h>

// Define motor control pins
sbit EN1 = P0^0;   
sbit IN1 = P0^1;  
sbit IN2 = P0^2;  

// Delay function
void delay() {
    int i, j;
    for(i = 0; i < 100; i++) {
        for(j = 0; j < 1000; j++);
    }
}

void main() {
    EN1 = 1;  
    while(1) {
        IN1 = 1;
        IN2 = 0;
        delay();

        IN1 = 0;
        IN2 = 1;
        delay();
    }
}
```
