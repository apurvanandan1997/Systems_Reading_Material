`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    22:26:21 04/30/2018 
// Design Name: 
// Module Name:    processor 
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
`include "opcode_defs.v"

module processor(clk, led
    );

   	input clk;
	
	output [7:0] led;
	
	reg [7:0] led;
	
	wire [2:0] PC;
	wire [2:0] state;
	wire [31:0] instruction;
	wire [5:0] opcode;
	wire [4:0] rs;
	wire [4:0] rt;
	wire [4:0] rd;
	wire [15:0] imm;
	wire [5:0] func;
	wire [7:0] result;
	wire instruction_invalid;
	wire [7:0] rsv;
	wire [7:0] rtv;
	
	state_control SC(clk, PC, state);
	fetch IF(clk, state, PC, instruction);
	decode ID(clk, state, instruction, opcode, rs, rt, rd, imm, func);
	register_file RF(clk, state, rs, rt, (opcode == `OP_RFORM) ? rd : rt, result, instruction_invalid, rsv, rtv);
	execute EX(clk, state, opcode, rsv, rtv, imm, func, result, instruction_invalid);
	
	always @ (posedge clk) begin
	   	if (state == `STATE_OUTPUT) begin
		   	led <= rsv;
		end
	end

endmodule
