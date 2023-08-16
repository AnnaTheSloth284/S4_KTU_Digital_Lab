*VERILOG CODE*
<br>module or1(input a, input b, output y);
<br>&emsp;assign y = a|b;
<br>end

*TESTBENCH CODE*
<br>module or1_tb;
<br>&emsp;reg a;
<br>&emsp;reg b;
<br>&emsp;wire y;
<br>&emsp;or1 uut(.a(a),.b(b),.y(y));
<br>&emsp;initial begin
<br>&emsp;&emsp;a=0;b=0;
<br>&emsp;&emsp;#100 a=0;b=1;
<br>&emsp;&emsp;#100 a=1;b=0;
<br>&emsp;&emsp;#100 a=1;b=1;
<br>&emsp;end
<br>endmodule

*O/P*
<img width="817" alt="Screenshot 2023-08-16 at 7 55 05 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/da30c560-4a7e-4f58-b757-e81a29184861">
