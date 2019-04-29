`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    00:28:04 02/10/2018 
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
module detect_event(clk, rot_a, rot_b, rotation_event, rotation_direction
    );

	input clk, rot_a, rot_b;
	output rotation_event, rotation_direction;
	reg rotation_event, rotation_direction;
	
	always @ (posedge clk) begin
		if ((rot_a == 1) && (rot_b == 1)) begin
			rotation_event <= 1;
		end
		else if ((rot_a == 0) && (rot_b == 0)) begin
			rotation_event <= 0;
		end
		else if ((rot_a == 0) && (rot_b == 1)) begin
			rotation_direction <= 1;
		end
		else begin
			rotation_direction <= 0;
		end
	end

endmodule
