*VERILOG CODE*
<br>module ring_counter(Clock,Reset,Count_out);
<br>  &emsp;input Clock;
<br>  &emsp;input Reset;
<br>  &emsp;output [3:0] Count_out;
<br>  &emsp;reg [3:0] Count_temp;
<br>  &emsp;always @(posedge Clock or posedge Reset)
<br>  &emsp;&emsp;begin
<br>  &emsp;&emsp;&emsp;if(Reset==1'b1)
<br>  &emsp;&emsp;&emsp;&emsp;begin
<br>  &emsp;&emsp;&emsp;&emsp;&emsp;Count_temp = 4'b0001;
<br>  &emsp;&emsp;&emsp;&emsp;end
<br>  &emsp;&emsp;&emsp;else if(Clock==1'b1)
<br>  &emsp;&emsp;&emsp;&emsp;begin
<br>  &emsp;&emsp;&emsp;&emsp;&emsp;Count_temp = {Count_temp[2:0],~Count_temp[3]};
<br>  &emsp;&emsp;&emsp;&emsp;end
<br>  &emsp;&emsp;end
<br>  &emsp;assign Count_out = Count_temp;
<br>endmodule

*TESTBENCH*
<br>module tb_ring;
<br>&emsp;reg Clock;
<br>&emsp;reg Reset;
<br>&emsp;wire[3:0]Count_out;
<br>&emsp;ring_counter uut(.Clock(Clock),.Reset(Reset),.Count_out(Count_out));
<br>&emsp;initial begin
<br>&emsp;&emsp;Clock=0;
<br>&emsp;&emsp;Reset=1;
<br>&emsp;&emsp;#50;
<br>&emsp;&emsp;Reset=0;
<br>&emsp;&emsp;Clock=0; *//Initial clock value*
<br>&emsp;&emsp;repeat (10) begin
<br>&emsp;&emsp;&emsp;#25 Clock=~Clock; *//Toggle the clock every 25 time units*
<br>&emsp;&emsp;end
<br>&emsp;&emsp;$finish; *//End Simulation*


<br>&emsp;end
<br>endmodule

*O/P*
<img width="1416" alt="Screenshot 2023-08-16 at 11 36 17 AM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/252abf1b-b458-4629-8991-3cd3e726ea9b">
