*VERILOG CODE*
<br>module Demultiplexer_1_to_4_case (output reg [3:0] Y, input [1:0] A, input din);
<br>&emsp;always @ (Y,A)
<br>&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;case(A)
<br>&emsp;&emsp;&emsp;&emsp;2'b00: begin Y[0] = din; Y[3:1] = 0; end
<br>&emsp;&emsp;&emsp;&emsp;2'b01: begin Y[1] = din; Y[0] = 0; end
<br>&emsp;&emsp;&emsp;&emsp;2'b10: begin Y[2] = din; Y[1:0] = 0; end
<br>&emsp;&emsp;&emsp;&emsp;2'b11: begin Y[3] = din; Y[2:0] = 0; end
<br>&emsp;&emsp;&emsp;endcase
<br>&emsp;&emsp;end
<br>endmodule

*TESTBENCH CODE*
<br>module Demultiplexer_1_to_4_case_tb;
<br>&emsp;wire [3:0] Y;
<br>&emsp;reg [1:0] A;
<br>&emsp;reg din;
<br>&emsp;Demultiplexer_1_to_4_case I0 (Y, A, din);

<br>&emsp;initial begin
<br>&emsp;&emsp;$dumpfile("dump.vcd"); $dumpvars;
<br>&emsp;&emsp;din = 1;
<br>&emsp;&emsp;A = 2'b00;
<br>&emsp;&emsp;#100 A = 2'b01;
<br>&emsp;&emsp;#100 A = 2'b10;
<br>&emsp;&emsp;#100 A = 2'b11;
<br>&emsp;end

<br>&emsp;initial begin
<br>&emsp;$monitor("%t| Din = %d| A[1] = %d| A[0] = %d| Y[0] = %d| Y[1] = %d| Y[2] = %d| Y[3] = %d",$time, din, A[1], A[0], Y[0], Y[1], Y[2], Y[3]);
<br>&emsp;end
<br>endmodule

*O/P*
<img width="1150" alt="Screenshot 2023-08-16 at 8 45 46 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/8ec63c15-7fe3-4edb-9241-c8635ebe0b85">
