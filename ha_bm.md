*VERILOG CODE*
<br>module ha_dm1(input a, input b, output s, output c);
<br>&emsp;reg s,c;
<br>&emsp;always @(a,b)
<br>&emsp;begin
<br>&emsp;&emsp;if(a==0 & b==0)
<br>&emsp;&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;&emsp;s=0;c=0;
<br>&emsp;&emsp;&emsp;end

<br>&emsp;&emsp;if(a==0 & b==1)
<br>&emsp;&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;&emsp;s=1;c=0;
<br>&emsp;&emsp;&emsp;end

<br>&emsp;&emsp;if(a==1 & b==0)
<br>&emsp;&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;&emsp;s=1;c=0;
<br>&emsp;&emsp;&emsp;end

<br>&emsp;&emsp;if(a==1 & b==1)
<br>&emsp;&emsp;&emsp;begin
<br>&emsp;&emsp;&emsp;&emsp;s=0;c=1;
<br>&emsp;&emsp;&emsp;end
<br>&emsp;end
<br>endmodule


*O/P*
<img width="1229" alt="Screenshot 2023-08-16 at 8 04 47 PM" src="https://github.com/AnnaTheSloth284/S4_KTU_Digital_Lab/assets/112563080/5a659eb7-e81b-4a88-bf1a-c666dd2e3b4b">
