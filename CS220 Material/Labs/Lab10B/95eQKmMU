`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company:
// Engineer: 
// 
// Create Date:    18:36:24 05/01/2018 
// Design Name: 
// Module Name:    fetch 
// Project Name: 
// Target Devices: 
// Tool versions: 
// Description: 
//
// Dependencies: 
//
// Revision: 
// Revision 0.01 - File Created
// Additional Comments: Authored by Mainak Chaudhuri
//
//////////////////////////////////////////////////////////////////////////////////
`include "state_defs.v"

module fetch(clk, state, program_counter, instruction
    );

   	input clk;
	input [2:0] state;
	input [7:0] program_counter;
	
	output [31:0] instruction;
	
	reg [31:0] instruction;
	
	reg [31:0] instruction_mem [0:10];
	
	initial begin
		instruction = 0;
		
		instruction_mem[0] = 32'b100011_00000_00001_0000000000000000;
		instruction_mem[1] = 32'b100011_00000_00010_0000000000000001;
		instruction_mem[2] = 32'b100011_00000_00011_0000000000000010;
		instruction_mem[3] = 32'b001001_00000_00100_0000000000000000;
		instruction_mem[4] = 32'b001001_00001_00101_0000000000000000;
		instruction_mem[5] = 32'b000000_00101_00010_00110_00000_101010;
		instruction_mem[6] = 32'b000100_00110_00000_0000000000000101;
		instruction_mem[7] = 32'b000000_00100_00101_00100_00000_100001;
		instruction_mem[8] = 32'b000000_00101_00011_00101_00000_100001;
		instruction_mem[9] = 32'b000000_00101_00010_00110_00000_101010;
		instruction_mem[10] = 32'b000101_00110_00000_1111111111111101;
	end
	
	always @ (posedge clk) begin
	   	if (state == `STATE_IF) begin
		   	instruction <= instruction_mem[program_counter];
		end
	end

endmodule
