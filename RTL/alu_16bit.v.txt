// =============================================================================
// Module : alu_16bit
// Description : 16-bit ALU supporting 8 operations
//   000 - ADD   : Y = A + B
//   001 - SUB   : Y = A - B
//   010 - AND   : Y = A & B
//   011 - OR    : Y = A | B
//   100 - XOR   : Y = A ^ B
//   101 - NOT   : Y = ~A
//   110 - SHL   : Y = A << 1
//   111 - SHR   : Y = A >> 1
//
// Flags : zero, carry, overflow, negative
// DFT   : muxed_scan ports (scan_en / scan_in / scan_out)
// =============================================================================
module alu_16bit (
    input  wire        clk,       // Register clock
    input  wire        rst_n,     // Active-low async reset
    // DFT ports
    input  wire        scan_en,
    input  wire        scan_in,
    output wire        scan_out,
    // Operands & control
    input  wire [15:0] A,
    input  wire [15:0] B,
    input  wire [ 2:0] op,
    input  wire        en,        // Enable: latch result on rising edge
    // Outputs
    output reg  [15:0] Y,         // Result register
    output reg         flag_zero,
    output reg         flag_carry,
    output reg         flag_overflow,
    output reg         flag_neg
);

    // -------------------------------------------------------------------------
    // Combinational ALU core
    // -------------------------------------------------------------------------
    reg  [16:0] result_ext;   // 17-bit to capture carry

    always @(*) begin
        result_ext = 17'd0;
        case (op)
            3'b000: result_ext = {1'b0, A} + {1'b0, B};          // ADD
            3'b001: result_ext = {1'b0, A} - {1'b0, B};          // SUB
            3'b010: result_ext = {1'b0, A  & B};                  // AND
            3'b011: result_ext = {1'b0, A  | B};                  // OR
            3'b100: result_ext = {1'b0, A  ^ B};                  // XOR
            3'b101: result_ext = {1'b0, ~A};                      // NOT
            3'b110: result_ext = {A[15], A[14:0], 1'b0};          // SHL
            3'b111: result_ext = {1'b0,  1'b0, A[15:1]};         // SHR
            default: result_ext = 17'd0;
        endcase
    end

    // Overflow: signed overflow for ADD/SUB only
    wire ov_add = (~A[15] & ~B[15] &  result_ext[15]) |
                  ( A[15] &  B[15] & ~result_ext[15]);
    wire ov_sub = (~A[15] &  B[15] &  result_ext[15]) |
                  ( A[15] & ~B[15] & ~result_ext[15]);

    // -------------------------------------------------------------------------
    // Output register (clocked)
    // -------------------------------------------------------------------------
    always @(posedge clk or negedge rst_n) begin
        if (!rst_n) begin
            Y            <= 16'd0;
            flag_zero    <= 1'b0;
            flag_carry   <= 1'b0;
            flag_overflow<= 1'b0;
            flag_neg     <= 1'b0;
        end else if (en) begin
            Y            <= result_ext[15:0];
            flag_zero    <= (result_ext[15:0] == 16'd0);
            flag_carry   <= result_ext[16];
            flag_neg     <= result_ext[15];
            case (op)
                3'b000:  flag_overflow <= ov_add;
                3'b001:  flag_overflow <= ov_sub;
                default: flag_overflow <= 1'b0;
            endcase
        end
    end

endmodule
