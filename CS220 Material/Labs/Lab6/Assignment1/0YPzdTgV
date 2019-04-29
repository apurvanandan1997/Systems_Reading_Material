`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer:
// 
// Create Date:    01:16:09 02/10/2018 
// Design Name: 
// Module Name:    drive_add_sub 
// Project Name: 
// Target Devices: 
// Tool versions: 
// Description: 
//
// Dependencies: 
//
// Revision: 
// Revision 0.01 - File Created
// Additional Comments: 
//
//////////////////////////////////////////////////////////////////////////////////
module drive_add_sub(clk, rotation_event, Y, rot_center, sum, overflow
    );
	 
	 input clk, rotation_event, rot_center;
	 input [3:0] Y;
	 
	 output [6:0] sum;
	 output overflow;
	 wire [6:0] sum;
	 wire overflow;
	 
	 reg prev_rotation_event = 1;
	 reg [6:0] A;
	 reg [6:0] B;
	 reg opcode;
	 reg [2:0] input_steps = 0;
	 
	 wire [6:0] carry;
	 
	 always @ (posedge clk) begin
		if ((prev_rotation_event == 0) && (rotation_event == 1)) begin
			if (input_steps == 0) begin
				A[3:0] <= Y;
				input_steps <= 1;
			end
			else if (input_steps == 1) begin
				A[6:4] <= Y[2:0];
				input_steps <= 2;
			end
			else if (input_steps == 2) begin
				B[3:0] <= Y;
				input_steps <= 3;
			end
			else if (input_steps == 3) begin
				B[6:4] <= Y[2:0];
				input_steps <= 4;
			end
			else if (input_steps == 4) begin
				opcode <= Y[0];
				input_steps <= 0;
			end
		end
		if (rot_center == 1) begin
			input_steps <= 0;
		end
		prev_rotation_event <= rotation_event;
	end

	one_bit_add_sub ADD0 (A[0], B[0], opcode, opcode, sum[0], carry[0]);
	one_bit_add_sub ADD1 (A[1], B[1], opcode, carry[0], sum[1], carry[1]);
	one_bit_add_sub ADD2 (A[2], B[2], opcode, carry[1], sum[2], carry[2]);
	one_bit_add_sub ADD3 (A[3], B[3], opcode, carry[2], sum[3], carry[3]);
	one_bit_add_sub ADD4 (A[4], B[4], opcode, carry[3], sum[4], carry[4]);
	one_bit_add_sub ADD5 (A[5], B[5], opcode, carry[4], sum[5], carry[5]);
	one_bit_add_sub ADD6 (A[6], B[6], opcode, carry[5], sum[6], carry[6]);
	
	assign overflow = carry[5]^carry[6];

endmodule
