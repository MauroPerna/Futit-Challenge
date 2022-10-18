# Javascript

 1) Alert no imprime por consola, este abre una ventana emergente en el navegador con el resultado de la funcion que se le pasa como parametro. 
   Si por printed se entiende imprimir por consola lo que devuelve en todos los casos es "undefined". Hecha esta salvedad lo que nos arroja el alert es:

	a) 25 porque, 2*2 + 3*3 + 2*2*3 => 4 + 9 + 12 = 25
	b) 81 porque, 4*4 + 5*5 + 2*4*5 => 16 + 25 + 40 = 81
	c) 2 porque, cada vez que se ejecuta la funcion numLlamadas se incrementa en 1 (numLlamadas++) y la misma lo hace 2 veces (casos a) y b))
	d) "undefined" porque, las funciones tienen su propio entorno de ejecucion y al estar definida la variable "cuadradoDeA" dentro de la funcion solo existe 
	   en ella, cuando en el scope global pregunto por la variable la misma no esta definida. 


 2) alert(s2.toLowerCase()) => "hello world!"

 3) Dado:

    ```js
        var mostrar = function(param){
            param();
        }
    ```

    Mostrar por consola: "Openbravo!!!"

    definimos:

    ```js
        function mensaje() {
            console.log("Openbravo!!!")
        }
    ```
    
    Pasamos mensaje como callback a mostrar de la siguiente manera:
    
	mostrar(mensaje) => por consola veremos = Openbravo!!!

 4) 
 
```js
        function isDiagonalMatrix(matrix) {
                for (let i = 0; i < matrix.length; i++) {
                        for (let j = 0; j < matrix.length; j++) {
                            /* 
                                no nos interesa la diagonal principal, dado
                                que sus elementos pueden o no ser 0.
                                Nos interesa que el resto de elementos que
                                no conforman la diagonal sean iguales a 0
                                en esta condicion lo que estamos evaluando es 
                                justamente eso, decimos que siempre que los iteradores
                                sean distintos (en el caso de la diagonal siempre son 
                                iguales la diagonal empieza en 0,0 sigue en 1,1 y termina 
                                en 2,2 para una matriz 3x3). Si esta condicion se cumple,
                                lo que queremos saber es si dicho elemento es distinto de 0
                                en cuyo caso lo fuera seria condicion suficiente para 
                                indicar que dicha matriz no es una matriz diagonal.
                            */

                                if(i !== j && matrix[i][j] !== 0) {
                                        return false;
                                }
                        }
                }

                return true;
        }

        console.log(isDiagonalMatrix([[1, 0, 0], [0, 2, 0], [0, 0, 3]]));
```
