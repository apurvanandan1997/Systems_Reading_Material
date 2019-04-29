`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    20:39:37 05/01/2018 
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
`include "memop_defs.v"

module processor(clk, led
    );

   	input clk;
	
	output [7:0] led;
	
	reg [7:0] led;
	
	wire [7:0] PC;
	wire [2:0] state;
	wire [31:0] instruction;
	wire [5:0] opcode;
	wire [4:0] rs;
	wire [4:0] rt;
	wire [4:0] rd;
	wire [15:0] imm;
	wire [5:0] func;
	wire [7:0] result;
	wire result_valid;
	wire [7:0] rsv;
	wire [7:0] rtv;
	wire [7:0] load_value;
	
	state_control SC(clk, PC, state);
	fetch IF(clk, state, PC, instruction);
	decode ID(clk, state, instruction, opcode, rs, rt, rd, imm, func);
	register_file RF(clk, state, rs, rt, (opcode == `OP_RFORM) ? rd : rt, (opcode == `OP_LW) ? load_value : result, (opcode == `OP_LW) ? 1'b1 : result_valid, rsv, rtv);
	execute EX(clk, state, opcode, rsv, rtv, imm, func, PC, result, result_valid);
	mem DATA_MEMORY(clk, state, result, (opcode == `OP_LW) ? `MEM_READ : `MEM_IDLE, rtv, load_value);
	
	always @ (posedge clk) begin
	   	if (state == `STATE_OUTPUT) begin
		   	led <= rsv;
		end
	end

endmodule
