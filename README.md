# VLSI LAB EXPERIMENTS-03
# SIMULATION AND IMPLEMENTATION OF MULTIPLIER
## AIM: 
To simulate and synthesis Multiplier using VIVADO

## APPARATUS REQUIRED:
VIVADO 2023.2

## PROCEDURE:
 STEP:1 Start the Vivado, Select and Name the New project.
 
 STEP:2 Select the device family, device, package and speed. 
 
 STEP:3 Select new source in the New Project and select Verilog Module as the Source type.
 
 STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.
 
 STEP:5 Select the Behavioural Simulation in the Source Window and click the check syntax.
 
 STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

 ## 2Bit Multiplier
 ![image](https://github.com/Sricharumathy/Experiment-03-vlsi-/assets/159044760/74bc8099-d378-4ca7-9e6c-68e157dd735f)
 ## Program
 ```
module HA(a, b, s, c);
input a, b;
output s, c;
assign s=a ^ b;
assign c=a & b;
endmodule
module multiplier_2(a, b, c);
input [1:0] a, b;
output [3:0] c;
wire w1;
assign c[0]=a[0] & b[0];
HA h1(a[0] & b[1], a[1] & b[0], c[1], w1);
HA h2(a[1] & b[1], w1, c[2], c[3]);
endmodule
```
## Output
![image](https://github.com/Sricharumathy/Experiment-03-vlsi-/assets/159044760/f29dd6df-623b-4bca-8f36-6dc51e76349a)

## 4Bit Multiplier
![image](https://github.com/Sricharumathy/Experiment-03-vlsi-/assets/159044760/0b06e3d1-fa51-44d3-926c-2900243e3e66)
## Program
```
module HA(a,b,sum,carry);
input a,b;
output sum,carry;
assign sum=a^b;
assign carry=a&b;
endmodule
module FA(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
assign sum=a^b^c;
assign carry=(a&b)|(b&c)|(c&a);
endmodule
module mul_4b(a,b,p);
input[3:0]a,b;
output [7:0]p;
wire [17:1]c,s;
assign p[0]=a[0]&b[0];
HA h1(a[1]&b[0],a[0]&b[1],p[1],c[1]);
FA f1(a[2]&b[0],a[1]&b[1],c[1],s[1],c[2]);
FA f2(a[3]&b[0],a[2]&b[1],c[2],s[2],c[3]);
HA h2(a[3]&b[1],c[3],s[3],c[4]);
HA h3(a[0]&b[2],s[1],p[2],c[5]);
FA f3(a[1]&b[2],c[5],s[2],s[4],c[6]);
FA f4(a[2]&b[2],s[3],c[6],s[5],c[7]);
FA f5(a[3]&b[2],c[4],c[7],s[6],c[8]);
HA h4(a[0]&b[3],s[4],p[3],c[9]);
FA f6(a[1]&b[3],s[5],c[9],p[4],c[10]);
FA f7(a[2]&b[3],s[6],c[10],p[5],c[11]);
FA f8(a[3]&b[3],c[8],c[11],p[6],p[7]); 
endmodule
```

## Output
#![image](https://github.com/Sricharumathy/Experiment-03-vlsi-/assets/159044760/66883bf8-04b2-4481-969b-cf124f3df8d3)

## Result:
Thus, The 2 Bit and 4 Bit Multiplier are simulated successfully.









