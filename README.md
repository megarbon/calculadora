# calculadora
Una calculadora sencilla usando html, css y js

 Si quieres probarla solamente tienes que hacer clic en el enlace de abajo:
 [Link Preview](https://rawcdn.githack.com/megarbon/calculadora/9d9f3a3f4da3de227f7f4a269ec049cd46ddfc56/index.html)
     

El diseño es muy simple, utilizo grid para poder colocar los elementos a mi gusto.

La logica de la calculadora se hace en la funcion compute con un switch. Tiene un sistemas de detección de errores del usuario como introducir varios operadores seguidos, mas de un "." consecutivo o calcular una operacion sin haber establecido los digitos de previo y actual. Estos errores no podrán darse ejemplo:

    chooseOperation(operation) {
      if (this.currentOperand === '') return //en este punto se evita que puedas darle a igual sin haber un operador.
      if (this.previousOperand !== '') {
        this.compute()
     .
     .
     .

