`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    19:47:27 04/30/2018 
// Design Name: 
// Module Name:    state_control 
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

`define MAX_PC 7

module state_control(clk, program_counter, state
    );

   	input clk;
   	input [2:0] program_counter;
	output [2:0] state;
	
	reg [2:0] state;
	
	initial begin
	   	state = `STATE_IF;
	end
	
	always @ (posedge clk) begin
	   	if ((state == `STATE_WB) && (program_counter < `MAX_PC)) begin
         		state <= `STATE_IF;
		end
		else if (state != `STATE_OUTPUT) begin
		   	state <= state + 1;
		end
	end

endmodule
