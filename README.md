# Introducción a Angular y Express
---

Lo primero que hay que entender de ambas tecnologías es que son frameworks, lo que esto significa es que no necesitarás buscar mucho fuera de ellos para realizar cualquier acción ya que es muy probable que lo que quieras hacer esté integrado.

Esto no quiere decir que no puedas añadir librerías externas, por supuesto que puedes, pero si ya existe dentro del ecosistema del framework es mejor utilizar su propia herramienta para que no haya posibilidad de problemas de compatibilidad.

## Diferencia entre frontend y backend
---

Puedes pensar que es algo claro, pero es importante tener clara la diferencia entre lo que es backend y frontend, especialmente si has desarrollado aplicaciones de escritorio, ¿por qué? Bueno, cuando se desarrolla una aplicación de escritorio toda la aplicación se escribe como una sola aplicación, lo que esto significa es que tanto la funcionalidad como la interfaz de usuario se desarrollan juntas y cuando está completa entonces se compila y ya está toda la aplicación.

En el desarrollo web esto es diferente, cuando se desarrolla un sistema con interfaz de usuario y funcionalidad, estos se dividen en dos aplicaciones, una se conoce como backend y la otra como frontend, y se debe de tener bien en claro que son escencialmente dos aplicaciones separadas.

El frontend se encarga única y exclusivamente de la interfaz de usuario, es importante no ponerle mucha carga ya que se ejecuta en el navegador del usuario, por lo que no es óptimo que este ejecute toda la funcionalidad de la aplicación.

Por otro lado el backend se encarga de la funcionalidad de la aplicación, este no tiene la limitación del frontend que se ejecuta en el ordenador del cliente sino que se ejecuta en un servidor ya sea como IAAS (Infrastructure as a Service) o gestionado por un PAAS (Platform as a Service). Esto nos permite exigir un poco más a la aplicación.

## NodeJS
---

La definición que ofrece la pagina oficial es la siguiente:

> *Ideado como un entorno de ejecución de JavaScript orientado a eventos asíncronos, Node.js está diseñado para crear aplicaciones network escalables. Esto contrasta con el modelo de concurrencia más común de hoy en día, en el que se emplean hilos del Sistema Operativo. Las redes basadas en hilos son relativamente ineficientes y muy difíciles de usar.*

Para ponerlo en palabras mas simple, como supongo comprende JavaScript se ejecuta en un navegador, pero en el desarrollo de aplicaciones y cuando ya estas estan compiladas para su uso se ejecuta en el sistema, esto es gracias a NodeJS.

**¿Quiere decir esto que el computador ya tiene NodeJS junto al navegador?**

No, los navegadores contienen compiladores mayormente escritos en lenguajes como `C` o `C++` los cuales se comunican mejor con el ordenador, por ejemplo el compilador que viene junto a Chrome es llamado V8, este mismo compilador es utilizado por NodeJS para permitirnos ejecutar JavaScript en el sistema.

### Instalación

