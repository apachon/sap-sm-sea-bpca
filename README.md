# Solution Manager Scope Effor Anlyzer (SEA) y Business Process Change Analyzer (BPCA)

## Introducción

**Solution Manager Scope Effor Anlyzer** (SEA en adelnate) permite realizar un análisis inicial en el caso que se realice algún proyecto de actualización que permitirá tener información sobre el impacto del cambio, tanto a nivel de código, como para estimar las pruebas necesarias, para validar la nueva configuración.

**Business Process Change Analyzer** (BPCA en adelante) realiza un análisis sobre el impacto que tendrán los cambios en los procesos de negocio.

Tanto el análisis de SEA como de BPCA se realiza teniendo en cuenta las estadísticas de uso del sistema, se recomienda contar con estadísticas actualizadas de al menos 3 meses previos a la ejecución de uno u otro análisis.
Así mismo, la ejecución de SEA es una herramienta orientativa, pensada para la fase de planificación de proyectos, y sus resultados no deben considerarse como única fuente para la ejecución del mismo. 

BPCA necesitara estar alimentado de los casos de tests para ser más eficiente en su resultado. 

Se accederá a está herramientas accediendo a la transacción **SM_WORKCENTER - Solution Manager: Work Centers URL.**

Es posible que al iniciarse el navegador aparezca el siguiente mensaje de advertencia.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/main/images/2021-12-09%2010_43_26-Este%20sitio%20no%20es%20seguro.%20-%20Internet%20Explorer.png)

En caso que aparezca se pulsa la opción Continuar en la página werb (no recomendado) :) y ya aparece el panel del usuario con el que nos hemos logado y las tiles que tiene accesible organizadas por secciones, como en este caso son Custon Code Management, Change Management o Test Suite.![](https://github.com/apachon/sap-sm-sea-bpca/blob/e7e44c9375a6e75cf5e2f99121888a26179aaa9d/images/2021-12-09%2010_46_42-SAP%20Easy%20Access%20%20-%20%20User%20Menu%20for%20ANGEL%20PACHON.png)

## SEA

El análisis de SEA se basa basa en las estadísticas de uso y en las relaciones de **Boom of Materials (BOMs)** de los objetos de primer nivel, para proporcionar el listado de ejecutables (Transacciones y Programas) que se tienen que validar durante las pruebas. Por medio del **Test Scope Optimizer (TSO)** es capaz de calcular la combinación de ejecutables óptima para reducir el número de pruebas.

Se recomienda ejecutar en análisis SEA en horas en las que no haya mucha carga de trabajo en el sistema, ya que la generación de BOMs genera una carga importante en el sistema.

### Ejecución de análisis SEA

Se ejecuta el siguiente tile 

![](https://github.com/apachon/sap-sm-sea-bpca/blob/d7b018c9948243739601ec9f5befa30a07e06de4/images/2021-12-09%2011_15_35-Home%20-%20Internet%20Explorer.png)

Y se selecciona la opción **New** para crear un nuevo análisis

![](https://github.com/apachon/sap-sm-sea-bpca/blob/ffa90212a1d15d63fc86f2ca0e3ee7beb8b3c148/images/2021-12-09%2011_18_28-Scope%20and%20Effort%20Analyzer%20-%20Internet%20Explorer.png)

Se selecciona el sistema y la versión a analizar. Previamente deberá estar creado el maintenance planner con los cambios que se van a realizar.

> El maintance planner id es un documento que se crea desde el Marketplace de SAP cuando dices a que Enhacement o nivel de Packages quieres subir te genera este documento, el usuario con el que se genera el análisis SEA debe tener permisos para ver estos documentos desde el OSS. Esta parte normalmente viene dada por el equipo de BASIS que nos tiene que informar en cada caso que Maintance Planner ID seleccionar.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/8502e46e652176a7c4eca2309a05f448ead78805/images/2021-12-13%2011_11_18-Create%C2%A0Analysis_%C2%A0Step%C2%A01%C2%A0%C2%A0(Select%C2%A0System%C2%A0and%C2%A0Assign%C2%A0Maintenance%C2%A0Plan)%20-%20Internet%20.png)

Se selecciona el Planner Transaction Id

![](https://github.com/apachon/sap-sm-sea-bpca/blob/f7148c5736fb6236a9fd9c3cf50f3a25ba0089bd/images/2021-12-09%2011_43_39-Create%C2%A0Analysis_%C2%A0Step%C2%A01%C2%A0%C2%A0(Select%C2%A0System%C2%A0and%C2%A0Assign%C2%A0Maintenance%C2%A0Plan)%20-%20Internet%20.png)

Se especifica el sistema dónde están los desarrollos, el sistema dónde están las estadisticas y dónde está el sistema en el que se va a realizar la optimización del test.

Aquí se recomienta informar los sistemas de producción para los dos primeros apartados, dónde están los objetos custom y modificaciones a analizar y las estadísticas. En cambio se recomienda informar un entorno no productivo para el Test Scope Optimization para no sobrecargar el entorno de producción.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/a0072610a51e23a584b8ce268843d38bacb7f389/images/2021-12-09%2011_58_49-Create%C2%A0Analysis_%C2%A0Step%C2%A02%C2%A0%C2%A0(Specify%C2%A0Additional%C2%A0Systems)%20-%20Internet%20Explorer.png)

Una vez completado este paso se selecciona la Solución y la Branch.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/22bbfa331c05c4f87fc85d4729a149f1f70ead9f/images/2021-12-13%2011_39_11-Create%C2%A0Analysis_%C2%A0Step%C2%A03%C2%A0%C2%A0(Specify%C2%A0Solution%C2%A0Documentation)%20-%20Internet%20Explorer.png)

Posteriormente se debe indicar el alcance del test a realizar, para este caso concreto se selecciona un alcance creado que no tiene ningún tipo de filtro y se analiza el 100% del alcance.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/8176826168a0d00640110f58ce5bc4430f3069a0/images/2021-12-13%2012_17_45-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Se selecciona el alcance creado.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/8ddb2f6bef5583affc18bbf9cba6090eaf95e07b/images/2021-12-13%2012_21_54-Create%C2%A0Analysis_%C2%A0Step%C2%A04%C2%A0%C2%A0(Specify%C2%A0Test%C2%A0Scope)%20-%20Internet%20Explorer.png)

