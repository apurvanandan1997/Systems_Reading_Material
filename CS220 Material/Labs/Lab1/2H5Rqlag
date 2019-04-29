// Verilog test fixture created from schematic D:\CS220Labs\Lab1_2\full_adder_schematic\full_adder_sch.sch - Sat Jan 13 23:52:54 2018
// Created by Mainak Chaudhuri

`timescale 1ns / 1ps

module full_adder_sch_full_adder_sch_sch_tb();

// Inputs
   reg a;
   reg b;
   reg cin;

// Output
   wire sum;
   wire cout;

// Bidirs

// Instantiate the UUT
   full_adder_sch UUT (
		.sum(sum), 
		.a(a), 
		.b(b), 
		.cin(cin), 
		.cout(cout)
   );
// Initialize Inputs
   always @(sum or cout) begin
      $display("time=%d: %b + %b + %b = %b, cout = %b\n", $time, a, b, cin, sum, cout);   
   end

initial begin
   a = 0; b = 0; cin = 0;
   #5
   a = 0; b = 1; cin = 0;
   #5
   a = 1; b = 0; cin = 1;
   #5
   a = 1; b = 1; cin = 1;
   #5
   $finish;
end

endmodule
