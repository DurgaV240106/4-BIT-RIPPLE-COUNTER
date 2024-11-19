# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**

1.Type the program in Quartus software.
2.Compile and run the program.
3.Generate the RTL schematic and save the logic diagram.
4.Create nodes for inputs and outputs to generate the timing diagram.
5.For different input combinations generate the timing diagram.

**PROGRAM**

/* Program for 4 Bit Ripple Counter and verify its truth table in quartus using Verilog programming.

 Developed by:Durga V
 RegisterNumber:212223230052
*/
```
module EX12 (
    output reg [3:0] q,
    input clk, reset
);
    wire t0, t1, t2, t3;
    T_FF tff0(t0, clk, reset);
    T_FF tff1(t1, t0, reset);
    T_FF tff2(t2, t1, reset);
    T_FF tff3(t3, t2, reset);

    always @(posedge clk or posedge reset) begin
        if (reset) begin
            q <= 4'b0000;
        end else begin
            q <= {t3, t2, t1, t0};
        end
    end
endmodule

module D_FF(
    output reg q,
    input d, clk, reset
);
    always @(posedge clk or posedge reset) begin
        if (reset) begin
            q <= 1'b0;
        end else begin
            q <= d;
        end
    end
endmodule

module T_FF(
    output q,
    input clk, reset
);
    wire d;
    D_FF dff0(q, d, clk, reset);
    not n1(d, q); // not is Verilog-provided primitive.
endmodule
```
**RTL LOGIC FOR 4 Bit Ripple Counter**
![image](https://github.com/user-attachments/assets/d486f1ae-b5c0-40a0-b632-434784c8b3ed)

**TIMING DIGRAMS FOR 4 Bit Ripple Counter**
![image](https://github.com/user-attachments/assets/170d9766-dc73-4d04-b3d2-cba53732cd2c)

**RESULTS**
The 4-bit ripple counter implemented in Verilog has been successfully completed. Its functionality has been validated through simulation and comparison with the expected values from the functional tables
