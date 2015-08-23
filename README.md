# mul_16_to_1

module mux16(input[3:0]  select, input[15:0] d, output reg q );
always @( select or d )
begin
   case( select )
       0 : q = d[0];
       1 : q = d[1];
       2 : q = d[2];
       3 : q = d[3];
       4 : q = d[4];
       5 : q = d[5];
       6 : q = d[6];
       7 : q = d[7];
       8 : q = d[8];
       9 : q = d[9];
       10 : q = d[10];
       11 : q = d[11];
       12 : q = d[12];
       13 : q = d[13];
       14 : q = d[14];
       15 : q = d[15];
   endcase
end
endmodule

module stimulus;
reg [15:0]d;
reg [3:0]select;
wire OUTPUT;

mux16 mymux(select, d, OUTPUT);

initial begin
d[0] = 0;
d[1] = 0;
d[2] = 0;
d[3] = 0;
d[4] = 0;
d[5] = 0;
d[6] = 0;
d[7] = 0;
d[8] = 0;
d[9] = 0;
d[10] = 1;
d[11] = 0;
d[12] = 0;
d[13] = 0;
d[14] = 0;
d[15] = 0;

select[0] = 0; select[1] = 1;
select[2] = 0; select[3] = 1; 
#1 $display("S0 = %b, S1 = %b, S2 = %b, S3 = %b, OUTPUT = %b \n",
 select[0], select[1], select[2], select[3], OUTPUT); 

select[0] = 1; select[1] = 0;
select[2] = 1; select[3] = 0;
#1 $display("S0 = %b, S1 = %b, S2 = %b, S3 = %b, OUTPUT = %b \n",
 select[0], select[1], select[2], select[3], OUTPUT); 


end


endmodule
