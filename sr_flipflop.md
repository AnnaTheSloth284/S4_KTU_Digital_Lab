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
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;endcase
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;end
<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;end
  
<br>endmodule
