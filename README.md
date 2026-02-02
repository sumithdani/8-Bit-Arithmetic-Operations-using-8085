# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.

## Apparatus Required:
•	Laptop with internet connection

## Algorithm:

### For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
   
### Program:
```
LDA 1000H
MOV B,A
LDA 1001H
ADD B
STA 4300H
JC STORE_CARRY
HLT
STORE_CARRY:MVI A,01H
STA 4301H
HLT
```

### Output:
<img width="1488" height="772" alt="image" src="https://github.com/user-attachments/assets/54babfeb-cd10-4d07-9929-708f20b6adc9" />
<img width="288" height="438" alt="image" src="https://github.com/user-attachments/assets/0ec61322-3d48-4feb-bfdb-0d72d05fc293" /><img width="288" height="438" alt="image" src="https://github.com/user-attachments/assets/79f202ee-db26-4e41-bd65-77a0493ef293" />




### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
CMP C
JC SWAP
SWAP:
MOV B,A
MOV A,C
SUB B
STA 4300H
HLT
```

### Output:
<img width="870" height="498" alt="image" src="https://github.com/user-attachments/assets/8c6567d7-f006-46d0-8ca3-72c4059d739d" />
<img width="382" height="555" alt="image" src="https://github.com/user-attachments/assets/d28ce31f-6ac6-4138-9130-655dffe9747d" />
<img width="385" height="536" alt="image" src="https://github.com/user-attachments/assets/c46f52d7-d518-4db0-87ba-eed796458b88" />



### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B,A
MVI A,00H
LOOP:ADD C
DCR B
JNZ LOOP
STA 4300H
HLT
```



### Output:
<img width="1503" height="594" alt="image" src="https://github.com/user-attachments/assets/303af633-aafb-4752-919a-465f33e69242" />
<img width="877" height="607" alt="image" src="https://github.com/user-attachments/assets/aa21b1e0-2430-48c2-b33f-2b78a25b203a" />
<img width="752" height="605" alt="image" src="https://github.com/user-attachments/assets/137d4ea4-1140-47e2-a047-0ccae9cb99f5" />

### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B, A
MVI A, 00H
LOOP: CMP B
JC END
SUB B
INR A
JMP LOOP
END: STA 4300H
MOV A, C
STA 4301H
HLT
```


### Output:

## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

