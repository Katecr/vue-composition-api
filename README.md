<div align="center">
  <h1>VUE </h1>
  <h2>Componentes y Composition API</h2>
</div>

<div style="margin-bottom:50px;"></div>

# Tabla de contenido
1. [Introducción a Vue CLI](#introducción-a-vue-cli)
2. [Estructura del proyecto](#estructura-del-proyecto)
3. [Componentes dinámicos](#componentes-dinámicos)
4. [Componentes asíncronos](#componentes-asíncronos)
5. [Transiciones](#transiciones)

<div style="margin-bottom:50px;"></div>

## Introducción a Vue CLI

> https://cli.vuejs.org/guide/installation.html

1. Instalar el CLI e inicializar proyecto con Vite
```bash
npm init vue@latest
```

2. Pasarnos a la carpeta del proyecto creado
```bash
cd project_name
```

3. Installamos npm
```bash
npm install
```

4. Inicializar el servidor
```bash
npm run dev
```
===

1. Instalar el CLI e inicializar proyecto con esta
```bash
npm install -g @vue/cli
```

2. Creamos el proyecto y le asignamos un nombre
```bash
vue create project_name
```

3. Pasarnos a la carpeta del proyecto creado
```bash
cd project_name
```
4. Inicializar el servidor
```bash
npm run serve
```

> Con ```vue ui``` se puede generar una interfaz para administrar todas las opciones del proyecto. Pero si se instalo con vite no funciona.


<div style="margin-bottom:50px;"></div>

## Estructura del proyecto

- **package.json** → Tiene nuestras dependencias, nuestros scripts que correremos con npm, nos prepara el terreno para poder trabajar.
- **README.md** → Podemos ver los distintos comandos para poder instalar dependencias, ejecutar el servidor de desarrollo, compilar para producción, eslinter, documentación oficial.
- **babel.config.js** → Configuración de babel. Es pequeño debido a que el equipo de desarrollo detrás de este proyecto ya se encargó de generar un preset de babel js, que ya lo tiene instalado nuestro proyecto.
- **.gitignore** → Ignorar archivos para no subirlos al repositorio.
- **.eslintrc.js** → Archivo para configurar eslint, este archivo agrega dos reglas, cuando se tenga activado el modo productivo se va a pedir que no se tengan console.log() y que no hayan debugger.
- **.browserslistrc** → Le indicamos con que versiones de navegadores debe trabajar.
- **node_modules** → En esta carpeta van a estar todos los módulos y dependencias que tiene nuestro proyecto.
- **public/** → Esta carpeta contiene un favicon.ico y un index.html, corre en un servidor de archivos estáticos.
- **src/** → La carpeta más importante, vamos a colocar todos los archivos en los que de verdad vamos a estar trabajando durante el desarrollo del proyecto. El archivo main.js es el archivo que va a encontrar el proyecto de webpack y lo va a utilizar para inicializar todo lo que tiene que ver con JavaScript en nuestro proyecto.
- **src/App.vue** → Componente principal, es en el que se creará la App en main.js.
- **src/assets** → Contendrá archivos estáticos, la diferencia entre src/assets y public/ es que assets se va a empaquetar junto con los archivos del proyecto, es decir, se va adjuntar todo el código javascript, css y html que se genere y también se van a incluir estos archivos estáticos en la carpeta dist (Creada con npm run build), lo que pasa con public es que esto no pasa a la carpeta dist, sin embargo, quedaría más del lado del servido, mientras que assets queda del lado del cliente.
- **src/components** → Esta carpeta contendrá todos los componentes hechos en Vue.js que utilizaremos en nuestro proyecto. Esta carpeta se puede estructurar como sea, se pueden tener subcarpetas, por ejemplo.

<div style="margin-bottom:50px;"></div>

## Componentes dinámicos

 Vue nos ofrece la posibilidad de generar componente dinamicos usando tag de vue ```<component>```

 ha este tag le defininimos la directriz ```v-bind``` para hacerlo reactivo, para complementar el v-bind se usa la palabra reservada de vue ```is```, este va tomar el valor del componente(nombre del componente definido en la propiedad components del componente(que lo contiene) y no el nombre con el que lo estamos importando.), osea que dependiendo del valor de is se muestra cierto componente u otro.

```javascript
 component :is="componente" />
```

Para que los estilos solo afecte al componente de interes y no de manera global a los otros componentes añadimos en el tag style la palabra reservada scoped

```html
<style scoped>
    css
</style>
```

<div style="margin-bottom:50px;"></div>

## Componentes asíncronos

Son aquellos componentes que quiero que carguen despues de que carguen los componentes principales e importantes de mi aplicacion. Para poder hacer esto debo importar de vue la propiedad defineAsyncComponent, antes del export default.

```javascript
import {defineAsyncComponent} from "vue";

const HelloWorld = defineAsyncComponent(()=> import("./components/HelloWorld.vue"))
```
### Ventajas
1. Que los proyectos carguen mucho más rapido
2. Que los proyectos solo carguen los componbentes que van a necesitar


<div style="margin-bottom:50px;"></div>

## Transiciones

> https://vuejs.org/guide/built-ins/transition.html

Permite aplicar css al momento de determinar si un elemento aparece o desaparece en pantalla.

Por ejemplo: Utilizamos la transición para agregar un desvanecimiento al clickear el botón que muestra (U oculta) el menú.

```javascript
<script>
import Menu from "./components/vMenu.vue";

export default {
  name: "App",
  components: { Menu },
  data() {
    return {
      show: false,
    };
  },
};
</script>

<template>
    <button @click="show = !show">Menu</button>
    <transition name="fade">
      <Menu v-show="show" />
    </transition>
</template>

<style >
.fade-enter-from,
.fade-leave-to{
  opacity:0;
}
.fade-enter-active,
.fade-leave-active{
  transition: opacity 0.3s ease;
}
</style>
```
Los modificadores que tiene una trancisión es:

**from:** cuando se inicia la transición
**to:** cuando se termina la transición
**active:** cuando se está ejecutando la transición

Para que funcione la transición, se debe agregar la clase .fade-enter-active o .fade-leave-active a los elementos que se quieren animar.

**fade-enter-active:** cuando se inicia la transición

**fade-leave-active:** cuando se termina la transición