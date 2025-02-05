## VHDL CODE FOR DIGITAL FILTER


// Code your design here
module fir_filter (
    input clk,
    input reset,
    input [7:0] x,    // 8-bit input signal
    output reg [15:0] y  // 16-bit output signal
);

    // Coefficients for the FIR filter (3-tap filter)
    reg [7:0] h [0:2];  // Array to hold coefficients
    reg [7:0] x_reg [0:2];  // Array to hold previous inputs

    // Initialize coefficients
    initial begin
        h[0] = 8'b00000001;  // h[0] = 1
        h[1] = 8'b00000010;  // h[1] = 2
        h[2] = 8'b00000001;  // h[2] = 1
    end

    always @(posedge clk or posedge reset) begin
        if (reset) begin
            // Reset outputs and registers
            y <= 16'b0;
            x_reg[0] <= 8'b0;
            x_reg[1] <= 8'b0;
            x_reg[2] <= 8'b0;
        end else begin
            // Shift input samples
            x_reg[0] <= x;
            x_reg[1] <= x_reg[0];
            x_reg[2] <= x_reg[1];

            // FIR filter computation: y[n] = h[0] * x[n] + h[1] * x[n-1] + h[2] * x[n-2]
            y <= h[0] * x_reg[0] + h[1] * x_reg[1] + h[2] * x_reg[2];
        end
    end

endmodule


### TEST BENCH

// Code your testbench here
// or browse Examples
module tb_fir_filter();

    // Declare signals for the testbench
    reg clk;
    reg reset;
    reg [7:0] x;    // 8-bit input signal
    wire [15:0] y;   // 16-bit output signal

    // Instantiate the FIR filter
    fir_filter uut (
        .clk(clk),
        .reset(reset),
        .x(x),
        .y(y)
    );

    // Clock generation
    always begin
        #5 clk = ~clk;  // Toggle clock every 5 time units (10 time units period)
    end

    // Stimulus process
    initial begin
        // Initialize signals
        clk = 0;
        reset = 0;
        x = 8'b0;

        // VCD file generation for waveform
        $dumpfile("dump.vcd");   // Specify the VCD file name
        $dumpvars(0, tb_fir_filter);  // Dump all variables in the testbench

        // Apply reset
        reset = 1;
        #10 reset = 0;

        // Apply input stimulus
        x = 8'b00000001; // x[0] = 1
        #10 x = 8'b00000010; // x[1] = 2
        #10 x = 8'b00000011; // x[2] = 3
        #10 x = 8'b00000001; // x[3] = 1
        #10 x = 8'b00000100; // x[4] = 4
        #10 x = 8'b00000101; // x[5] = 5
        #10 x = 8'b00000010; // x[6] = 2

        // End simulation
        #50;
        $finish;
    end

    // Monitor output signals
    initial begin
        $monitor("Time = %0t, x = %b, y = %b", $time, x, y);
    end

endmodule
