*VERILOG CODE*
<br>module m41(
<br>&emsp;input a,
<br>&emsp;input b,
<br>&emsp;input c,
<br>&emsp;input d,
<br>&emsp;input s0,
<br>&emsp;input s1,
<br>&emsp;output out);
<br>&emsp;assign out = s1?(s0?d:c):(s0?b:a);
<br>endmodule

*TESTBENCH CODE*
<br>module m41_tb;
<br>&emsp;reg a;
<br>&emsp;reg b;
<br>&emsp;reg c;
<br>&emsp;reg d;
<br>&emsp;reg s0;
<br>&emsp;reg s1;
<br>&emsp;wire out;
<br>&emsp;m41 uut(.a(a),.b(b),.c(c),.d(d),.s0(s0),.s1(s1),.out(out));
<br>&emsp;initial begin
<br>&emsp;&emsp;$dumpfile("dump.vcd"); $dumpvars;
<br>&emsp;&emsp;a=1'b0;
<br>&emsp;&emsp;b=1'b0;
<br>&emsp;&emsp;c=1'b0;
<br>&emsp;&emsp;d=1'b0;
<br>&emsp;&emsp;s0=1'b0;
<br>&emsp;&emsp;s1=1'b0;
<br>&emsp;end
<br>&emsp;always #40 a = ~a;
<br>&emsp;always #20 b = ~b;
<br>&emsp;always #10 c = ~c;
<br>&emsp;always #5 d = ~d;
<br>&emsp;always #80 s0 = ~s0;
<br>&emsp;always #160 s1 = ~s1;
<br>endmodule

*O/P*
<img width="1256" alt="Screenshot 2023-08-16 at 5 06 51 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/f6b4f3c4-99cb-4477-b44b-09c3f3aa327b">


