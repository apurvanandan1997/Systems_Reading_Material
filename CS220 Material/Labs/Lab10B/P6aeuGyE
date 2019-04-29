`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company:
// Engineer: 
// 
// Create Date:    19:59:35 05/01/2018 
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

module execute(clk, state, opcode, rsv, rtv, imm, func, program_counter, result, result_valid
    );

   	input clk;
	input [2:0] state;
	input [5:0] opcode;
	input [7:0] rsv;
	input [7:0] rtv;
	input [15:0] imm;
	input [5:0] func;
	
	output [7:0] result;
	output result_valid;
	output [7:0] program_counter;
	
	reg [7:0] result;
	reg result_valid;
	reg [7:0] program_counter;
	
	initial begin
	   	result_valid = 0;
		program_counter = 0;
	end
	
	always @ (posedge clk) begin
	   	if (state == `STATE_EX) begin
		   	if ((opcode == `OP_ADDU) && (func == `FUNC_ADDU)) begin
			   	result <= rsv + rtv;
				result_valid <= 1;
				program_counter <= program_counter + 1;
			end
			else if ((opcode == `OP_SUBU) && (func == `FUNC_SUBU)) begin
			   	result <= rsv - rtv;
				result_valid <= 1;
				program_counter <= program_counter + 1;
			end
			else if ((opcode == `OP_SLT) && (func == `FUNC_SLT)) begin
			   	result <= ($signed(rsv) < $signed(rtv)) ? 8'b00000001 : 8'b00000000;
				result_valid <= 1;
				program_counter <= program_counter + 1;
			end
			else if ((opcode == `OP_ADDIU) || (opcode == `OP_LW)) begin
			   	result <= rsv + imm[7:0];
				result_valid <= 1;
				program_counter <= program_counter + 1;
			end
			else if (opcode == `OP_BEQ) begin
			   	program_counter <= ((rsv == rtv) ? (program_counter + imm[7:0]) : (program_counter + 1));
				result_valid <= 0;
			end
			else if (opcode == `OP_BNE) begin
			   	program_counter <= ((rsv != rtv) ? (program_counter + imm[7:0]) : (program_counter + 1));
				result_valid <= 0;
			end
			else begin
			   	result_valid <= 0;
				program_counter <= program_counter + 1;
			end
		end
	end

endmodule
