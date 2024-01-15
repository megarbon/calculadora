// Declaraciones
var operandoa, operandob, operacion;
var resultado = 0;
var numeroActual = "";

// Funciones Declarativas
const clicEnNumero = numero => numeroActual += numero;
const realizarOperacion = op => (operandoa = parseFloat(numeroActual), operacion = op, numeroActual = "");
const resolver = () => (operandob = parseFloat(numeroActual), resultado = realizarOperacion(`${operandoa} ${operacion} ${operandob}`), numeroActual = resultado.toString());
const limpiar = () => numeroActual = "";
const resetear = () => (limpiar(), operandoa = operandob = resultado = 0, operacion = "");

// Ejemplo de uso
clicEnNumero("1");
clicEnNumero("2");
realizarOperacion("+");
clicEnNumero("3");
resolver();
// Resultado: 15
