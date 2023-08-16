*VERILOG CODE*
<br>module not1(input a, output y);
<br>&emsp;assign y = ~a;
<br>endmodule

*TESTBENCH CODE*
<br>module not1_tb;
<br>&emsp;reg a;
<br>&emsp;wire y;
<br>&emsp;not1 uut(.a(a),.y(y));
<br>&emsp;initial begin
<br>&emsp;&emsp;a=0;
<br>&emsp;&emsp;#100 a=1;
<br>&emsp;end
<br>endmodule

*O/P*
<img width="932" alt="Screenshot 2023-08-16 at 7 59 43 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/535bce22-614d-411f-8c32-a472c8213862">
