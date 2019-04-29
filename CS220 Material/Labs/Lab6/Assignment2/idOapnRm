`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    02:46:23 02/10/2018 
// Design Name: 
// Module Name:    one_bit_add_sub 
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
module one_bit_add_sub(a, b, opcode, cin, sum, cout
    );
	 
	 input a, b, opcode, cin;
	 output sum, cout;
	 wire sum, cout;
	 
	 assign sum = a^b^opcode^cin;
	 assign cout = (a & (b^opcode)) | ((b^opcode) & cin) | (cin & a);

endmodule
