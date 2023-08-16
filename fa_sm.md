*VERILOG CODE*
<br>module fulladderSM1(a,b,c,sum,carry);
<br>&emsp;input a;
<br>&emsp;input b;
<br>&emsp;input c;
<br>&emsp;output sum;
<br>&emsp;output carry;
<br>&emsp;wire ha1_sum;
<br>&emsp;wire ha1_carry;
<br>&emsp;wire ha2_carry;
<br>&emsp;wire sum;
<br>&emsp;wire carry;
<br>&emsp;halfadder ha1 (a,b,ha1_sum,ha1_carry);
<br>&emsp;halfadder ha2 (ha1_sum,c,sum,ha2_carry);
<br>&emsp;or(ha1_carry, ha2_carry, carry);
<br>endmodule

<br>module halfadder(
<br>&emsp;&emsp;input a,
<br>&emsp;&emsp;input b,
<br>&emsp;&emsp;output sum ,
<br>&emsp;&emsp;output carry
<br>&emsp;);
<br>&emsp;assign sum  = a ^ b;
<br>&emsp;assign carry = a & b;
<br>endmodule

*TESTBENCH CODE*
<br>module fulladderSM1_tb;
<br>&emsp;// Inputs
<br>&emsp;reg a;
<br>&emsp;reg b;
<br>&emsp;reg c;
<br>&emsp;// Outputs
<br>&emsp;wire sum;
<br>&emsp;wire carry;
<br>&emsp;// Instantiate the Unit Under Test (UUT)
<br>&emsp;fulladderSM1 uut (.a(a), .b(b), .c(c), .sum(sum), .carry(carry));
<br>&emsp;initial begin
<br>&emsp;&emsp;$dumpfile("dump.vcd"); $dumpvars;
<br>&emsp;&emsp;// Initialize Inputs
<br>&emsp;&emsp;a = 0;
<br>&emsp;&emsp;b = 0;
<br>&emsp;&emsp;c = 0;
<br>&emsp;&emsp;// Wait 100 ns for global reset to finish
<br>&emsp;&emsp;#100; a=0;b=0;c=1;
<br>&emsp;&emsp;#100 a=0;b=1;c=0;
<br>&emsp;&emsp;#100 a=0;b=1;c=1;
<br>&emsp;&emsp;#100 a=1;b=0;c=0;
<br>&emsp;&emsp;#100 a=1;b=0;c=1;
<br>&emsp;&emsp;#100 a=1;b=1;c=0;
<br>&emsp;&emsp;#100 a=1;b=1;c=1;
<br>&emsp;&emsp;#100 ;
<br>&emsp;end
<br>endmodule 

*O/P*

