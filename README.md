# Solution Manager Scope Effor Anlyzer (SEA) y Business Process Change Analyzer (BPCA).

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

Posteriormente se debe indicar el alcance del test a realizar, para este caso concreo se selecciona un alcance creado que no tiene ningún tipo de filtro y se analiza el 100% del alcance.

![](https://github.com/apachon/sap-sm-sea-bpca/blob/8176826168a0d00640110f58ce5bc4430f3069a0/images/2021-12-13%2012_17_45-Business%20Process%20Change%20Analyzer%20-%20Internet%20Explorer.png)

Se selecciona el alcance creado.

![]()
