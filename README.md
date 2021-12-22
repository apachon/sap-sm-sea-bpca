# Solution Manager Scope Effor Anlyzer (SEA) y Business Process Change Analyzer (BPCA)

## Introducción

**Solution Manager Scope Effor Anlyzer** (SEA en adelante) permite realizar un análisis inicial en el caso que se realice algún proyecto de actualización que permitirá tener información sobre el impacto del cambio, tanto a nivel de código, como para estimar las pruebas necesarias, para validar la nueva configuración.

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

### Interpretar análisis SEA

Una vez finalizado el análisis se pulsa en el nombre del análisis se accede al analisis realizado.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/50a6677fc43e19161e578114cdadd64297b38f55/images/2021-12-17%2015_42_15-Scope%20and%20Effort%20Analyzer%20-%20Internet%20Explorer.png)

Una vez dentro se muestra tres pestañas.

#### Summary

En este apartado se hace un resumen de todo el esfuerzo, lo calcula en días, contando como un día laboral de 8 horas y una persona.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/ddf10e102874ff6e4acbbcc80a2ccb8f8f8a1db7/images/2021-12-17%2016_00_11-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

La grafica muestra la distribución de las modificaciones de los objetos custom en las siguientes tres categorías:

- **Ajustes Requeridos**: Los objetos en esta categoría se verán impactados durante el update y deberán ser revisados minucioisamente después del update para evitar errores. Las modificaciones que están en conflicto con la versión del upgrade y que aparece en las herramientas SPAU y SPDD aparecerán en esta categoría.
- **Ajustes propuestos:** Los objetos custom que son asignados a esta categoría usan objetos del repositorio de SAP que han sido cambiados en esta nueva versión del producto. Sin embargo, estos objetos no suelen causar ningún problema a la hora de trabajar por lo que podremos evitar ajustar estos objetos a no ser que nos causen algún error o problema en la fase de tests.
- **Ajustes no necesarios:** En esta categoría aparecen todos los objetos que no son impactados durante el upgrade o que están marcados como no usados. 

En la parte de abajo aparece la grafica de **Regression Test Efforts for Optimized Test Scope** que muestra todos los esfuerzos relacionados con las pruebas de regresión funcional.
Nos muestra el esfuerdo medido en días que nos supondría realizar todos los test de regresión.
Muestra los días de esfuerzo que ganaríamos y el porcentaje total de tiempo ahorrado.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/ae584b906c70469c7dfcb260bd2e560a4b3dbca7/images/2021-12-17%2016_23_21-sap-sm-sea-bpca_2021-12-17%2016_00_11-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Interne.png)

#### Modifications / Custom Developments

##### Overview

En esta sección nos muestra los objetos que se deben analizar y los divide en objetos que pertenecen a la SPDD, a la SPAU y el impacto por aplicación. Primero nos muestra una imagen global en la que se muestran los siguinetes gráficos para tener una visión global.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/9cd2cb459edd5bfb07a29c4588a33a4704b36a2d/images/2021-12-17%2016_31_50-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