Y por último en el últiomo paso antes de lanzar análisis se revisan toda la configuración que se ha relizado del análisis.

Una vez validado se puede lanzar análisis **Start Analysis**.

### Análisis SEA

## BPCA

El escenario de BPCA es una utilidad de Solution Manager que permite identificar el impacto que pueden producir los cambios.
Verificar que se ha ejecutado correctamente el job de carga de TBOMs. El job esta programado cada 3 semanas.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/a19e0a9714f5aab14e8833ae3e64d24a9e198a23/images/2021-12-13%2016_09_42-Job%20Overview.png)

### Puntos Críticos

Hay cuatro puntos críticos a los que hay que enfrentarse cuando se produce un cambio en un sistema con distintos procesos de negocio.

- Pruebas en Landscapes con sistemas heterógeneos
- Soluciones de Update de SAP que afectan a objetos críticos en un proceso de negocio
- Setup del sistema para testeos y mantenimiento de los juegos de datos.
- Esfuerzo para la creación y mantenimiento de pruebas automáticas.

### Dar Solución esos puntos

1. SAP Solution Manager actúa como Hub central para controlar eventos de cambio y testeos integrados E2E.
2. Funcionalidad para planificación de testeos basándose en riesgo. Pruebas de funcionales y de regresión.
3. Interfases a Partner test Suites.

### Casos de Uso

Se identifican 4 casos de uso para los que aplica BPCA:

1. **Cambio de Customizing**.
   Se produce una modificación en el Customizing que afecta a un proceso de negocio. Hay que identificar qué procesos de negocio se ven afectados y planificar así las pruebas que es necesario realizar para asegurar que ese cambio funciona correctamente.
2. **Desarrollo Custom**.
   Se realiza una modificación en un objeto Custom como un programa, módulo de función, clase, etc. Hay que identificar qué procesos de negocio se ven afectados y planificar así las pruebas que es necesario realizar para asegurar que ese cambio funciona correctamente.
3. **Activación de EhP Business Function planificado**.
   El despliegue de un EhP provoca la activación de una Business Function. Hay que identificar qué procesos de negocio se ven afectados y planificar así las pruebas que es necesario realizar para asegurar que ese cambio funciona correctamente.
4. **Optimización del alcance de las pruebas necesarias por el despliegue de un SP/EhP**.
   Se debe realizar el despliegue de un SP o un EhP SAP. BPCA permite analizar el alcance del impacto de este cambio sobre los procesos de negocio y calcular el esfuerzo a realizar para generar un plan de pruebas optimizado.

### Crear análisis BPCA

Se accede a la transacción **SM_WORKCENTER - Solution Manager: Work Centers URL** y se accede al tile **Business Process Change Analyzer**.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/19edcd905e7096f88e8f889adcbd69371de3e193/images/2021-12-13%2015_35_53-Home%20-%20Internet%20Explorer.png)

Se selecciona la opción del tipo de impacto que queremos analizar, en nuestro caso el análisis de impacto de transportar una orden de transporte, es decir, se selcciona la opción **Transport Requests**.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/9530a124fbcf46735eb5f07fb068d953c79a3962/images/2021-12-13%2020_05_23-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Se selecciona el sistema y el mandante donde está la orden con los cambios a analizar.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/9bc8200d2f187bc25f7a4ff9ad78273bd2c5d666/images/2021-12-13%2020_08_58-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Se selecciona la orden, para ello hay que entrar mediante matchcode y buscar la orden concreta.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/e53a9095f925d06f42e65218a6c9ba5bf554ffce/images/2021-12-14%2010_35_56-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Se selecciona la solucion, el branch y la vista. Que es el alcance del análisis a realizar.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/c81e7b79c3601c0ba8bf08edab363ba315897c62/images/2021-12-14%2010_45_18-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Por último se añade una descripción al análisis.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/c81e7b79c3601c0ba8bf08edab363ba315897c62/images/2021-12-14%2010_45_18-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

En parámetros opcionales se podrá definir el TSO (Test Scope Optimization)
TSO es una herramienta que se puede utilizar una vez realizado el análisis. Muestra estadísticas del análisis que facilitan la toma de decisiones para realizar los tests necesarios una vez realizada la modificación. 

También permite recomendar casos de Test que cubran un porcentaje determinado de objetos modificados agrupando los procesos que contienen el mayor número de impactos en la modificación.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/34372993d6061a0438e8951a1bf1149e2ad28811/images/2021-12-14%2010_50_25-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Por último se lanza el análisis.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/a32441e92209b89f5606ef2637946b5c51fa239f/images/2021-12-14%2010_52_13-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Una vez finalizado mostrará los resultados y se podrán revisar e ir creando los casos de test necesarios para ir documentando los procesos de negocio con sus respectivos tests.
