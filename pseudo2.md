// Estado inicial
const estadoInicial = {
operacionAnterior: '',
operacionActual: '0',
operacion: null,
hayResultado: false,
};

// Funciones de actualización del estado
const actualizarEstado = (estado, input) => {
switch (input.tipo) {
case 'numero':
return procesarNumero(estado, input.valor);
case 'operacion':
return procesarOperacion(estado, input.valor);
case 'igual':
return procesarIgual(estado);
case 'borrar':
return procesarBorrar(estado);
case 'limpiarTodo':
return estadoInicial;
default:
return estado;
}
};

const procesarNumero = (estado, numero) => {
if (estado.hayResultado) {
return {
operacionAnterior: '',
operacionActual: numero === '.' ? '0.' : numero,
operacion: null,
hayResultado: false,
};
}

const nuevoOperacionActual =
estado.operacionActual === '0' || estado.operacionActual === '-0'
? numero === '.'
? '0.'
: numero
: estado.operacionActual + numero;

return {
...estado,
operacionActual: nuevoOperacionActual,
};
};

const procesarOperacion = (estado, operacion) => {
if (estado.hayResultado) {
return {
...estado,
operacionAnterior: estado.operacionActual,
operacionActual: '0',
operacion,
hayResultado: false,
};
}

return {
...estado,
operacionAnterior: estado.operacionActual,
operacionActual: '0',
operacion,
};
};

const procesarIgual = (estado) => {
const previo = parseFloat(estado.operacionAnterior);
const actual = parseFloat(estado.operacionActual);

if (isNaN(previo) || isNaN(actual) || estado.operacion === null) {
return estado;
}

const resultado = realizarOperacion(previo, actual, estado.operacion);

return {
operacionAnterior: '',
operacionActual: resultado.toString(),
operacion: null,
hayResultado: true,
};
};

const procesarBorrar = (estado) => {
if (estado.operacionActual.length === 1 || estado.hayResultado) {
return {
...estado,
operacionActual: '0',
hayResultado: false,
};
}

const nuevoOperacionActual = estado.operacionActual.slice(0, -1);

return {
...estado,
operacionActual: nuevoOperacionActual,
};
};

const realizarOperacion = (previo, actual, operacion) => {
switch (operacion) {
case '+':
return previo + actual;
case '-':
return previo - actual;
case '_':
return previo _ actual;
case '/':
return previo / actual;
default:
return actual;
}
};

// Ejemplo de uso
let estado = estadoInicial;

// Simulación de entrada de datos
const entradaDeDatos = [
{ tipo: 'numero', valor: '5' },
{ tipo: 'operacion', valor: '+' },
{ tipo: 'numero', valor: '3' },
{ tipo: 'igual' },
{ tipo: 'numero', valor: '2' },
{ tipo: 'borrar' },
{ tipo: 'limpiarTodo' },
];

// Procesamiento de la entrada
entradaDeDatos.forEach((input) => {
estado = actualizarEstado(estado, input);
console.log('Operación:', input.valor);
console.log('Resultado:', estado.operacionActual);
});