![](https://github.com/apachon/sap-sm-sea-bpca/blob/1e1dcbbbd87fa534000f260025dba2f65f43ee25/images/2021-12-17%2016_39_34-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

![](https://github.com/apachon/sap-sm-sea-bpca/blob/daa4e719a58bd71fe4c3d414bbab7dd0324f5a6a/images/2021-12-17%2016_41_16-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

![](https://github.com/apachon/sap-sm-sea-bpca/blob/104b0f57bdd1a00907e368abb61c6e7300b17e63/images/2021-12-17%2016_42_21-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

##### Detail

Para acceder al detalle se puede acceder mediente el desplegable:

![](https://github.com/apachon/sap-sm-sea-bpca/blob/184db0d66317129c1574ef4aa0a282b8361f5938/images/2021-12-20%2017_26_15-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

En esta sección nos muestra los objetos que se deben analizar y los divide en objetos que pertenecen a la SPDD, a la SPAU y el impacto por aplicación.

Dentro de este detalle hay dos pestañas para movernos entre el detalle de **Modifications** y el detalle de **Custom Developments**.

![]()

##### Detail - Modications

En modifications lo primero que muestra es una estimación de lo que va costar pasar la SPAU y la SPDD.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/038dcc16b02da9d67b67be45ac0f16a295c6f812/images/2021-12-20%2017_16_16-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

![](https://github.com/apachon/sap-sm-sea-bpca/blob/039b8a8259019b204df1453a15172990589a071b/images/2021-12-20%2017_17_41-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

A continuación se muestra el impacto de las modificaciones a realizar durante la SPAU por módulo.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/eaf337c21981870447c4dc2fe022bda679f4aa1f/images/2021-12-20%2017_20_05-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

A continuación se muestra el impacto de las modificaciones a realizar durante la SPDD por módulo.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/3007888478a0c492e2ae6d0ab1f9a1b8b012a002/images/2021-12-20%2017_22_26-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

Por último muestra una lista de los objetos impactados.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/8bc5f885248a832494e06a609454b35c38e71bfc/images/2021-12-20%2017_23_49-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

##### Detail - Custom Developments

Lo primero que se muestra es una estimación en días del esfuerzo de realizar para realizar ajustes y pruebas.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/3543fcd885272028a38a9b17ac660596b9c916f8/images/2021-12-21%2015_28_50-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

Lo siguinete que se muestra es un recuento de objetos clasificados por impacto.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/010291b1f1156f59298d57454a8dc502f462d0d0/images/2021-12-21%2015_34_53-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

Después de muestra una grafica con el numero de objetos impactados por cada uno de los paquetes de desarrollo.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/7735019d3527afd4e5e27f6e1841521cc43d9091/images/2021-12-21%2015_37_43-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

Y el esfuerzo Requerido en cada uno de estos paquetes.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/cf6815ffc92d76cff961e2163edd4ae4ad128c3c/images/2021-12-21%2015_39_51-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

Por último se muestra un minucioso detalle de todos los objetos custom a adaptar.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/ea54947c10ead8dd0d7a0942f6bee6606832bdd2/images/2021-12-21%2015_42_10-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

#### Test Management

En este apartado volvemos a tener dos apartados diferenciados, **Overview** y **Detail**.

##### Overview

En el primer apartado se muestran tres gráficos:

- Nos muestra la suma del esfuerzo de ejecución de todos los casos de test de los proyectos o soluciones seleccionados en el análisis.

- Proporciona un desglose del esfuerzo de la prueba de todos los procesos impactados con TSO (Test scope optimization).

- Proporciona un desglose del esfuerzo de la prueba de todos los procesos impactados sin TSO (Test scope optimization).

![](https://github.com/apachon/sap-sm-sea-bpca/blob/15ec4e4ef12fb6b677e73f94703705d79aa08ce8/images/2021-12-22%2010_08_44-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

En el segundo apartado se muestra el apartado Solution Documentation.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/6083f48eba0e9c54286dda7b850ec61b47e17c93/images/2021-12-22%2010_17_44-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

Statistics Test Management.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/eb11bddd99753eda9694d207d1ddd34ebe889ec0/images/2021-12-22%2010_31_56-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

Test Scope and Effort with TSO - Full Scope versus Custom Code and Modifications.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/f4b9607d56aa3d1116ad335c1bd9950e50ff7191/images/2021-12-22%2010_33_45-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

Test Case recomendations.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/743c11d519359b91e3b551a33b91d665a5a923eb/images/2021-12-22%2010_35_05-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

##### Detail

En este apartado se muestra una overview del alcance de la prueba y las actividades de mantenimiento.
En la columna X vemos los procesos de negocio impactados.
En la columna Y “izquierda” nos muestra el porcentaje de la cobertura de la prueba 
En la columna Y “derecha” nos muestra el esfuerzo en días que nos supondrá la realización de las pruebas.
La línea Azul nos muestra la cobertura de las pruebas con puntos en cada paso del proceso.
La zona verde es el alcance de la prueba seleccionada
Columnas naranjas es el esfuerzo de las pruebas manuales.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/bef91f8e8d7b18f17a994f598ffd097cf0cd131c/images/2021-12-22%2010_52_59-Analysis_%C2%A0ERP_FUSION_SP23_20211216%20-%20Internet%20Explorer.png)

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

> En esta prueba la orden tiene la modificación de un módulo de funciones estándar que es llamado desde la EXIT **MV50AFZ1** **Userexit a partir de 21D para tratamiento de entregas**
> 
> A tener en cuenta para comprobar que tiene sentido con las acciones que obtenemos como resultado en el análisis.

Se selecciona la solucion, el branch y la vista. Que es el alcance del análisis a realizar.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/c81e7b79c3601c0ba8bf08edab363ba315897c62/images/2021-12-14%2010_45_18-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Por último se añade una descripción al análisis.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/0204cd740105169697230d0bbbc041edc5f29f1d/images/2021-12-14%2010_47_45-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

En parámetros opcionales se podrá definir el TSO (Test Scope Optimization)
TSO es una herramienta que se puede utilizar una vez realizado el análisis. Muestra estadísticas del análisis que facilitan la toma de decisiones para realizar los tests necesarios una vez realizada la modificación. 

También permite recomendar casos de Test que cubran un porcentaje determinado de objetos modificados agrupando los procesos que contienen el mayor número de impactos en la modificación.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/34372993d6061a0438e8951a1bf1149e2ad28811/images/2021-12-14%2010_50_25-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Por último se lanza el análisis.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/a32441e92209b89f5606ef2637946b5c51fa239f/images/2021-12-14%2010_52_13-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Una vez finalizado mostrará los resultados y se podrán revisar e ir creando los casos de test necesarios para ir documentando los procesos de negocio con sus respectivos tests.

Para acceder a los resultados se pulsa el botón Optimize Test Scope.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/b24d863707af2177dfeafd4f92f6ecedc218eecc/images/2021-12-14%2017_00_43-Bandeja%20de%20entrada%20-%20angel.pachon@stratesys-ts.com%20-%20Outlook%20-%20copia.png)

En el apartado **Test Scope Optimization Ranking** en el apartado **Ranked List** se indican las transacciones/ejecutables que hay que habría que probar para cumplir con el 100% de las pruebas. Para esto hay que pulsar el botón **Show Executables**.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/66f4ec42661e74724db65a6ab010384db7353d1b/images/2021-12-14%2017_22_21-BPCA_%C2%A0Test%C2%A0Scope%C2%A0Optimization%20-%20Internet%20Explorer.png)

Aquí se puede observar que con probar las 2 transacciones a probar **FB02** y **DRFOUT** se cubriría el 100% de las pruebas con un esfuerzo acumulado de 4 horas.

En la pestaña **Test Case Recomendations**

![](https://github.com/apachon/sap-sm-sea-bpca/blob/4fe5b742115bb30d08398364a6091d633f3be177/images/2021-12-14%2017_28_23-BPCA_%C2%A0Test%C2%A0Scope%C2%A0Optimization%20-%20Internet%20Explorer.png)

Vemos un remumen que nos indica cosas interesantes como que crear un script para realizar esta prueba de manera automática y acumulada costaría unas 20 horas, cada vez que haya que modifcar este script automático nos costaría 3,5 horas. Pero una vez hecho las pruebas nos costarían un esfuerzo de 0,5 horas frente a las 4 horas que cuesta hacer las pruebas de manera manual, todas estas estimaciónes de esfuerzos son <u>orientativas</u>.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/0d4ce5a057ebe989a58dc37122d7b777c53cdaba/images/2021-12-14%2017_32_52-BPCA_%C2%A0Test%C2%A0Scope%C2%A0Optimization%20-%20Internet%20Explorer.png)

En el resumen final vemos como nos recomienda que se creen New Automated Test Case para cada transacción el esfuerzo de crear cada uno de ellos, el esfuerzo acumulado, el esfuerzo de probar a mano cada una de las transacciones y el esfuerzo de probarlas una vez automatizadas estas pruebas.
