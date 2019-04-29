`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    00:35:52 02/10/2018 
// Design Name: 
// Module Name:    drive_led 
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
module drive_led(clk, rotation_event, rotation_direction,
                 led0, led1, led2, led3, led4, led5, led6, led7
    );

	input clk, rotation_event, rotation_direction;
	output led0, led1, led2, led3, led4, led5, led6, led7;
	reg led0=1;
	reg led1, led2, led3, led4, led5, led6, led7;
	
	reg prev_rotation_event;
	
	always @ (posedge clk) begin
		if ((prev_rotation_event == 0) && (rotation_event == 1)) begin
			if (rotation_direction == 0) begin
				led0 <= led1;
				led1 <= led2;
				led2 <= led3;
				led3 <= led4;
				led4 <= led5;
				led5 <= led6;
				led6 <= led7;
				led7 <= led0;
			end
			else begin
				led0 <= led7;
				led7 <= led6;
				led6 <= led5;
				led5 <= led4;
				led4 <= led3;
				led3 <= led2;
				led2 <= led1;
				led1 <= led0;
			end
		end
		prev_rotation_event <= rotation_event;
	end

endmodule
