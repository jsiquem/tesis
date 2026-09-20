# Registro de pruebas funcionales ejecutadas

**Fecha:** 20 de septiembre de 2026  
**Sistema:** Sistema Web de gestión contable  
**Frontend observado:** Angular  
**Módulos evaluados:** Facturas FEL/SAT, Proveedores y Nomenclatura contable  
**Usuario de prueba:** Administrador  
**Entorno:** Navegador local autenticado en `localhost:4200`

## Criterio de registro

Se utilizó el criterio **Aprobado** cuando la acción produjo un resultado observable y coherente en la interfaz. Se utilizó **No verificable** cuando el control estaba visible, pero la acción no produjo un cambio observable o requería una condición que no estaba disponible. Se utilizó **No ejecutado** cuando no fue posible completar la operación por falta de un archivo o de datos de entrada.

## Matriz de resultados

| ID | Módulo | Tipo | Aspecto evaluado | Procedimiento realizado | Resultado observado | Estado |
|---|---|---|---|---|---|---|
| FEL-01 | Facturas FEL/SAT | SIS | Acceso y disponibilidad del módulo | Se inició sesión y se navegó a `/facturas/fel`. | La pantalla cargó correctamente y mostró el estado “POSTGRESQL CONECTADO”, el área de carga y la validación previa. | **Aprobado** |
| FEL-02 | Facturas FEL/SAT | SIS | Consulta histórica de facturas | Se presionó “Mostrar datos cargados”. | El control permaneció visible, pero no apareció un catálogo o listado adicional después de la interacción. | **No verificable** |
| FEL-03 | Facturas FEL/SAT | SIS | Disponibilidad de carga de archivo | Se revisó el control de selección de archivo y los formatos permitidos. | La interfaz acepta archivos CSV, XLS o XLSX de hasta 15 MB. No se completó la carga porque no había un archivo FEL de prueba disponible. | **No ejecutado** |
| FEL-04 | Facturas FEL/SAT | SIS | Validaciones previas a guardar | Se verificó el bloque de validación mostrado antes del procesamiento. | La pantalla declara validaciones de receptor, NIT, autorización, IVA, duplicados y cambios inmutables; no se pudo comprobar con un archivo real. | **No verificable** |
| PROV-01 | Proveedores | SIS | Consulta del directorio | Se abrió `/proveedores` y se revisó el directorio. | Se visualizaron 4 proveedores, estados activos, condiciones de crédito, retenciones y cuentas contables asociadas. | **Aprobado** |
| PROV-02 | Proveedores | SIS | Selección de modalidad de partida | Se cambió “Tipo de partida” de “Mensual por proveedor” a “Transitoria general”. | La interfaz cambió correctamente la modalidad y ocultó el selector individual de proveedor. | **Aprobado** |
| PROV-03 | Proveedores | SIS | Generación de partida transitoria | Se seleccionó “Transitoria general” y se presionó “Generar partidas”. | El botón recibió la interacción, pero no se observó una nueva partida, mensaje de confirmación ni cambio numérico verificable. | **No verificable** |
| NOM-01 | Nomenclatura | SIS | Carga del catálogo contable | Se abrió `/nomenclatura` y se revisaron los indicadores. | Se visualizaron 39 cuentas, 4 tipos registrados y estado de catálogo “Activo”. | **Aprobado** |
| NOM-02 | Nomenclatura | SIS | Búsqueda de cuenta por código | Se ingresó `610112` en el buscador. | El catálogo se filtró a una cuenta: “DEPRECIACIONES Y COMBUSTIBLES”, tipo Gasto, naturaleza Debe y estado Activa. | **Aprobado** |
| NOM-03 | Nomenclatura | SIS | Apertura del formulario de nueva cuenta | Se presionó “Nueva cuenta”. | El botón recibió la interacción, pero no se mostró un formulario ni una ventana de registro observable. | **No verificable** |

## Resumen numérico

| Estado | Cantidad | Porcentaje sobre 10 casos |
|---|---:|---:|
| Aprobado | 5 | 50 % |
| No verificable | 4 | 40 % |
| No ejecutado | 1 | 10 % |
| **Total** | **10** | **100 %** |

## Interpretación

Las pruebas ejecutadas confirman que el sistema actual permite acceder a los tres módulos seleccionados, consultar el directorio de proveedores, cambiar la modalidad de generación de partidas, cargar el catálogo de nomenclatura y filtrar una cuenta contable específica. Sin embargo, no es metodológicamente correcto declarar una aprobación total. La carga FEL requiere un archivo de prueba y las acciones de consulta histórica, generación de partidas y apertura de formularios no produjeron un resultado visible durante la ejecución. Estos casos deben repetirse después de verificar la implementación de los eventos o de disponer de datos de prueba.

## Evidencia y limitaciones

La evidencia primaria de esta ejecución corresponde a las vistas observadas en el navegador autenticado. Las capturas existentes del sistema pueden asociarse a FEL, Proveedores y Nomenclatura, pero no sustituyen la evidencia específica de una operación que no produjo respuesta visible. Por ello, los cuatro casos marcados como “No verificable” no deben representarse como pruebas aprobadas en las gráficas de la tesis.
