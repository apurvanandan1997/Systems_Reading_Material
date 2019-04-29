`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    20:26:18 05/01/2018 
// Design Name: 
// Module Name:    mem 
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
`include "memop_defs.v"

module mem(clk, state, address, op, store_value, load_value
    );

   	input clk;
	input [2:0] state;
	input [7:0] address;
	input [1:0] op;
	input [7:0] store_value;
	
	output [7:0] load_value;
	
	reg [7:0] load_value;
	
	reg [7:0] data_mem [0:2];
	
	initial begin
	   	data_mem[0] = 8'b11101100;
		data_mem[1] = 8'b00001010;
		data_mem[2] = 8'b00000010;
	end
	
	always @ (posedge clk) begin
	   	if (state == `STATE_MEM) begin
		   	if (op == `MEM_READ) begin
			   	load_value <= data_mem[address];
			end
			else if (op == `MEM_WRITE) begin
			   	data_mem[address] <= store_value;
			end
		end
	end

endmodule
