# verilogcodes

Lab #3: Arithmetic and Logic Unit (ALU)
In this lab you are required to implement an ALU on the FPGA board.
The ALU is an integral part of a processor in a computer that carries out the execution of various instructions. It performs Arithmetic operations as well as Logic operations on the two inputs and produces the output. 
The ALU is represented by the following.
 
A and B are two operands. In this lab, we shall take these two operands as 4-bit wide. R is the output of the computation and is also a 4-bit wide.
F is the function that is to be performed by the ALU and is 4-bit wide for this lab. D is the collection of two output bits D1D0. D0 bit is set to 1 if R is ‘4’b0000’. It remains 0 otherwise. D1 bit is set as given in the table below (it roughly represents the Carry out)
For the lab you shall be required to implement the following operations.
Function Code (F)	Operation to perform	D1
4’b0000	R = A	0
4’b0001	R = –A (Use 2’s complement representation only)	if A is -8 (i.e. 4’b1000), the output R shall not be correct and hence D1 is set to 1 to indicate overflow.
4’b0010	R = A + B	D1 is Carry out of the summation
4’b0011	R = A – B	D1 is 1 if A – B can not be represented in 4 bits (i.e. there is a borrow into the 4th bit)
4’b0100	R = 2 * A (aka arithmetic shift to left by one bit)	D1 is set to 1 if 2*A can not be represented in 4 bit.
4’b0101	R= ⌊A/2⌋ (aka arithmetic shift to right by one bit)	0
4’b0110	R=A+1 	D1 is Carry out of the summation
4’b0111	R=A-1	D1 is 1 if the A-1 can not be represented in 4 bits.
4’b1000	R=~A	0
4’b1001	R=A&B	0
4’b1010	R=A|B	0
4’b1011	R=A⊕B	0
4’b1100	R=A≪1	0
4’b1101	R=A≫1	0
4’b1110	R=A	0
4’b1111	R=4^' b1111	0

You must make the following module declaration.
module ALU(input A[3:0], input B[3:0], input F[3:0], output R[3:0], output D[1:0]);
…
Input and output
Set A on switches SW3 to SW6 (SW3 carrying the least significant bit of A).
Set B on switches SW7 to SW10 (SW7 carrying the least significant bit of B).
Set F on switches SW11 to SW14 (SW11 carrying the least significant bit to F).
For output use the seven segment display to show R as a hex digit on the 7 segment display with EN0.
The output D0 to be set on the DP signal of the 7-segment display.
Output D1 to be set on the LED LD0 on the board.
Procedure.
	First write the code and a test bench.
	Simulate the code using the test bench and see if the outputs appear as desired.
	Define the UCF file for the input output as described above. Synthesize your code for the FPGA and download the bit file on the FPGA. You will not be able to synthesize the test bench as it is not a synthesizable construct.
	Try out various switch combinations to see if the output is as indicated as in the table above. Must ensure that you get all combination on D0 and D1 bits with various inputs of A, B and F.
