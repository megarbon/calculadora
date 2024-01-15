Proceso calculadora

    Leer operacion
    //aqui se verifica que el usuario ingreso una funcion valida//
    si operacion>0 y operacion<5 Entonces
    	Escribir "ingrese el primer numero"
    	Leer numero1
    	Escribir "Ingrese el segundo numero"
    	Leer numero2
    	Si operacion=1 Entonces
    		Escribir "el resultado de la suma es"
    		resultado=numero1+numero2
    	Fin Si
    	Si operacion=2 Entonces
    		Escribir "el resultado de la resta es"
    		resultado=numero1-numero2
    	FinSi
    	Si operacion=3 Entonces
    		Escribir "el resulado de la multiplicacion"
    		resultado=numero1*numero2
    	FinSi
    	Si operacion=4 Entonces
    		Escribir "el resultado de la division es"
    		resultado=numero1/numero2
    	FinSi
    	Escribir resultado
    Sino
    	Escribir "esa no es una operacion valida"
    FinSi

FinProceso
