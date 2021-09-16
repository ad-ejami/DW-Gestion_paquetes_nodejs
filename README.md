# Acerca de NPM, paquetes y módulos
**¿Qué es NPM (node package manager) ?** Es un gestor de paquetes, el más popular que tiene JavaScript, donde encontrarás una gran cantidad de recursos para poder implementar en tus proyectos. También vas a poder crear tus propios paquetes y compartirlos con toda la comunidad.

### Instalacion de node
Comprobar la version de node
```
sudo apt-get install nodejs npm
node -v
npm -v
```
### Cómo actualizar NPM
```
npm install -g npm
```

## Comandos basicos
crear archivos package.json el cual contiene toda la información acerca de nuestro proyecto
```
$ npm init 
```
crear rápido un archivo package.json para configurarlo despues
```
$ npm init -y 
```
Asignar nuestros datos a npm pero no es tan obligatorio hacer esto
```
npm set init.author.email <email>
npm set init.author.name <name>
```
## Instalación de dependencias
Las dependencias se deben instalar en nuestra captera raís de nuestro proyecto
```
$ npm i <pkg>
$ npm i <pkg> | npm install <pkg> --save | npm install <pkg> -S
```
por defecto se instala como una independencia `requerida` para el proyecto, es decir, que el paquete que instalas es necesario para vivir en producción.

```
$ npm install <pkg> -D | npm install <pkg> --save-dev 
```
Este flag nos va a permitir establecer que el paquete que vamso a instalar solo es necesario en nuestro entorno local o el entorno de desarrollo.

```
$ npm install <pkg> -g 
```
Instalar un paquete de forma global. Esto permite que podamos utilizar este paquete en diferentes proyectos. Por lo general, se deben instalar estod paquetes con permisos de administrador.

Si no queremos colocar permisos de administrador a cada rato, podemos seguir esta guía: https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally

```
$ npm list -g --depth 0
```
ver los paquetes que están instalados de forma global
```
$ npm list
```
para listar los paquetes que tiene un proyecto en especifico
```
$ npm install <pkg> -O
```
Podemos instalar de forma opcional un paquete con este comando
```
$ npm install <pkg> --dry-run
```
Este flag indica que el paquete no va a ser instalado dentro del proyecto, simplemente es una simulación, nada mas nos muestra el output como si se fuese instalado.

```
$ npm install <pkg> -f | npm install <pkg> --force
```
Instalar algún paquete de forma forzada. Nos va a permitir instalar este paquete forzando esa instalación a que sea desde el último recurso desde el servidor de NPM

```
$ npm install <pkg>@<version>
```
Para instalar algún paquete con una versión especifica

## Actualizar y eliminar

```
$ npm outdate
```
Para ver si se encuentran desactualizados los paquetes y, además nos indica las ultimas versiones de esos paquetes

```
$ npm update
```
Podemos actualizar los paquetes que se encuentran desactualizados
```
$ npm install <pkg>@latest
```
Podemos actualizar un paquete en especifico a su ultima versión con este comando
```
$ npm uninstall <pkg>
```
Para desinstalar o eliminar un paquete en especifico. Esto lo elimina del package.json y node_moduls
```
$ npm install <pkg> --no-save
```
Nos permite desinstalar o eliminar un paquete, pero sin eliminarlo del package.json pero si del node_moduls

## Simbolos ^ y ~
```
$ npm install <pkg> --sabe-exact | npm install <pkg> -E
```
Para instalar la dependencia en su version exacta

## Ejecutar tareas (script)
```
$ npm run <script-name>
```
Podemos ejecutar nuestros propios scripts con este comando.
## Solución de problemas

Uno de los problemas que podemos toparnos en la construccion de nuestros proyectos, trabajando con un equipo, es que nuestros archivos de node_moduls no estén correctamente instalados o tengamos una versión anterior.

Una forma de solucionarlo es eliminar la carpeta de 'node_moduls' o ejecutar un comando que a nosotros nos va a dar seguridad de limpiar ese 'cache'que pueda llegar a existir

```
$ npm cache clean -f | npm cache clean --force
```
elimina la cache
```
$ npm cache verify
```
con esto vamos a poder ver si ya la cache ha sido eliminada y que todas las instalaciones de nuestros recursos van a ir hacia los servidores de NPM
```
$ npm audit
```
Para ver las vulnerabilidades que tenemos en nuestro proyecto
```
$ npm audit --json
```
Nos genera un json con información un poco mas detallada de lo que esta pasando con estos paquetes que instalamos.
```
$ npm audit fix
```
Para solucionar las vulnerabilidades que tengamos en nuestro proyecto. Básicamente, actualiza a la ultima versión nuestros paquetes con las dependencias que requerian

## Probar nuestros paquetes de npm localmente
Ya debemos tener todo el proyecto configurado, para luego ejecutar los siguientes comandos:
```
$ npm install <pkg> -O
```
