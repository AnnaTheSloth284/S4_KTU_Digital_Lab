*VERILOG CODE*
<br>module ha_dm1(input a, input b, output s, output c);
<br>&emsp;assign s = a^b;
<br>&emsp;assign c = a&b;
<br>endmodule

*TESTBENCH CODE*
<br>module ha_dm1_tb;
<br>&emsp;reg a;
<br>&emsp;reg b;
<br>&emsp;wire s;
<br>&emsp;wire c;
<br>&emsp;ha_dm1 uut(.a(a),.b(b),.s(s),.c(c));
<br>&emsp;initial begin
<br>&emsp;&emsp;a=0;b=0;
<br>&emsp;&emsp;#100 a=0;b=1;
<br>&emsp;&emsp;#100 a=1;b=0;
<br>&emsp;&emsp;#100 a=1;b=1;
<br>&emsp;end
<br>endmodule

*O/P*
<img width="1229" alt="Screenshot 2023-08-16 at 8 04 47 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/db0ff5ea-0397-4f13-b8f3-6228c38ae1af">
