Clase Calculadora:
Método constructor(elementoTextoOperacionAnterior, elementoTextoOperacionActual):
this.elementoTextoOperacionAnterior = elementoTextoOperacionAnterior
this.elementoTextoOperacionActual = elementoTextoOperacionActual
limpiar()

    Método limpiar():
        this.operacionActual = ''
        this.operacionAnterior = ''
        this.operacion = undefined

    Método borrar():
        this.operacionActual = convertirCadenaANumero(this.operacionActual.toString().slice(0, -1))

    Método agregarNumero(numero):
        Si (numero es '.' y this.operacionActual incluye '.') entonces retornar
        this.operacionActual = convertirCadenaANumero(this.operacionActual.toString() + numero.toString())

    Método elegirOperacion(operacion):
        Si (this.operacionActual === '') entonces retornar
        Si (this.operacionAnterior !== '') entonces
            realizarOperacion()
        Fin Si
        this.operacion = operacion
        this.operacionAnterior = this.operacionActual
        this.operacionActual = ''

    Método realizarOperacion():
        Declarar resultado
        Declarar previo = convertirCadenaANumero(this.operacionAnterior)
        Declarar actual = convertirCadenaANumero(this.operacionActual)
        Si (isNaN(previo) || isNaN(actual)) entonces retornar
        Switch (this.operacion):
            Caso '+':
                resultado = previo + actual
                Romper
            Caso '-':
                resultado = previo - actual
                Romper
            Caso '*':
                resultado = previo * actual
                Romper
            Caso '÷':
                resultado = previo / actual
                Romper
            Por defecto:
                Retornar
        Fin Switch
        this.operacionActual = resultado
        this.operacion = undefined
        this.operacionAnterior = ''

    Método obtenerNumeroFormateado(numero):
        Declarar cadenaNumero = numero.toString()
        Declarar digitosEnteros = convertirCadenaANumero(cadenaNumero.split('.')[0])
        Declarar digitosDecimales = cadenaNumero.split('.')[1]
        Declarar visualizacionEntera
        Si (isNaN(digitosEnteros)) entonces
            visualizacionEntera = ''
        Sino:
            visualizacionEntera = digitosEnteros.toLocaleString('es', { maximumFractionDigits: 0 })
        Fin Si
        Si (digitosDecimales no es nulo) entonces
            Retornar `${visualizacionEntera}.${digitosDecimales}`
        Sino:
            Retornar visualizacionEntera

    Método actualizarVisualizacion():
        this.elementoTextoOperacionActual.innerText =
            obtenerNumeroFormateado(this.operacionActual)
        Si (this.operacion no es nulo) entonces
            this.elementoTextoOperacionAnterior.innerText =
                `${obtenerNumeroFormateado(this.operacionAnterior)} ${this.operacion}`
        Sino:
            this.elementoTextoOperacionAnterior.innerText = ''

Definir botonesNumeros como document.querySelectorAll('[data-numero]')
Definir botonesOperacion como document.querySelectorAll('[data-operacion]')
Definir botonIgual como document.querySelector('[data-igual]')
Definir botonBorrar como document.querySelector('[data-borrar]')
Definir botonLimpiarTodo como document.querySelector('[data-limpiar-todo]')
Definir elementoTextoOperacionAnterior como document.querySelector('[data-operacion-anterior]')
Definir elementoTextoOperacionActual como document.querySelector('[data-operacion-actual]')

Definir calculadora como nueva Calculadora(elementoTextoOperacionAnterior, elementoTextoOperacionActual)

Para cada botón en botonesNumeros:
botón.addEventListener('click', () => {
calculadora.agregarNumero(botón.innerText)
calculadora.actualizarVisualizacion()
})

Para cada botón en botonesOperacion:
botón.addEventListener('click', () => {
calculadora.elegirOperacion(botón.innerText)
calculadora.actualizarVisualizacion()
})

botonIgual.addEventListener('click', botón => {
calculadora.realizarOperacion()
calculadora.actualizarVisualizacion()
})

botonLimpiarTodo.addEventListener('click', botón => {
calculadora.limpiar()
calculadora.actualizarVisualizacion()
})

botonBorrar.addEventListener('click', botón => {
calculadora.borrar()
calculadora.actualizarVisualizacion()
})
