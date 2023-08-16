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
<img width="1261" alt="Screenshot 2023-08-16 at 7 48 48 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/3a25d770-f0f4-48db-b29a-8e749421517d">
