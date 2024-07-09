// CODE AND TESTBENCH FOR FINITE STATE MACHINE //

module fsm (
input wire clk,
input wire reset,
output reg [1:0] state
);
// State encoding
parameter A = 2'b00, B = 2'b01, C = 2'b10;
// State register
reg [1:0] next_state;
always @(posedge clk or posedge reset) begin
if (reset)
state <= A;
else
state <= next_state;
end
always @(*) begin
case (state)
A: next_state = B;
B: next_state = C;
C: next_state = A;
default: next_state = A;
endcase
end
endmodule


/////////////  TESTBENCH  ////////////////


module fsm_tb;
// Inputs
reg clk;
reg reset;
// Outputs
wire [1:0] state;
// Instantiate the FSM
fsm uut (
.clk(clk),
.reset(reset),
.state(state)
);
// Clock generation
initial begin
clk = 0;
forever #5 clk = ~clk;
end
// Test sequence
initial begin
// Initialize reset
reset = 1;
#10 reset = 0;
// Check transitions
#20;
if (state != 2'b01) $display("Test Failed at time %t: expected 
state 01, got %b", $time, state);
#20;
if (state != 2'b10) $display("Test Failed at time %t: expected 
state 10, got %b", $time, state);
#20;
if (state != 2'b00) $display("Test Failed at time %t: expected 
state 00, got %b", $time, state);
$display("All tests passed");
$stop;
end
endmodule
