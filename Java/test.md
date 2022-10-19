# Java

1) Hibernate es un ORM (mapeo objeto-relacional). Los ORM permiten escribir sentencias como habitualmente se haria en un lenguaje orientado a objetos y el ORM se encarga de traducir dichas sentencias a comandos SQL que las base de datos relacionales comprenden y de esta manera nos permite persistir información sin la necesidad de escribir comandos SQL.

**Decidí hacer el ejercicio con Javascript dado que si bien entendia que me estaba pidiendo el ejercicio mi limitado manejo de la sintaxis de Java hacia complicado la resolución.**

3) 
    ```js
    function quickSort(array) {

        var pivot = array.length - 1;
        var left = [];
        var equals = [];
        var right = [];
        equals.push(array[pivot]);
        for (let i = 0; i < array.length - 1; i++) {
            if (array[i] >= array[pivot]) left.push(array[i]);
            if (array[i] < array[pivot]) {
                if(array[i] !== 0) {
                    left.push(array[i])
                } else {
                    right.push(array[i]);
                }
            }
        }
        if (left.length <= 1 && right.length <= 1) return left.concat(equals).concat(right);
        if (left.length >= 1 && right.length <= 1) return quickSort(left).concat(equals).concat(right);
        if (left.length <= 1 && right.length >= 1) return left.concat(equals).concat(quickSort(right));
        if (left.length > 1 && right.length > 1) return quickSort(left).concat(equals).concat(quickSort(right));
    }

    console.log(quickSort([ 1, 0, 2, 0, 0, 3, 4 ]))
    console.log(quickSort([ 1, 0, -2, 0, 0, 3, 4, 0, 0]))

    /*
    La complejidad del algoritmo quick sort es O(n*logn)
    */
    ```