Para instalar NodeJS primero debemos dirijirnos a su sitio oficial [NodeJS](https://nodejs.org/es), en este podemos encontrar 2 opciones la LTS y la Actual, LTS son las siglas de Long-Term Support (apoyo a largo plazo) lo que hace referencia garantizar la solucion de bugs durante los proximos 30 meses.

Luego de descargar el archivo lo ejecutamos e installamos siguiendo los pasos y asegurandonos de al final marcar la opcion de instalar todas las dependencias necesarias.

Esto puede llegar a tardar un momento dependiendo de la capacidad de conexión que tengan disponible.

Para comprobar de que se ha instalado correctamente podemos ejecutar el siguiente comando en el terminal o cmd: `node --version` este imprimira en el termminal la versión de **node** que esta instalada.

Junto a node tambien se instala **npm** cuyas siglas dicen Node Package Manager o manejador de paquetes de node, este se utiliza para instalar librerias y frameworks en la aplicacion o el sistema, para provar que esta instalado se puede ejecutar el comando `npm --version` este imprimira en el termminal la versión de **npm** que esta instalada.

## TypeScript
---

Como saben **JavaScript** no es un lenguaje con tipado como lo son **C++**, **C#** o **Java**, esto es muy propenso a generar errores y realentizar el desarrollo de aplicaciones, por esta razón se creo **TypeScript**, el cual es en palabras simples **JavaScript** pero con sintaxy para tipos.

> *TypeScript es un lenguaje de programación fuertemente tipado que se basa en JavaScript, proporcionándole mejores herramientas a cualquier escala.*

Este no es obligatorio para el uso de **Express** con **NodeJS** pero es altamente recomendado el utlizarlo. Por el contrario **Angular** requiere el uso de **TypeScript** por lo que no se puede evitar el utilizarlo.

## Express
---

> **Express** es un framework de aplicaciones web **Node.js** mínimo y flexible que proporciona un sólido conjunto de funciones para aplicaciones web y móviles.
> *Tambien notar que otros frameworks muy famosos como **NestJS** estan basados en **Express**.*

### Como instalarlo

Para esto primero tenemos que configurar un entorno de **Node.js** para hacer esto sigamos estos pasos:
 - Crear una carpeta para este en este caso se llamara **backend** ya que su objetivo es ser una aplicación backend.
 - Luego abrir un terminal dentro de esta carpeta y ejecutar el comando `npm init` luego de ejecutar el comando este solicitara que se incerten datos concernientes a la aplicación si un dato se deja vacío se tomara una definición default, este generar un archivo llamado `package.json`.
 - Luego procederemos a ejecutar `npm install express`, esto instalara dos paquetes de dependencias, el anterior mente mencionado framework **Express**.


### Pequeño ejemplo con express

En este pequeño ejemplo estaremos realizando una aplicación simple que muestre en el navegador la frase **Hola mundo!**, para ello debemos seguir estos pasos:
 - Instalaremos una dependencia mas aparte de **Express** la cual es **dotenv** que sirve para el manejo de variables de entorno esta se instala con el siguiente codigo `npm install dotenv`. Estas son dependencias de la aplicación.
 - Luego instalaremos unas cuantas dependencias de desarrollo que no seran aplicadas a la aplicación final luego de ser compilada para esto ejecutaremos el siguiente comando en el terminal `npm install --save-dev nodemon ts-node typescript @types/express @types/node`. Las cuales sirven para:
   - **Nodemon:** Nodemon es una utilidad de la que dependen cerca de 3 millones de proyectos, que monitorizará cualquier cambio en tu fuente y reiniciará automáticamente tu servidor. Perfecto para el desarrollo. 
   - **ts-node:** It JIT o Just In Time (Justo A Tiempo) transforma TypeScript en JavaScript, permitiéndole ejecutar directamente TypeScript en Node.js sin precompilación.
   - **TypeScript:** Permite compilar codigo de TypeScript a JavaScript.
   - **@types:** Estos son tipos de typescript para la ayuda del desarrollo de aplicaciones.
 - Luego ejecutaremos el commando `npx tsc --init` el cual iniciara un espacio de trabajo con typescript, esto lo hara generando un archivo llamado `tsconfig.json` el cual tendra diferentes configuraciones dentro del mismo en este caso solo nos enfocaremos en las siguientes:
    >	{
			"compilerOptions": {
				"target": "ES2020",
				"module": "commonjs",
				"esModuleInterop": true,
				"forceConsistentCasingInFileNames": true,
				"strict": true,
				"skipLibCheck": true
			},
			"include": ["src/**/*"]
		}
 - Luego en la carpeta donde hemos hecho toda la configuración generaremos otra carpeta llamada `src` donde estara almacenado todo nuestro codigo.
 - Dentro de la carpeta `src` crearemos un archivo llamado `index.ts` el cual sera la fuente de ejecución de nuestro projecto.
 - Para poder ejecutar el projecto tambien necesitamos agregar dos scripts a el archivo `package.json`, los cuales son:
	- **dev:** `"start": "npx nodemon --watch ./src ./src/index.ts"` este se utiliza para ejecutar el entorno de desarrollo de la aplicación.
    - **build:** `"build": "npx tsc"` este se utiliza para compliar la aplicación.
 - Ahora vamos a escribir codigo dentro del archivo `index.ts`:
   - Primero tenemos que importar la libreria de **Express** para ello escribimos lo siguiente `import express from "express";`.
   - Ahora para crear la aplicación escribimos `const app = express();`.
   - Luego para formar una ruta inicial escribimos `app.get('/', (req, res) => { res.send("Hello world!"); });` 
   - Y para finalmente iniciar el servidor escribimos `app.listen(3000, () => { console.log('Ejemplo de la aplicación escuchando en el puerto 3000.'); })` este comando iniciara la aplicación e imprimira por la consola el puerto en el que se esta ejecutando.
   - En este punto podremos ejecutar la aplicación ejecutando `npm start` en el terminal.

#### Conectando el app con MySQL

npm install --save mysql
npm install --save-dev @types/mysql

## Angular
---
> ***Angular** es un marco de diseño de aplicaciones y una plataforma de desarrollo para crear aplicaciones de una sola página eficaces y sofisticadas.*

### Como instalarlo

Instalar **Angular** es simple solo hay que ejecutar el siguiente comando `npm install -g @angular/cli` aunque si es posible que se genere un error por problemas de instalación de **NodeJS** de ser este el caso simplemente se ejecuta el instalador de **NodeJS** y se selecciona la opción de reparar.

Luego de tener el **CLI** (Comand Line Interface) de **Angular** el sistema tendra el comando de ejecución **ng** para probar que no hay ningun problema de instalación se puede ejecutar `ng version` si no hay problema al ejecutarlo aparecera la versión instalada en el sistema.

### Configuracion de angular

En este caso se estara trabajando dentro de una carpeta llamada `frontend`, abrimos un terminal en la carpeta de `frontend` y en ella ejecutamos `ng new app_name --directory ./` este comando generara una nueva aplicación llamada `app_name` y estara ubicada en el directorio `frontend` o en el que este ubicada el terminal. Durante la ejecución solicitar datos como si se quiere agregar el **Angular routing** que sirve para las rutas en **Angular** y tambien cual procesador de estilos prefiere, recomiendo utilizar `scss` ya que este permite hacer mas cosas que el `css` sin cambiar mucho la sintaxys.

Al terminar tendriamos la aplicación lista y podemos iniciarla con los comandos `npm start` o `ng serve`. Ambos realizan la misma acción.

### Conectar angular con el backend

# Recursos utiles

[Angular](https://angular.io/) 
[NodeJS](https://nodejs.org/en)
[Express](https://expressjs.com/)
[TypeScript](https://www.typescriptlang.org/)
[npm](https://www.npmjs.com/)
[Road Map](https://roadmap.sh/)
[Chart.js](https://www.chartjs.org/)
[Angular powered bootstrap](https://ng-bootstrap.github.io/#/home)
[W3Schools](https://www.w3schools.com/)
[SCSS](https://sass-lang.com/)
[Nodemon](https://nodemon.io/)
[EnmaScript](https://enmascript.com/)
