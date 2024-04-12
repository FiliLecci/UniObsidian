c## Moduli
Esistono due tipi di moduli in verilog:
### Primitive
Sono essenzialmente delle tabelle di verità.
Ogni primitiva può prendere in input un qualsiasi numero di valori ma ne può restituire solamente uno.
### Module
Sono "formule" booleane
___
## Simboli
![![AESO/#^Table4]]
___
## Esempio
```verilog
//half adder che calcola sia il risultato che il carry
module prova;
  reg a;
  reg b;
  wire c, r;
  
  half_adder modulodatestare(r, c, a, b);
  
  initial 
    begin
		for(i=0;i<4;i=i+1)
			begin
				{a,b}=i; //in questo modo il valore di i viene messo in a e b sotto forma di valore binario
			#1	display("%b %b : ris %b, carry %b", a, b, r, c);
			end
	    $finish;
    end
endmodule

//half adder che calcola sia il risultato che il carry

//definizione di un modulo di tipo "module" per calcolare il risultato
module half_adder_ris(output ris, input a, input b);
	assign ris = ((~a)&&b)||(a&&(~b));
endmodule

//definizione di un modulo di tipo "primitive" per calcolare il carry
primitive half_adder_carry(output carry, input a, input b);
	table
		0 0 : 0;
		0 1 : 0;
		1 0 : 0;
		1 1 : 1;
	endtable
endprimitive

//definizione modulo che usa quelli precedenti per calcolare sia risultato che carry
module half_adder(output ris, output carry, input a, input b);
	half_adder_ris module1(ris, a, b);
	half_adder_carry module2(carry, a, b);
endmodule
```