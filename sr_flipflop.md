*VERILOG CODE*
<br>module sr_ff (s,r,clk,reset,q,q_bar);
<br>&emsp;input s,r;
<br>&emsp;input clk;
<br>&emsp;input reset;
<br>&emsp;output q,q_bar;
<br>&emsp;wire s,r,clk;
<br>&emsp;reg q,q_bar;

<br>&emsp;always @(posedge clk) 
<br>&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;if (reset) 
<br>&emsp;&emsp;&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;&emsp;&emsp;q = 1'b0;
<br>&emsp;&emsp;&emsp;&emsp;&emsp;q_bar = 1'b1;
<br>&emsp;&emsp;&emsp;&emsp;end 
<br> &emsp;&emsp;&emsp;else
<br>&emsp;&emsp;&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;&emsp;&emsp;case({s,r})
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;{1'b0,1'b0}:begin q=q;q_bar=q_bar;end
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;{1'b0,1'b1}:begin q=1'b0;q_bar=1'b1;end
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;{1'b1,1'b0}:begin q=1'b1;q_bar=1'b0;end
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;{1'b1,1'b1}:begin q=1'bx;q_bar=1'bx;end
<br>&emsp;&emsp;&emsp;&emsp;&emsp;endcase
<br>&emsp;&emsp;&emsp;&emsp;end
<br>&emsp;&emsp;end
  
<br>endmodule

*TESTBENCH*
<br>module tb_srff;

<br>&emsp;reg s;
<br>&emsp;reg r;
<br>&emsp;reg clk;
<br>&emsp;reg reset;
  
<br>&emsp;//Outputs
<br>&emsp;wire q;
<br>&emsp;wire q_bar;
  
<br>&emsp;sr_ff uut (.s(s),.r(r),.clk(clk),.reset(reset),.q(q),.q_bar(q_bar));
<br>&emsp;initial begin
<br>&emsp;&emsp;clk = 1;
<br>&emsp;&emsp;forever #50 clk = ~clk;
<br>&emsp;end
<br>&emsp;initial begin
<br>&emsp;&emsp;s=1'b1; r=1'b0; reset = 0;
<br>&emsp;&emsp;#100 reset = 0; s=1'b1; r=1'b0;
<br>&emsp;&emsp;#100 reset = 1; s=1'b0; r=1'b1;
<br>&emsp;&emsp;#100 reset = 0; s=1'b0; r=1'b0;
<br>&emsp;&emsp;#100 reset = 0; s=1'b1; r=1'b0;
<br>&emsp;end
<br>endmodule

*O/P*
<img width="1254" alt="Screenshot 2023-08-16 at 12 45 53 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/10746951-c4a9-4d6b-b087-d9034cecfc4f">
