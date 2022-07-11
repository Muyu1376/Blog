---
title: someideas
tags: 网站
abbrlink: 4f24eca6
date: 2022-07-11 14:12:04
categories: Verilog
---
@[TOC](目录)

# Verilog学习笔记1，记录要点

## assign和always语句的区别

assign语句是连续赋值语句
always语句是条件赋值语句，也叫敏感赋值语句

assign语句需要使用的是wire型变量
always语句使用reg型变量

assign综合的一定是组合逻辑电路
always综合的不一定是时序逻辑电路

```Verilog
always@(*)begin

end
 //*表示always块中所有输入变量发生变化时，执行always中的语句
```

## case语句

用法与c语言类似
~~~Verilog
`timescale 1ns/1ns
module mux4_1(
input [1:0]d1,d2,d3,d0,
input [1:0]sel,
output[1:0]mux_out
);
//四选一多路选择器
//*************code***********//
    reg [1:0] temp;   
    always@(*)begin
    case(sel)
        2'b00:temp=d3;
        2'b01:temp=d2;
        2'b10:temp=d1;
        2'b11:temp=d0;
        default:temp=d0;
    endcase
    end        
assign mux_out=temp;
//*************code***********//
endmodule
~~~

## ？：三目运算符

~~~verilog
assign a=b?c:d;
//等价于如果b为真，将c赋值给a，否则将d赋值给a
//等价于if else语句，但是if else只能在always块中使用
//三目运算符可以在assign中使用，不需要单独声明寄存器变量
~~~
