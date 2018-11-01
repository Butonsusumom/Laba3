# Задание 26
![Image alt](https://github.com/Butonsusumom/Laba3/blob/master/screen.PNG)

> Delphi

```dpr
Program LR3;
uses
  SysUtils;
function Power(x:Real;y:Integer):Real;//rising a number to a positive integer power
   var i:Integer;
       s:Real;
    begin
      s:=1;
       for i:=1 to y do
        s:=s*x;
      Power:=s;
    end;
{$APPTYPE CONSOLE}
var x,h,f1,chisl,f2,slt,slp,esp :real;
      i,k,N,final :integer;
BEGIN
 writeln('------------------------------------------------------------------------');
 writeln('|       |        |     e=10^-2     |     e=10^-3     |     e=10^-4     |');
 writeln('|   x   |  f1(x) |------------------------------------------------------');
 writeln('|       |        |  f2(x) |   N    |  f2(x) |   N    |  f2(x) |   N    |');
 writeln('------------------------------------------------------------------------');
 x:=-0.6;
 h:=0.05;
 final:=20;
  for i:=1 to final do //counting f1 and f2 for all values of x
   begin
    f1:=2*x/3+2*x*x*x/9-x*x*x/3*ln(1-x*x)-2/3*arctan(x);  //counting f1 for certain value of x
    write('|',x:7:2,'|',f1:8:4,'|');
    k:=1;                  // count ererything for first addend
    chisl:=Power(x,2*k+3);
    slt:=chisl/(k*(2*k+3));
    slp:=0;
    f2:=slt;
    N:=1;
    esp:=0.01;


       repeat     //cycle that calculates value f2 for certan value x
         chisl:=chisl*sqr(x);
         k:=k+1;
         slp:=slt;
         slt:=chisl/(k*(2*k+3));

         if Abs(slt-slp)<esp then     //condition for output the value f2 and N for certain accuracy
         begin
           write(f2:8:4,'|',N:8,'|');
           esp:=esp/10;   //change accuracy
         end;
         f2:=slt+f2;
         N:=N+1;

        until esp<0.0001;    //contition under which we finish calculations
    writeln;
    x:=x+h;
    Writeln('|       |        |        |        |        |        |        |        |');
   end;
   writeln('------------------------------------------------------------------------');
   readln;
END.

```

 

