/*module singleportram(clk,din,dout,we,addr);
  input we,clk;
  input [2:0]addr;
  input [7:0]din;
  output reg[7:0]dout;
  reg [7:0]data[0:7];
  
  always@(posedge clk) begin
    if(we)
      data[addr]<=din;
    else
      dout<=data[addr];
  end
endmodule*/

module dualportram(clk,din_a,din_b,dout_a,dout_b,we_a,we_b,addr_a,addr_b);
  input we_a,we_b,clk;
  input [2:0]addr_a,addr_b;
  input [7:0]din_a,din_b;
  output reg[7:0]dout_a,dout_b;
  reg [7:0]data[0:7];
  
  always@(posedge clk) begin
    if(we_a)
      data[addr_a]<=din_a;
    else
      dout_a<=data[addr_a];
  end
  always@(posedge clk) begin
    if(we_b)
      data[addr_b]<=din_b;
    else
      dout_b<=data[addr_b];
  end
endmodule
