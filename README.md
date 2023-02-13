# Introducción al uso de Jupyter Notebooks y R Markdown
En el marco del curso "Introducción al análisis bioinformático de secuencias de RAD-seq". Realizado en Ushuaia, Argentina durante febrero 2023.

### Autores
**Santiago Ceballos** (CADIC-CONICET, UNTdF), **Ulises Balza** (CADIC-CONICET) & **Nicolas Lois** (INIBIOMA-CONICET, UBA).

### Introduccion a Jupyter Notebooks y R Markdown
Esta clase es parte del curso "Introducción al análisis bioinformático de secuencias de RAD-seq". Su objetivo es acercar a lxs estudiantes al _logging_  de sus proyectos bioinformaticos a traves del uso de una aplicación web que ayuda a combinar código, texto explicativo y recursos multimedia en un solo documento. Los _Jupyter Notebooks_ presentan una interfaz visual fácilmente comprensible y trabajar con grandes bases de datos (locales o libres en la web) de manera transparente y replicable.

#### Replicabilidad
1. Es honesto (permite mostrar el proceso desde los datos crudos hasta el plot final)
2. Es práctico (e.g. volver a realizar todos los análisis con modificaciones solicitadas en la revisión en un artículo)
3. Es útil (utilizar recursos en repositorios con muchas herramientas comentadas que permiten ahorrar mucho tiempo)
4. En el fondo, es lo que hacemos siempre! La semana pasada lxs estudiantes del primer curso usaron un protocolo para armar sus bibliotecas de fragmentos generados por la técnica RAD, no podemos completar el proceso sin hacer un protocolo prolijo y replicable para analizar los datos, es un riesgo que no deberíamos correr luego de haber puesto tantos recursos en obtener la información.

Hasta ahora estuvieron trabajando en la terminal, lo cual es un buen ejercicio, pero ahora les vamos a proponer dejar un registro ordenado de todo lo que hicieron. La propuesta es análoga a lo que muchos de ustedes ya conocen: trabajar en R Studio en lugar de trabajar en la consola de R directamente.

------------------------------------------------

#### Actividad
Para este ejercicio vamos a correr un ejemplo distinto. Pero ahora la complejidad aumenta, porque vamos a a acceder a los datos de manera remota desde nuestra computadora a traves de las herramientas de jupyter lab. Los primeros pasos son un poco engorrosos pero el resultado final (creemos) vale la pena. Ya nos dirán.

Primero vamos a copiar los archivos necesarios para trabajar y clonar este repositorio en nuestra carpeta en el cluster.

1. Para eso tienen que primero conectarse como hicieron esta semana por protocolo ssh:
```console
ssh cursorad2023@170.210.70.37 
```
e ingresan la clave

2. Clonar el repositorio en su carpeta
```console
cd SU_NOMBRE
```
```console
git clone https://github.com/nlois/Bioinformatica_Ush2023
```

3. Copiar la carpeta carancho_estudiantes 

```console
cp -r /home/cursorad2023/carancho_estudiantes/ /home/cursorad2023/alumnos/SU_NOMBRE/Bioinformatica_Ush2023
```
el _flag_ ```-r``` permite copiar carpetas completas.

Listo! Fíjense con qué facilidad consiguen este repositorio con los scripts para trabajar y una narrativa que acompaña el codigo! 

##### Conectar un Jupyter notebook
Bien, ahora tenemos que conectarnos al cluster a traves del notebook, para eso vamos a tener que activar un environment (una configuracion particular del sistema que tiene instalada todos los elementos necesarios para poder trabajar en los notebooks). Si se fijan, en este repositorio hay un archivo que se llama cursorad.yml. Este archivo contiene todos los programas y sus versiones y permite instalarlos en cualquier sistema operativo que tenga Anaconda (disponible para Windows, Mac y Linux en https://www.anaconda.com/)

Volviendo a la conexion con jupyter...En la misma consola en la que estan conectadxs al cluster deben **activar** el environment (que ya instalamos para ahorrar ese paso porque lleva bastante tiempo y no podrían hacerlo todxs a la vez).

```console
conda activate cursorad
```

Ahora tenemos que configurar el _jupyternotebook_ en el cluster para que corra a través de un puerto que sea accesible desde nuestra computadora. Entonces, en la consola del cluster corran la siguiente línea (acá hay que tener cuidado que cada unx abra su propio puerto, esperen indicaciones de los números a utilizar en lugar de las XX):

```console
jupyter notebook --no-browser --port=78XX
```

No cierren la consola del cluster, porque se cierra el puerto y tienen que empezar de nuevo!! 

Ahora abran una terminal local y corran el siguiente código (Mac y linux lo corren directo desde una consola nueva sin problemas, en Windows les conviene abrir un Windows PowerShell).

```console
ssh -N -f -L localhost:8001:localhost:78XX cursorad2023@170.210.70.37 
```  

Por ultimo, en un explorador de internet abrir la siguiente dirección: http://localhost:8001/. Les va a solicitar un token. Lo tienen que copiar de la consola (que dejaron antes abierta) del cluster.

Ahora sí! Exploramos el cluster desde la aplicacion web de jupyter y vamos a abrir el archivo que se llama ```script_carancho_curso.ipynb```. Seguimos las instrucciones del script, las cuales no son más que simplemente los pasos que llevamos adelante durante esta semana en la consola. Así como les chiques del primer curso se llevaron un souvenir (placa de adaptadores), ustedes se van a llevar el script en formato de narrativa, comentado y reproducible.
