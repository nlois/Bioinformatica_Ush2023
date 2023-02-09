# Introduccion al uso de Jupyter Notebooks y R Markdown
En el marco del curso "Introducción al análisis bioinformático de secuencias de RAD-seq". Realizado en Ushuaia, Argentina durante febrero 2023.

### Autores
**Santiago Ceballos **(CADIC-CONICET, UNTdF), **Ulises Balza** (CADIC-CONICET) & **Nicolas Lois **(INIBIOMA-CONICET, UBA).

### Introduccion a Jupyter Notebooks y R Markdown
Esta clase es parte del curso "Introducción al análisis bioinformático de secuencias de RAD-seq". Su objetivo es acercar a lxs estudiantes al logging  de sus proyectos bioinformaticos a traves del uso de una aplicación web que ayuda a combinar código, texto explicativo y recursos multimedia en un solo documento. Los Jupyter Notebooks presentan una interfaz visual y fácilmente comprensible y trabajar con grandes bases de datos (locales o libres en la web) de manera transparente y replicable.
unix

#### Replicabilidad
1. Es honesto
2. Es práctico (revisión en un paper)
3. Es útil (copiar lo que hicieron otros y no perder el tiempo)
4. Es lo que hacemos siempre! La semana pasada usaron un protocolo para armar sus bibliotecas de fragmentos, no podemos hacer eso sin hacer un protocolo para analizar los datos, es un riesgo que no estamos dispuestos a aceptar.

Estuvieron trabajando en la terminal, lo cual es un buen ejercicio, pero ahora les vamos a proponer dejar un registro ordenado de todo lo que hicieron. La propuesta es analoga a lo que muchos de ustedes ya conocen: trabajan en R Studio en lugar de trabajar en la consola de R directamente.

#### Actividad
Para este ejercicio vamos a correr un ejemplo distinto con datos reales de un vertebrado. Ahora la complejidad aumenta, tenemos los datos en el cluster de la UNTdF y vamos a accederlos de manera remota desde nuestra computadora a traves de las herramientas de jupyter lab.

Primero vamos a clonar este repositorio en nuestra carpeta en el cluster.

Para eso tienen que seguir los siguientes pasos:
1. conectarse por protocolo ssh:
```console
ssh cursorad2023@170.210.70.37 
```
e ingresan la clave

2. Clonar el repositorio en su carpeta
```console
cd NOMBRE_DE_CARPETA
git clone https://github.com/nlois/Bioinformatica_Ush2023
```

Listo! Fíjense con qué facilidad consiguen este repositorio con los scripts para trabajar y una narrativa que acompania el codigo! 

##### Conectar un Jupyter notebook
Bien, ahora tenemos que conectarnos al cluster a traves del notebook, para eso vamos a tener que activar un environment (una configuracion particular del sistema que tiene instalada todos los elemntos necesarios para poder trabajar en los notebooks). Si se fijan, en este repositorio hay un archivo que se llama cursorad.yml. Este archivo contiene todos los programas y sus versiones y permite instalarlos en cualquier sistema operativo que tenga Anaconda (disponible para Windows, Mac y Linux en LINK)

Volviendo a la conexion con jupyter. En la misma consola en la que estan conectadxs al cluster deben activar el environment (que ya instalamos para ahorrar ese paso porque lleva bastante tiempo y no podrian hacerlo todxs a la vez).

```console
conda activate cursorad
```

Ahora tenemos que configurar el jupyternotebook en el cluster para que corra a traves de un puerto que nosotros podamos acceder. Entonces, en la consola del cluster corran la siguiente línea (acá hay que tener cuidado que cada uno abra su propio puerto, esperen indicacion de los numeros a utilizar en lugar de las XX):

```console
jupyter notebook --no-browser --port=78XX
```

No cierren la consola del cluster, porque se cierra el puerto y tienen que empezar de nuevo!! 

Ahora abran una terminal local y corran el siguiente código (Mac y linux lo corren directo desde una consola nueva sin problemas, en Windows tambien pero consulten si no logran abrir otra consola desde su emulador e.g. PuTTY o Windows PowerShell).

```console
ssh -N -f -L localhost:8001:localhost:78XX cursorad2023@170.210.70.37 
```  

Por ultimo, en un explorador de internet abrir la siguiente dirección: http://localhost:8001/

``console
Les va a solicitar un token. Lo tienen que copiar de la consola del cluster
```


Ahora sí! Exploramos el cluster desde la aplicacion web de jupyter y vamos a abrir el archivo que se llama script_carancho_curso.ipynb. Seguimos las instrucciones del script, las cuales no son más que simplemente los mismos pasos que llevamos adelante durante esta semana en la consola. Así como les chiques del primer curso se llevaron un souvenir (placa de adaptadores) uds se van a llevar el script en formato de narrativa, comentado y reproducible.
