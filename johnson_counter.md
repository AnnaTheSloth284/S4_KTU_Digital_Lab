*VERILOG CODE*

module johnson_counter(Clock,Reset,Count_out);

  input Clock;
  
  input Reset;
  output [3:0] Count_out;
  reg [3:0] Count_temp;
  always @(posedge(Clock) or Reset)
    begin
      if(Reset==1'b1)
        begin
          Count_temp=4'b0000;
        end
      else if(Clock==1'b1)
        begin
          Count_temp = {Count_temp[2:0],~Count_temp[3]};
        end
    end
  assign Count_out = Count_temp;
endmodule

*TESTBENCH*
module tb_johnson;
  reg Clock;
  reg Reset;
  wire[3:0]Count_out;
  johnson_counter uut(.Clock(Clock),.Reset(Reset),.Count_out(Count_out));
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars(1);
    Clock=1;
    forever #50 Clock=~Clock;
  end
  initial begin
    Reset=1;
    #50;
    Reset=0;
  end
endmodule

*O/P*
<img width="1413" alt="Screenshot 2023-08-16 at 11 09 58 AM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/85013c2c-a3c0-4b32-b377-dd3603b0cda0">
