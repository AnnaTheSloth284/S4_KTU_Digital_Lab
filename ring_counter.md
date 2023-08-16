*VERILOG CODE*
<br>module ring_counter(Clock,Reset,Count_out);
<br>  &emsp;input Clock;
<br>  &emsp;input Reset;
<br>  &emsp;output [3:0] Count_out;
<br>  &emsp;reg [3:0] Count_temp;
<br>  &emsp;always @(posedge(Clock),Reset)
<br>  &emsp;&emsp;begin
<br>  &emsp;&emsp;&emsp;if(Reset==1'b1)
<br>  &emsp;&emsp;&emsp;&emsp;begin
<br>  &emsp;&emsp;&emsp;&emsp;&emsp;Count_temp = 4'b0001;
<br>  &emsp;&emsp;&emsp;&emsp;end
<br>  &emsp;&emsp;&emsp;else if(Clock==1'b1)
<br>  &emsp;&emsp;&emsp;&emsp;begin
<br>  &emsp;&emsp;&emsp;&emsp;&emsp;Count_temp = {Count_temp[0],Count_temp[3:1]}; 
<br>  &emsp;&emsp;&emsp;&emsp;end
<br>  &emsp;&emsp;end
<br>  &emsp;assign Count_out = Count_temp;
<br>endmodule

*TESTBENCH*
<br>module tb_ring;
<br>&emsp;reg Clock;
<br>&emsp;reg Reset;
<br>&emsp;wire [3:0] Count_out;
<br>&emsp;ring_counter uut(.Clock(Clock),.Reset(Reset),.Count_out(Count_out));
<br>&emsp;initial begin
<br>&emsp;&emsp;Clock = 1;
<br>&emsp;&emsp;forever #50 Clock = ~Clock;
<br>&emsp;&emsp;end
<br>&emsp;initial begin
<br>&emsp;&emsp;Reset = 1;
<br>&emsp;&emsp;#50
<br>&emsp;&emsp;Reset = 0;
<br>&emsp;&emsp;end
<br>endmodule

*O/P*
<img width="1260" alt="Screenshot 2023-08-16 at 9 22 59 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/105f38f5-8636-4337-870b-2b076e17da1e">
