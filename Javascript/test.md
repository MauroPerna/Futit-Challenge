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

# React

1) Las props de los componentes de react son:
	+ Parametros que se le pasan al componente.
	+ Las props afectan el resultado del renderizado del componente y son utilizados para, a través de un componente padre, pasarle información al componente hijo.

2) Los componentes son funciones o clases que retornan un elemento (JSX). Esta funcion o clase permite definir estados del componente a la par de agregar funcionalidades. 

3) Componente de clase, componente de funcion, componente padre, componente hijo. 

4) El estado de un componente es todo aquello que afecta al renderizado del mismo y que es administrado dentro del componente. Podria pensarse en el estado asi como en las props que son pasadas como parametro pero en el caso del estado este se define y se controla dentro del componente. 

5) El ciclo de vida de react se podria dividir en 3 fases: Montaje del componente, actulizaciones del mismo y desmontaje. En cada etapa tenemos (en los componentes de clase)funciones que nos permiten manejar este ciclo de vida:
	+ Montaje => cuando el componente se monta por primera vez tenemos una funcion que se ejecuta luego de este primer montaje que es componentDidMount()
	+ Actualización => cada vez que algo provoca el re-renderizado de un componente (actualización) tenemos una funcion que nos permite realizar ciertas acciones que es componentDidUpdate().
	+ Desmontaje => Se ejecuta cuando el compoente se desmonta y nos permite realizar ciertas acciones como por ejemplo si teniamos un event listener darlo de baja para que no continue atento a un nuevo evento dado que esto no va a ocurrir ya que el componente no existe más. Este metodo es componentWillUnmount().

    Por otro lado en los componente de funcion tenemos un hook que agrupa todos estos comportamiento y es useEffect()
    ```js
        useEffect(()=> {
            /*
            todo lo que ejecutemos aqui equivaldria a un componentDidMount()
            */
            
            return () => { todo lo que se ejecute aqui equivaldria a un componentWillUnmount()};
        },[si pasamos dependencias equivaldria a un componentDidUpdate()])
    ``` 

6) Para setear un estado dentro de un componente depende si es un componente de clase o funcion. Si es un componente de clase debemos setear el contructor y dentro utilizar this.state:

    ```js
	class MyComponent extends React.Component {
  		constructor(props) {
    			super(props);
    			this.state = {};
  		}
		/*
		Resto del componente
		*/
	}
    ```
	
   En un componente de funcion por otro lado tenemos el hook useState que nos devuelve 2 elementos una variable que representa el estado mismo y
   una funcion para manipular el estado:

    ```js
	const [value, setValue] = useState();
    ```

7)  this.state.value = "my value"
 
8) Cuando cambia el estado de un componente se provoca un re-renderizado del mismo.

9) Suponiendo que por props me pasen un array de objetos del estilo: : { firstname: "demo", lastname: "demo", dni: 1234 } un componente se veria de la siguiente forma.

    ```js
	import react from 'react'
	
	export default function MyComponent(array) {
	
		return(
			<>
			  <ul>
			    {
				array.map(e=> {
					<li>
					    <div>
						<p>{e.firstname}</p>
						<p>{e.lastname}</p>
						<p>{e.dni}</p>
					     </div>
					</li>
				})
			    }
			  </ul>
			</>
		)
	
	}
    ```

10)
    ```js
	import react from 'react'
	
	export default function MyOtherComponent(data) {
	
		return(
			<h1>{data}</h1>
		)
	
	}
    ```

11) import name from 'name';

12) import MiComponente from './MyComponent.js';

13) 
    El error es que falta el return:
	```js 
    return(
        <h1>
            Hello World
        </h1>
    )
    ```

14) El componente es un contador que cada vez que se le da click al boton suma 1 a una variable estado que se llama property.

15) El this.setState(property: 'Propiedad') no puede ir dentro del render().

16) Una llamada a una REST api puede hacerse ya sea utilizando fetch que viene con el lenguaje o instalando una libreria como axios para hacer peticiones HTTP.

17) useEffect es un hook que me permite controlar el ciclo de vida de un componente de funcion.
	```js
    useEffect(()=> {
		/*
		todo lo que pongamos aqui se ejecuta una vez montado el componente
		*/
		
		return () => { se ejecuta una vez desmonatado el componente};
	},[lo que pongamos aqui sera una dependencia que en caso de cambiar provocara un re-renderizado])
    ``` 

18) 
    ```js
	import { useState } from "react";	

	export default function useCustomHook(increment) {
  		const [count, setCount] = useState(0);

  		return {
		   value: count,
		   add: () => setCount(prevCount => prevCount + increment)
		};
	}
    ```


