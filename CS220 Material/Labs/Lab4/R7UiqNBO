`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date:    10:33:03 01/30/2018 
// Design Name: 
// Module Name:    lcd_welcome_top 
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
module lcd_welcome_top(
	clk,
	lcd_rs,
	lcd_rw,
	lcd_e,
	lcd4,
	lcd5,
	lcd6,
	lcd7
    );

	input clk;
	output lcd_rs, lcd_rw, lcd_e, lcd4, lcd5, lcd6, lcd7;
	wire lcd_rs, lcd_rw, lcd_e, lcd4, lcd5, lcd6, lcd7;
	
	lcd_welcome LCD ("WELCOME TO CSE  ",
			 "IIT KANPUR      ",
			 clk, lcd_rs, lcd_rw, lcd_e, lcd4, lcd5, lcd6, lcd7);
endmodule
