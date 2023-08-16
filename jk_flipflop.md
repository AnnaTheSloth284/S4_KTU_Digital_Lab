*VERILOG CODE*
<br>module jk_ff (j,k,clk,reset,q,q_bar);
<br>&emsp;input j,k;
<br>&emsp;input clk;
<br>&emsp;input reset;
<br>&emsp;output q,q_bar;
<br>&emsp;wire j,k,clk;
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
<br>&emsp;&emsp;&emsp;&emsp;&emsp;case({j,k})
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;{1'b0,1'b0}:begin q=q;q_bar=q_bar;end
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;{1'b0,1'b1}:begin q=1'b0;q_bar=1'b1;end
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;{1'b1,1'b0}:begin q=1'b1;q_bar=1'b0;end
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;{1'b1,1'b1}:begin q=~q;q_bar=~q_bar;end
<br>&emsp;&emsp;&emsp;&emsp;&emsp;endcase
<br>&emsp;&emsp;&emsp;&emsp;end
<br>&emsp;&emsp;end
  
<br>endmodule

*TESTBENCH*
<br>module tb_jkff;

<br>&emsp;reg j;
<br>&emsp;reg k;
<br>&emsp;reg clk;
<br>&emsp;reg reset;
  
<br>&emsp;//Outputs
<br>&emsp;wire q;
<br>&emsp;wire q_bar;
  
<br>&emsp;sr_ff uut (.j(j),.k(k),.clk(clk),.reset(reset),.q(q),.q_bar(q_bar));
<br>&emsp;initial begin
<br>&emsp;&emsp;clk = 1;
<br>&emsp;&emsp;forever #50 clk = ~clk;
<br>&emsp;end
<br>&emsp;initial begin
<br>&emsp;&emsp;s=1'b1; r=1'b0; reset = 0;
<br>&emsp;&emsp;#100 reset = 0; j=1'b1; k=1'b0;
<br>&emsp;&emsp;#100 reset = 0; j=1'b0; k=1'b1;
<br>&emsp;&emsp;#100 reset = 0; j=1'b0; k=1'b0;
<br>&emsp;&emsp;#100 reset = 0; j=1'b1; k=1'b0;
<br>&emsp;end
<br>endmodule

*O/P*
