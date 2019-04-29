`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    02:48:03 02/10/2018 
// Design Name: 
// Module Name:    drive_worm 
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
`define EAST 2'b00
`define WEST 2'b01
`define NORTH 2'b10
`define SOUTH 2'b11

module drive_worm(clk, rotation_event, Y, xc, yc
    );

	input clk, rotation_event;
	input [3:0] Y;
	
	output [3:0] xc;
	output [3:0] yc;
	reg [3:0] xc = 0;
	reg [3:0] yc = 0;
	
	reg [4:0] A;
	reg [4:0] B;
	wire [4:0] C;
	reg opcode;
	reg prev_rotation_event = 1;
	reg [1:0] direction;
	reg count=0;
	
	wire carry[4:0];
	
	always @ (posedge clk) begin
		if (count == 1) begin
			if (direction == `EAST) begin
				if (C[4] == 1) begin
					xc <= 4'b1111;
				end
				else begin
					xc <= C[3:0];
				end
			end
			else if (direction == `WEST) begin
				if (C[4] == 1) begin
					xc <= 4'b0000;
				end
				else begin
					xc <= C[3:0];
				end
			end
			else if (direction == `NORTH) begin
				if (C[4] == 1) begin
					yc <= 4'b1111;
				end
				else begin
					yc <= C[3:0];
				end
			end
			else begin
				if (C[4] == 1) begin
					yc <= 4'b0000;
				end
				else begin
					yc <= C[3:0];
				end
			end
		end
		if ((prev_rotation_event == 0) && (rotation_event == 1)) begin
			B <= {3'b000,Y[1:0]};
			direction <= Y[3:2];
			count <= 0;
			if (Y[3:2] == `EAST) begin
				opcode <= 0;
				A <= xc;
			end
			else if (Y[3:2] == `WEST) begin
				opcode <= 1;
				A <= xc;
			end
			else if (Y[3:2] == `NORTH) begin
				opcode <= 0;
				A <= yc;
			end
			else if (Y[3:2] == `SOUTH) begin
				opcode <= 1;
				A <= yc;
			end
		end
		else begin
			count <= 1;
		end
		prev_rotation_event <= rotation_event;
	end

	one_bit_add_sub ADD0 (A[0], B[0], opcode, opcode, C[0], carry[0]);
	one_bit_add_sub ADD1 (A[1], B[1], opcode, carry[0], C[1], carry[1]);
	one_bit_add_sub ADD2 (A[2], B[2], opcode, carry[1], C[2], carry[2]);
	one_bit_add_sub ADD3 (A[3], B[3], opcode, carry[2], C[3], carry[3]);
	one_bit_add_sub ADD4 (A[4], B[4], opcode, carry[3], C[4], carry[4]);

endmodule
