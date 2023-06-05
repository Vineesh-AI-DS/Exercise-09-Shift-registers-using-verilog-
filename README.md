
# Experiment--09-Implementation-of Shift-registers-using-verilog-
### AIM: To implement PISO , PIPO,PISO  using verilog and validating their functionality using their functional tables
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 
Shift registers are basically of 4 types. These are:

Serial In Serial Out shift register
Serial In parallel Out shift register
Parallel In Serial Out shift register
Parallel In parallel Out shift register
Serial-In Serial-Out Shift Register (SISO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a serial output is known as Serial-In Serial-Out shift register. Since there is only one output, the data leaves the shift register one bit at a time in a serial pattern, thus the name Serial-In Serial-Out Shift Register.

The logic circuit given below shows a serial-in serial-out shift register. The circuit consists of four D flip-flops which are connected in a serial manner. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337366-540cc45e-11fe-4cce-9503-560dc704bc7d.png)
FIGURE -01 
erial-In Parallel-Out shift Register (SIPO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a parallel output is known as Serial-In Parallel-Out shift register.

The logic circuit given below shows a serial-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal is connected in addition to the clock signal to all the 4 flip flops in order to RESET them. The output of the first flip flop is connected to the input of the next flip flop and so on. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337438-03416c7e-7c9d-4939-ba34-c355b9fc79c5.png)
FIGURE-02
The above circuit is an example of shift right register, taking the serial data input from the left side of the flip flop and producing a parallel output. They are used in communication lines where demultiplexing of a data line into several parallel lines is required because the main use of the SIPO register is to convert serial data into parallel data.
Parallel-In Serial-Out Shift Register (PISO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and produces a serial output is known as Parallel-In Serial-Out shift register.

The logic circuit given below shows a parallel-in-serial-out shift register. The circuit consists of four D flip-flops which are connected. The clock input is directly connected to all the flip flops but the input data is connected individually to each flip flop through a multiplexer at the input of every flip flop. The output of the previous flip flop and parallel data input are connected to the input of the MUX and the output of MUX is connected to the next flip flop. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.
![image](https://user-images.githubusercontent.com/36288975/172337544-1632407f-1743-4b17-b480-00663d01e59f.png)
FIGURE-03
A Parallel in Serial out (PISO) shift register us used to convert parallel data to serial data.

Parallel-In Parallel-Out Shift Register (PIPO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and also produces a parallel output is known as Parallel-In parallel-Out shift register.

The logic circuit given below shows a parallel-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal and clock signals are connected to all the 4 flip flops. In this type of register, there are no interconnections between the individual flip-flops since no serial shifting of the data is required. Data is given as input separately for each flip flop and in the same way, output also collected individually from each flip flop![image](https://user-images.githubusercontent.com/36288975/172337661-babb1f90-6286-4d14-8cbd-26a380ee085e.png)
FIGURE-04
A Parallel in Parallel out (PIPO) shift register is used as a temporary storage device and like SISO Shift register it acts as a delay element.

### Procedure
```
1.Use quartus software and import required modules.
2.Assign inputs and outputs for shift registers.
3.Assign logic for input to give output at positive edge. 
4.Perform opertaions and produce rtl circuit.
5.End module
```


### PROGRAM 1:
```
Program for  Implementation-of Shift-registers-using-verilog-
Developed by: Vineesh.M
RegisterNumber: 212221230122 
```
```
module SIPO(c,si,po);
input c,si;
output [7:0] po;
reg [7:0] temp;
always @ (posedge c)
begin
temp = {temp[6:0],si};
end
assign po = temp;
endmodule 
```


### RTL LOGIC  REGISTERS   

![image](https://github.com/Vineesh-AI-DS/Exercise-09-Shift-registers-using-verilog-/assets/93427254/630d8f8c-4d6a-49c2-8b2f-abc7d03a75b9)





### TIMING DIGRAMS FOR SHIFT REGISTERS
![image](https://github.com/Vineesh-AI-DS/Exercise-09-Shift-registers-using-verilog-/assets/93427254/6072a0d7-7bf0-43b5-844e-9e6955eea8bd)


### PROGRAM 2:
``` 
mmodule PISO(Clk,Pin,load,so);
input load,Clk;
input [3:0] Pin;
output reg so;
reg [3:0] temp;
always @ (posedge Clk)
begin 
if(load)
temp <= Pin;
else
begin
so<=temp[3];
temp <={temp[2:0],1'b0};
end
end
endmodule
```
### RTL LOGIC  REGISTERS   


![image](https://github.com/Vineesh-AI-DS/Exercise-09-Shift-registers-using-verilog-/assets/93427254/f5b7950a-517e-43b3-87b5-312d179ddfb7)




### TIMING DIGRAMS FOR SHIFT REGISTERS

![image](https://github.com/Vineesh-AI-DS/Exercise-09-Shift-registers-using-verilog-/assets/93427254/508bf6d4-1e77-4d67-b7b2-ac688d4d2ba3)

### PROGRAM 3:
```
module PIPO (Po,Pi,clk);
input clk;
input[3:0] Pi;
output reg[3:0] Po;
always@(posedge clk)
begin
Po=Pi;
end 
endmodule
```
### RTL LOGIC  REGISTERS   
![image](https://github.com/Vineesh-AI-DS/Exercise-09-Shift-registers-using-verilog-/assets/93427254/89965887-7203-499a-9965-b42ae2ae0440)


### TIMING DIGRAMS FOR SHIFT REGISTERS


![image](https://github.com/Vineesh-AI-DS/Exercise-09-Shift-registers-using-verilog-/assets/93427254/badbc62c-86ef-4286-bda2-ab7fd492d2f7)



### RESULTS 
Thus the program to implement shift registers is done successful.
