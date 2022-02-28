En este tutorial veremos como usar python y pyodide para poder compilar a web assembly que sea compatible con cualquier motor de JavaScript. Un punto a favor es que no tenemos que hacer un build o compilar a mano nosotros, simplemente guardamos el código y el navegador se hará cargo.

Para poder usar pyodide es necesario añadir el script de pyodide a nuestro programa html
	<script src="https://pyodide-cdn2.iodide.io/v0.15.0/full/pyodide.js"></script>

Después en necesario iniciar el enviroment  esto puede tardar un poco en realizarse y aquí es el momento donde podemos agregar algún paquete como numpy o pandas que son soportados por pyodide. 
	languagePluginLoader.then(() =>
	
	pyodide.loadPackage(‘numpy’).then(()=>{
	//Para poder correr basta con correr python 
	pyodide.runPython(‘import numpy as np’)
	//tambien se puede imprimir a consola 
	console.log(pyodide.runPython(‘np.ones((3,3))’))

}))

Tambien podemos ingresar una variable  o el valor de algun componente para poder correr el código de python así que podemos pre escribir nuestro código de python en una variable como en el programa3.html donde solo imprimimos a consola un generador congruencial multiplicativo y un for o incluso podemos realizar cosas más interesantes como puede ser una pagina web donde tenemos un input del usuario de código de python y podemos ejecutarlo para mostrarle una salida como en ejemplo.html

	//corremos el codigo de python 
            pyodide.runPythonAsync(CodigoDePython)
	//esta es una función de salida de nuestro output
           .then(output => addToOutput(output))
            	            .catch((err) => { addToOutput(err) })

			//o podemos solo imprimir a consola 
.then(output => console.log(output))

Referencias 
https://medium.com/swlh/python-in-web-easy-5f7de3813055
