`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    23:31:27 05/11/2018 
// Design Name: 
// Module Name:    input_interface 
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
module input_interface(clk, rotation_event, sw, output_done, input0, input1, input2, input3, input_ready
    );

   	input clk;
   	input rotation_event;
	input [2:0] sw;
	input output_done;
	
	output [2:0] input0;
	output [2:0] input1;
	output [2:0] input2;
	output [2:0] input3;
	output input_ready;
	
	reg [2:0] input0;
	reg [2:0] input1;
	reg [2:0] input2;
	reg [2:0] input3;
	reg input_ready;
	
	reg [2:0] counter;
	reg prev_rotation_event;
	
	initial begin
	   	counter = 0;
		prev_rotation_event = 1;
		input_ready = 0;
	end
	
	always @ (posedge clk) begin
	   	if (output_done == 1) begin
		   	counter <= 0;
			input_ready <= 0;
		end
		else if ((prev_rotation_event == 0) && (rotation_event == 1)) begin
		   	if (counter == 0) begin
			   	input0 <= sw;
				counter <= counter + 1;
			end
			else if (counter == 1) begin
			   	input1 <= sw;
				counter <= counter + 1;
			end
			else if (counter == 2) begin
			   	input2 <= sw;
				counter <= counter + 1;
			end
			else if (counter == 3) begin
			   	input3 <= sw;
				counter <= counter + 1;
				input_ready <= 1;
			end
		end
		prev_rotation_event <= rotation_event;
	end

endmodule
