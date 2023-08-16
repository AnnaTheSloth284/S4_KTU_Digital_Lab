*VERILOG CODE*
<br>module t_ff (t,clk,reset,q);
<br>&emsp;input t;
<br>&emsp;input clk;
<br>&emsp;input reset;
<br>&emsp;output q;
<br>&emsp;wire t,clk;
<br>&emsp;reg q;

<br>&emsp;always @(posedge clk) 
<br>&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;if (!reset) 
<br>&emsp;&emsp;&emsp;&emsp;q <= 0;
<br> &emsp;&emsp;&emsp;else
<br>&emsp;&emsp;&emsp;&emsp;if(t)
<br>&emsp;&emsp;&emsp;&emsp;&emsp;q <= ~q;
<br>&emsp;&emsp;&emsp;&emsp;else
<br>&emsp;&emsp;&emsp;&emsp;&emsp;q <= q;
<br>&emsp;&emsp;end
  
<br>endmodule

*TESTBENCH*
<br>module tb_tff;

<br>&emsp;reg t;
<br>&emsp;reg clk;
<br>&emsp;reg reset;
  
<br>&emsp;//Outputs
<br>&emsp;wire q;
  
<br>&emsp;t_ff uut (.d(d),.clk(clk),.reset(reset),.q(q));
<br>&emsp;initial begin
<br>&emsp;&emsp;clk = 1;
<br>&emsp;&emsp;forever #50 clk = ~clk;
<br>&emsp;end
<br>&emsp;initial begin
<br>&emsp;&emsp;reset = 0; t = 1;
<br>&emsp;&emsp;#100 reset = 0; t = 1;
<br>&emsp;&emsp;#200 reset = 1; t = 1;
<br>&emsp;&emsp;#200 reset = 1; t = 0;
<br>&emsp;&emsp;#200 reset = 1; t = 1;
<br>&emsp;&emsp;#200 reset = 1; t = 1;
<br>&emsp;end
<br>endmodule

*O/P*
<img width="1379" alt="Screenshot 2023-08-16 at 1 17 50 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/15c46a6f-b8cb-4afc-aa75-11a8b3b18154">
