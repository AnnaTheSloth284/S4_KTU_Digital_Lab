*VERILOG CODE*
<br>module johnson_counter(Clock,Reset,Count_out);
<br>  input Clock;
<br>  input Reset;
<br>  output [3:0] Count_out;
<br>  reg [3:0] Count_temp;
<br>  always @(posedge(Clock) or Reset)
<br>   begin
<br>      if(Reset==1'b1)
<br>        begin
<br>          Count_temp=4'b0000;
<br>        end
<br>      else if(Clock==1'b1)
<br>        begin
<br>          Count_temp = {Count_temp[2:0],~Count_temp[3]};
<br>        end
<br>    end
<br>  assign Count_out = Count_temp;
<br>endmodule

*TESTBENCH*
<br>module tb_johnson;
<br>  reg Clock;
<br>  reg Reset;
<br>  wire[3:0]Count_out;
<br>  johnson_counter uut(.Clock(Clock),.Reset(Reset),.Count_out(Count_out));
<br>  initial begin
<br>    $dumpfile("dump.vcd");
<br>    $dumpvars(1);
<br>    Clock=1;
<br>    forever #50 Clock=~Clock;
<br>  end
<br>  initial begin
<br>    Reset=1;
<br>    #50;
<br>    Reset=0;
<br>  end
<br>endmodule

*O/P*
<img width="1413" alt="Screenshot 2023-08-16 at 11 09 58 AM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/85013c2c-a3c0-4b32-b377-dd3603b0cda0">
