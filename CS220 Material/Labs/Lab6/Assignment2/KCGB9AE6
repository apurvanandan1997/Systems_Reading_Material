`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    02:44:55 02/10/2018 
// Design Name: 
// Module Name:    detect_event 
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
module detect_event(clk, rot_a, rot_b, rotation_event
    );

	input clk, rot_a, rot_b;
	output rotation_event;
	reg rotation_event;
	
	always @ (posedge clk) begin
		if ((rot_a == 1) && (rot_b == 1)) begin
			rotation_event <= 1;
		end
		else if ((rot_a == 0) && (rot_b == 0)) begin
			rotation_event <= 0;
		end
	end

endmodule
