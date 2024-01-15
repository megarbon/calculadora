// Declaramos variables
var operandoa, operandob, operacion;
var resultado = obtenerElemento("resultado");
var reset = obtenerElemento("reset");

// Función para obtener elemento por ID
function obtenerElemento(id) {
return document.getElementById(id);
}

// Función para manejar clic en los números
function clicEnNumero(numero) {
resultado.textContent += numero;
}

// Función para realizar operaciones
function realizarOperacion(op) {
operandoa = resultado.textContent;
operacion = op;
limpiar();
}

// Función para limpiar el resultado
function limpiar() {
resultado.textContent = "";
}

// Función para resetear variables
function resetear() {
limpiar();
operandoa = 0;
operandob = 0;
operacion = "";
}

// Función para resolver la operación
function resolver() {
operandob = resultado.textContent;
resultado.textContent = eval(operandoa + operacion + operandob);
resetear();
}

// Eventos de clic
for (let i = 0; i <= 9; i++) {
obtenerElemento(i.toString()).onclick = function () {
clicEnNumero(i);
};
}

reset.onclick = resetear;
suma.onclick = function () { realizarOperacion("+"); };
resta.onclick = function () { realizarOperacion("-"); };
multiplicacion.onclick = function () { realizarOperacion("\*"); };
division.onclick = function () { realizarOperacion("/"); };
igual.onclick = resolver;
