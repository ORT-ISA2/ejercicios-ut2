# UT2 - Ejercicios de prácticas de entrega continua 

Para todos los ejercicios de esta unidad se utilizará como base el mismo ejemplo de proyecto con tecnologías definidas en los obligatorios del semestre pasado. La solución está dividida en varios componentes de back-end y front-end.  
El back-end lo componen una API REST, con la lógica y persistencia programada en proyectos C#.  
El front-end está compuesto por una interfaz de usuario web, programada sobre el framework Angular funcionando en node.JS. 

Para cada una de las clases programadas (unidad de testing) en el proyecto de lógica del negocio, hay una clase de test unitario correspondiente.  
Se debe considerar que las prácticas son para un equipo de desarrollo compuesto por 3 a 5 integrantes. 

Como paso previo a los ejercicios, los equipos deben crear un proyecto C# en Visual Studio y un proyecto Angular en node.JS para identificar los archivos y la configuración por defecto generada por la IDE. 

 

## 1. Control de versiones. 
El equipo de desarrollo utiliza un repositorio Git en la nube para versionar el código fuente. La documentación del proyecto se gestiona en Google Drive sin un procedimiento de versionado definido. La documentación incluye los planes de proyecto, resúmenes de reuniones, especificaciones de funciones del sistema.   
Los casos de test unitarios están el repositorio Git, pero los escenarios de prueba con ejemplos de datos del negocio son gestionados localmente por cada tester. Para realizar las pruebas los testers crean una base de datos local y la modifican con los datos de ejemplos. 

Se pide:  
 a. Identifique los elementos de la configuración del proyecto.  
 b. Defina una estructura de repositorio adecuada.  
 c. Establezca el procedimiento de versionado para el proyecto.  


## 2. Desarrollo trunk-based. 
El equipo de desarrollo utiliza una estrategia de ramas por feature. Cada vez que comienza el desarrollo de una nueva función o corrección de bug, se crea una nueva rama siguiendo un criterio de nombre con el número de la issue. Las ramas se mantienen durante el trabajo de la feature y se hace merge con la rama ‘development’ cuando los desarrolladores deciden pasar el trabajo a testing. 
  
Se pide:  
 a. ¿Qué problemas presenta este enfoque desde la perspectiva de DevOps?  
 b. ¿Qué pasos debe dar el equipo para pasar a una estrategia de desarrollo trunk-based?  
 c. Defina las ramas, frecuencia y criterios de merge.  

 
## 3. Proceso de build. 
En la situación actual, el proceso de build lo realiza cada desarrollador localmente en su propia IDE. El proceso de build no está definido en forma explícita, cada desarrollador decide como optimizar la compilación según sus necesidades de debug.  
  
Se pide:  
 a. Realice un esquema del proceso de build básico para cada componente del proyecto según su lenguaje.  
 b. Codifique el proceso de build en cada plataforma tecnológica.  
 c. Ejecute el proceso de build en forma local y analice la salida.  

 
## 4. Automatización del build.  
a. Ejecute el proceso de build desde GitHub Actions y estabilícelo.    
b. En cada componente del proyecto anterior introduzca errores que bloqueen el build.  
c. Ejecute el proceso de build desde GitHub Actions.  
d. Identifique el log para cada mensaje de error del proceso de build.  
e. Corrija los errores iterativamente hasta que ejecute correctamente el workflow definido en GitHub Actions.  


## 5. Repositorio de artefactos. 
El proceso de build genera los artefactos necesarios para ejecutar el proyecto (archivos binarios, configuraciones, recursos, bases de datos). Estos artefactos son generados localmente y empaquetados como ‘releases’ del proyecto. Los testers y cualquiera de los participantes del value stream pueden acceder a los artefactos y las notas de cada release en una carpeta compartida.  
El equipo de desarrollo quiere automatizar y realizar con mayor frecuencia el proceso de release al ambiente de staging. Se desea usar GitHub como repositorio de artefactos del proyecto. 

