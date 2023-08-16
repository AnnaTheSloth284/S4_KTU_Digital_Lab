*VERILOG CODE*
<br>module d_ff (d,clk,reset,q,q_bar);
<br>&emsp;input d;
<br>&emsp;input clk;
<br>&emsp;input reset;
<br>&emsp;output q,q_bar;
<br>&emsp;wire d,clk;
<br>&emsp;reg q,q_bar;

<br>&emsp;assign q_bar = ~q;

<br>&emsp;always @(posedge clk or posedge reset) 
<br>&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;if (reset) 
<br>&emsp;&emsp;&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;&emsp;&emsp;q <= 1'b0;
<br>&emsp;&emsp;&emsp;&emsp;end 
<br> &emsp;&emsp;&emsp;else
<br>&emsp;&emsp;&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;&emsp;&emsp;q <= d;
<br>&emsp;&emsp;&emsp;&emsp;end
<br>&emsp;&emsp;end
  
<br>endmodule

*TESTBENCH*
<br>module tb_dff;

<br>&emsp;reg d;
<br>&emsp;reg clk;
<br>&emsp;reg reset;
  
<br>&emsp;//Outputs
<br>&emsp;wire q;
<br>&emsp;wire q_bar;
  
<br>&emsp;d_ff uut (.d(d),.clk(clk),.reset(reset),.q(q),.q_bar(q_bar));
<br>&emsp;initial begin
<br>&emsp;&emsp;clk = 1;
<br>&emsp;&emsp;forever #100 clk = ~clk;
<br>&emsp;end
<br>&emsp;initial begin
<br>&emsp;&emsp;reset = 0; d=1'b0;
<br>&emsp;&emsp;#200 d=0; reset = 0;
<br>&emsp;&emsp;#200 d=1;reset = 0;
<br>&emsp;&emsp;#200 d=1;reset = 1;
<br>&emsp;end
<br>endmodule

*O/P*
<img width="1250" alt="Screenshot 2023-08-16 at 12 59 43 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/eaab3d94-7e41-47d9-a93a-60a6cbc96d6b">
