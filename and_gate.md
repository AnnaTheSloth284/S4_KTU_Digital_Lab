*VERILOG CODE*
<br>module and1(input a, input b, output y);
<br>&emsp;assign y = a&b;
<br>end

*TESTBENCH CODE*
<br>module and1_tb;
<br>&emsp;reg a;
<br>&emsp;reg b;
<br>&emsp;wire y;
<br>&emsp;and1 uut(.a(a),.b(b),.y(y));
<br>&emsp;initial begin
<br>&emsp;&emsp;a=0;b=0;
<br>&emsp;&emsp;#100 a=0;b=1;
<br>&emsp;&emsp;#100 a=1;b=0;
<br>&emsp;&emsp;#100 a=1;b=1;
<br>&emsp;end
<br>endmodule

*O/P*
