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
<img width="288" height="438" alt="image" src="https://github.com/user-attachments/assets/0ec61322-3d48-4feb-bfdb-0d72d05fc293" />
<img width="273" height="433" alt="image" src="https://github.com/user-attachments/assets/577dcf33-7d2d-4511-823c-ec43407e0545" />

### Verification:
![WhatsApp Image 2026-02-02 at 17 55 43](https://github.com/user-attachments/assets/ced840fb-bd57-413a-a270-72ba0cd86f5c)



### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:
```
LDA 1000H
MOV C,A
LDA 1001H
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
<img width="1445" height="692" alt="image" src="https://github.com/user-attachments/assets/b014df40-a4b9-4d04-b1bc-b37e2171cb12" />
<img width="283" height="438" alt="image" src="https://github.com/user-attachments/assets/2bd59a04-e45a-4fd3-81b7-4f41b0c0ffa7" />
<img width="293" height="438" alt="image" src="https://github.com/user-attachments/assets/a233f747-6734-4a3b-85ec-1a0e5c311e3d" />

### Verification:
![WhatsApp Image 2026-02-02 at 18 01 32](https://github.com/user-attachments/assets/56f22adf-0fad-46fc-b590-10f8860410bc)



### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
```
LDA 1000H
MOV C,A
LDA 1001H
MOV B,A
MVI A,00H
LOOP:ADD C
DCR B
JNZ LOOP
STA 4300H
HLT
```



### Output:
<img width="1421" height="519" alt="image" src="https://github.com/user-attachments/assets/befc0cc3-acb1-44fa-be0f-6a3b4b3774ce" />
<img width="273" height="425" alt="image" src="https://github.com/user-attachments/assets/a25d7d58-5592-463c-bffd-4dd50b9dee99" />
<img width="273" height="404" alt="image" src="https://github.com/user-attachments/assets/78b75a40-139c-454a-bd22-dc92c64a3482" />

### Verification:
![WhatsApp Image 2026-02-02 at 18 44 22](https://github.com/user-attachments/assets/412083a0-c314-47b6-b62b-2ed5c763c470)


### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:
```
LDA 1000H
MOV C, A
LDA 1001H
MOV B, A
ORA A         
JZ END         
MVI D, 00H
LOOP: MOV A, C
CMP B
JC END
SUB B
MOV C, A
INR D
JMP LOOP
END:  MOV A, D
STA 4300H
MOV A, C
STA 4301H
HLT
```


### Output:
<img width="1439" height="867" alt="image" src="https://github.com/user-attachments/assets/0cebc40b-3593-48df-b2cc-3d41b0b4a430" />
<img width="277" height="412" alt="image" src="https://github.com/user-attachments/assets/422db57c-8267-4081-8f7a-75ac9b434486" />
<img width="277" height="423" alt="image" src="https://github.com/user-attachments/assets/65834d1c-d24b-4aea-8a52-2ecfa3a8a315" />

### Verification:
![WhatsApp Image 2026-02-02 at 18 48 53](https://github.com/user-attachments/assets/6870b0e3-ff8e-46ce-bbe8-e6981595ef65)



## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

