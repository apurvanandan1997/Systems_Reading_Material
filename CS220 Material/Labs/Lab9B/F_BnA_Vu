`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    22:13:11 04/30/2018 
// Design Name: 
// Module Name:    execute 
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
`include "func_defs.v"

module execute(clk, state, opcode, rsv, rtv, imm, func, result, instruction_invalid
    );

   	input clk;
	input [2:0] state;
	input [5:0] opcode;
	input [7:0] rsv;
	input [7:0] rtv;
	input [15:0] imm;
	input [5:0] func;
	
	output [7:0] result;
	output instruction_invalid;
	
	reg [7:0] result;
	reg instruction_invalid;
	
	initial begin
	   	instruction_invalid = 1;
	end
	
	always @ (posedge clk) begin
	   	if (state == `STATE_EX) begin
		   	if ((opcode == `OP_ADDU) && (func == `FUNC_ADDU)) begin
			   	result <= rsv + rtv;
				instruction_invalid <= 0;
			end
			else if ((opcode == `OP_SUBU) && (func == `FUNC_SUBU)) begin
			   	result <= rsv - rtv;
				instruction_invalid <= 0;
			end
			else if (opcode == `OP_ADDIU) begin
			   	result <= rsv + imm[7:0];
				instruction_invalid <= 0;
			end
			else begin
			   	instruction_invalid <= 1;
			end
		end
	end

endmodule