Se pide:  
a. Definir un criterio de identificación de releases.  
b. En GitHub, aplicar tags y crear una nueva release.  
c. Agregar manualmente los archivos necesarios para ejecutar (binarios generados en el proceso de build del ejercicio anterior).  
d. Agregar notas de la release.  
e. Casos de prueba.  


## 6. Entornos tipo producción. 
La API REST creada para la solución tiene como objetivo de producción ejecutar en un servidor Windows 10 con Internet Information Services (IIS). El el mismo servidor se ejecuta una instancia de la base de datos SQL Server Express. El componente del front end (aplicación web Angular) se ejecutará en un runtime node.JS en un servidor Linux Ubuntu. Las versiones de cada componente del stack de ejecución no están definidas explícitamente en el proyecto. 

Se pide:  
a. Defina las versiones de componentes del stack del entorno de producción.  
b. Desarrolle un proceso de configuración utilizando Ansible.  
c. Investigue cómo realizar la gestión de la configuración a través de GitHub Actions.  


## 7. Ejecución de tests unitarios (MS Test). 
El equipo de desarrollo codifica test unitarios para cada funcionalidad desarrollada usando la técnica Test-Driven Development (TDD). Los test se codifican antes de la funcionalidad y se ejecutan para verificar que no pasan. Luego se codifica la funcionalidad hasta que pasan todos los test unitarios. Finalmente se realiza refactoring y agregan test que no fueron codificados inicialmente. La ejecución de los test unitarios la realiza cada desarrollador localmente desde la IDE. El equipo tiene como objetivo de mejora ejecutar todos los test unitarios para el proyecto que tiene la lógica principal del dominio cada vez que se suban cambios al repositorio. El proyecto está programado en C#. 

Se pide:  
a. Definir un workflow en GitHub Actions que ejecute todos los test unitarios para el proyecto cuando se sube un cambio.   
b. Para los procesos de build y test unitario, discuta la secuencia de ejecución más adecuada: I. Test, si pasa build. II. Build, si pasa test. III. Ejecutar en paralelo.   
c. Analizar el informe de cobertura de la ejecución de test unitario.  
d. Agregar al workflow una condición para que falle la ejecución cuando la cobertura es menor al 95%.  


## 8. Análisis de código. 
El equipo de desarrollo no tiene definido un estándar de codificación explícito, utiliza la configuración por defecto del editor de la IDE. Se desea estandarizar la codificación y utilizar análisis estático de código en el marco de la práctica de integración continua.  

Se pide:  
a. Identifique los estándares de código a utilizar para los lenguajes de los distintos componentes de la solución.  
b. En la IDE Visual Studio Code, investigue la forma de guardar una configuración de editor para que sea compartida por el equipo de desarrollo en el repositorio.  
c. Identifique herramientas que se pueden integrar a la IDE y ejecutar localmente para analizar la conformidad con los estándares de codificación C# y JavaScript. d. Identifique herramientas de análisis estático de código (linters) para los lenguajes de la solución.  
d. Analice la salida del analizar de código para decidir los warnings críticos y opcionales. Configure el analizador para evitar falsos positivos con respecto a criterio de análisis.  
e. Agregue al workflow de build y test unitario la ejecución de las herramientas de análisis de código.  
f. Agregue en el workflow una condición que no haga fallar el proceso si hay warnings críticos.  


## 9. Patrón deployment pipeline. 
Sobre la base de las mejoras anteriores al proceso de desarrollo, se desea practicar la integración continua utilizando el patrón deployment pipeline.  

Se pide:  
a. Identificar la actividades manuales y automáticas a realizar en el deployment pipeline.    
b. Crear un workflow unificado en GitHub Actions que ejecute las actividades del pipeline.   
c. Definir las condiciones en que el proceso falla y emite notificaciones.   
