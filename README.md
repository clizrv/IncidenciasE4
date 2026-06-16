##  Reporte Final de Ingeniería de Pruebas

[![Status](https://img.shields.io/badge/Status-NO%20LIBERADO-red?style=for-the-badge)](https://papeleria-desktop.onrender.com/)
[![Academic Project](https://img.shields.io/badge/IPN-UPIICSA-blue?style=for-the-badge)](https://www.upiicsa.ipn.mx/)
[![QA Tools](https://img.shields.io/badge/QA%20Tools-Selenium%20%7C%20Locust%20%7C%20TestCaseStudio-orange?style=for-the-badge)](#5-herramientas-utilizadas)

Documentación institucional y técnica del ciclo de calidad y aseguramiento de software para el sistema de escritorio **Papelería GO-MI**.

---

##  Información Institucional

* **Institución:** Instituto Politécnico Nacional (IPN)
* **Unidad Académica:** Unidad Profesional Interdisciplinaria de Ingeniería y Ciencias Sociales y Administrativas (UPIICSA)
* **Programa Académico:** Ingeniería en Informática
* **Unidad de Aprendizaje:** Ingeniería de pruebas
* **Secuencia:** 6NM62
* **Profesor:** Saul López Avila
* **Fecha de Entrega:** 16/06/2026
* **Equipo Evaluador (Equipo 4):**
  * Avila Sanchez Oswaldo Rafael
  * Flores Bracho Fernando
  * Flores Roa Jorge Alejandro
  * García Pérez Cristofer Alexander
  * Rojas Vargas Claudia Lizbeth 
  * Sánchez Vega Estrella

---

##  1. Información General del Proyecto

### 1.1 Nombre del Sistema
**Papelería GO-MI**

### 1.2 Descripción del Sistema
La **Papelería GO-MI** es una aplicación de escritorio diseñada como un sistema de gestión integral. Su objetivo principal es automatizar, centralizar y digitalizar en una base de datos local todos los procesos operativos que anteriormente se realizaban de manera manual (tales como registros en papel u hojas de cálculo), optimizando el control de inventarios, ventas y administración de personal.

### 1.3 Tecnología del Sistema
El sistema cuenta con un diseño arquitectónico particular enfocado al entorno de escritorio pero distribuido/renderizado mediante tecnologías modernas:

* **Modelo:** Aplicación monolítica de escritorio con separación interna en capas (UI, Lógica de Negocio y Datos).
* **Frontend:** Interfaz gráfica desarrollada con **Flet** (Framework de Python que renderiza sobre *Flutter Web/Desktop Canvas*).
* **Backend:** Lógica de negocio e interacciones construidas de forma nativa en **Python 3.10**.
* **Base de Datos:** **MySQL** de despliegue y almacenamiento local (embebida/sin necesidad de un servidor externo tradicional de alta infraestructura).
* **Control de Versiones:** **GitHub** para la gestión del código fuente.

### 1.4 URL del Sistema / Despliegue
* **URL de Acceso/Distribución:** [https://papeleria-desktop.onrender.com/](https://papeleria-desktop.onrender.com/)

---

##  2. Módulos y Funcionalidades Probadas

### 2.1 Módulos del Sistema

| Módulo | Descripción Funcional |
| :--- | :--- |
| **Iniciar Sesión** | Pantalla de autenticación segura donde el usuario ingresa sus credenciales para ser redirigido al panel correspondiente según su rol (**Encargado / Empleado**). |
| **Panel de Control** | Dashboard principal del administrador/encargado para visualizar indicadores del establecimiento comercial. |
| **Gestión de Empleados** | Vista general con el listado del personal que centraliza las operaciones de altas, bajas operativas y edición. |
| **Alta de Empleados** | Formulario controlado para registrar nuevos trabajadores en la base de datos local. |
| **Baja de Empleados** | Control interactivo para desactivar o modificar el estado de un empleado dentro del entorno operativo. |
| **Edición de Empleados** | Formulario dinámico para actualizar los datos personales o laborales de un empleado existente. |
| **Gestión de Productos** | Vista maestra del inventario con capacidades de filtrado avanzado por categorías. |
| **Agregar Producto** | Formulario de captura para insertar nuevas mercancías y stock inicial en el inventario. |
| **Eliminar Producto** | Flujo lógico/físico destinado a retirar un artículo del catálogo del sistema. |
| **Registrar Sugerencia** | Buzón digital interno donde se capturan comentarios y solicitudes de productos sugeridos por los clientes. |

### 2.2 Funcionalidades Críticas del Sistema
1. **Gestión Eficiente del Inventario:** Registro y actualización en tiempo real del stock (entradas, salidas y existencias) con alertas automáticas de stock mínimo y búsquedas indexadas por categoría/precio.
2. **Automatización del Proceso de Ventas:** Cálculo automatizado de totales y almacenamiento completo del historial de transacciones (fechas, productos, totales económicos).
3. **Buzón de Sugerencia de Productos:** Registro y seguimiento formal de productos sugeridos por clientes para análisis de viabilidad comercial.
4. **Reportes y Análisis Estratégicos:** Generación de métricas de ventas por periodos (diario, semanal, mensual, trimestral), detección de tendencias de compra y cálculo automático de márgenes de ganancia.
5. **Seguridad y Accesibilidad de Datos:** Consultas de alta velocidad, restricciones de acceso basadas en roles para datos sensibles (costos, ganancias netas) y respaldos automáticos contra pérdida de información.

---

##  3. Documentación (Insumos para Pruebas)

*Los artefactos técnicos base utilizados como oráculo de pruebas y especificación de requisitos:*
1. **Diccionario de Datos:** Documento técnico que especifica los tipos de datos, longitudes, restricciones de llaves (primarias/foráneas) y nulidades de las tablas de la base de datos embebida.
2. **Diagrama de Casos de Uso:** Modelo estructural que define los límites del sistema, los actores involucrados (Encargado, Empleado, Cliente) y las fronteras de sus interacciones funcionales.

---

##  4. Pruebas Realizadas

El aseguramiento de calidad se estructuró a través de un **Smoke Test** exploratorio y **3 Ciclos de Prueba Funcionales exhaustivos**, sumado a evaluaciones No Funcionales.

### 4.1 Pruebas Funcionales

####  Smoke Test (Prueba de Humo)
Fase exploratoria inicial enfocada en validar la estabilidad elemental en cuatro módulos clave: *Iniciar Sesión*, *Agregar Producto*, *Vista de Sugerencias* y *Registro de Nuevos Empleados*.

* **Resultado Global:** **Inestable.** La fase detectó múltiples discrepancias severas entre el comportamiento de la aplicación y la documentación de referencia, exponiendo flujos de negocio sin restricciones básicas.

#####  Incidencias Detectadas en Smoke Test:
1. **Crítica (Flujo de Negocio): Venta de Productos Sin Restricciones.** El sistema permite procesar y registrar transacciones con cantidades equivalentes a `"0"` artículos en el módulo de ventas y actualizar las listas con valores nulos.
   * *Sugerencia:* Implementar validaciones duras en backend y frontend que impidan avanzar en el flujo si la cantidad es $\le 0$ o si excede el stock real disponible.
2. **Alta (Funcionalidad Ausente): Apartados Inexistentes.** No se localizaron visualmente en la interfaz gráfica los flujos correspondientes a **"Baja de Empleado"** ni **"Eliminar Producto"**. Asimismo, en la ventana de *Registro de Compras*, el campo para ingresar el costo/precio está deshabilitado o ausente.
3. **Media (Validaciones): Permisividad de Datos.** Al modificar productos, se permite guardar cambios dejando la `"Descripción"` totalmente vacía. En el alta de personal, el sistema permite registrar usuarios duplicados y acepta nombres con símbolos y caracteres especiales (`@`, `$`, `*`). Los mensajes de error del sistema ante datos inválidos son genéricos y no orientan al operador.

---

####  CICLO 1: Validación Manual y Mapeo Lógico
Ejecución 100% manual orientada a mapear el comportamiento orgánico de las ventanas y certificar los resultados esperados frente a la lógica de negocio sin herramientas automatizadas.

#####  Incidencias Detectadas en Ciclo 1:
* **Crítica:** El módulo de ventas procesa e introduce ítems con cantidad `0` en la tabla de preventa. Adicionalmente, los formularios del inventario aceptan la inserción y guardado de precios y costos con **números negativos** (ej. `-4`, `-5`).
* **Alta:** Persiste el bloqueo técnico por la ausencia total del módulo **"Eliminar Producto"** en la interfaz física de esta versión del sistema.
* **Media:** Al editar un artículo, el sistema limpia la `"Descripción"` por defecto dejándola vacía de forma automática si no se altera, guardando el registro sin alertar.
* **Baja:** El flujo de baja de empleados fue reemplazado exitosamente por un botón que alterna el estado (*Activo/Inactivo*); sin embargo, la paleta de colores seleccionada provoca un contraste deficiente que pierde legibilidad en pantalla.
  * *Sugerencia:* Ajustar tipografía o fondo del botón para asegurar un contraste óptimo bajo pautas de accesibilidad.

---

####  CICLO 2: Regresión y Automatización Parcial
Ejecución mixta (manual/automatizada) enfocada en los casos fallidos del Ciclo 1 tras el primer bloque de correcciones del equipo de desarrollo. Se incorporaron scripts de automatización para los flujos de *Agregar Producto* y *Editar Producto*.

* **Resultado Global:** Se validó la mitigación de fallas del ciclo anterior, pero se detectó la persistencia de problemas de validación de datos en campos numéricos y la ausencia sistemática de interfaces.

#####  Incidencias Detectadas en Ciclo 2:
* **Crítica:** Durante la edición en el catálogo de productos, el sistema continúa permitiendo actualizar registros con valores de stock o precios de venta **negativos** (ej. `-10`). Al ingresar caracteres alfanuméricos erróneos en el stock, la interfaz muestra el banner `"Stock inválido"`, pero el flujo no bloquea la inserción en la base de datos, provocando desincronización.
* **Alta:** Bloqueo persistente. Sigue ausente la interfaz para dar de baja mercancía.
  * *Sugerencia:* Desarrollar e incorporar inmediatamente los botones y vistas finales para `Eliminar` y `Cancelar` dentro de la ventana de gestión de productos.
* **Media:** Falta de confirmaciones intuitivas de éxito. Al guardar un producto modificado, la UI redirige a la pantalla anterior abruptamente sin notificar la correcta transacción.
  * *Sugerencia:* Estandarizar alertas e incorporar modales de confirmación explícitos como `"Edición de producto exitosa"`.
* **Baja (UX):** Los campos opcionales no están señalizados. El campo `"Descripción"` guarda valores vacíos con éxito, lo cual es correcto por negocio, pero confunde al usuario al no contar con una etiqueta visual de `(Opcional)`.

---

####  CICLO 3: Certificación Final (Ciclo de Cierre)
Fase de certificación dirigida exclusivamente a comprobar el estado de los defectos remanentes del Ciclo 2.

#####  Incidencias Detectadas en Ciclo 3:
1. **Crítica:** El sistema permite guardar modificaciones que dejan el stock total en **números rojos** (saldos inconsistentes/negativos). Aunque el caso de prueba corre sin romperse a nivel código, la regla de negocio es vulnerada.
   * *Sugerencia:* Implementar un bloqueo estricto en el backend que impida guardar si el cálculo de existencias netas da un valor negativo.
2. **Alta:** Bloqueo Permanente. **El módulo "Eliminar Producto" no se incluyó en la compilación final**. No se puede cerrar el ciclo de vida del inventario.
3. **Media:** Sigue sin desplegarse un mensaje informativo de éxito tras realizar la actualización de un producto en la UI, a pesar de impactar correctamente la base de datos.

> ** Gestión de Issues:** Todas las incidencias se registraron y asignaron en tiempo real a través de **GitHub Issues**. Aquellas clasificadas como resueltas fueron cerradas previa ejecución de pruebas de regresión. Las incidencias remanentes en el Ciclo 3 permanecen abiertas en calidad de sugerencias/bloqueos pendientes de atención por el equipo de desarrollo.

---

###  Automatización de Pruebas (Caja Negra)

Para el aseguramiento de calidad del sistema, se seleccionó **Selenium WebDriver** bajo Python para interactuar con la aplicación desde la perspectiva del usuario final.

####  El Reto Técnico de Flet (Flutter Web Canvas)
El sistema está desarrollado sobre **Flet**, un framework que renderiza la UI utilizando la tecnología de **Flutter Web**. Esta arquitectura dibuja todos los componentes (botones, inputs, etiquetas) dentro de un lienzo interactivo de **HTML5 Canvas**. Como consecuencia, los componentes se vuelven **invisibles para los localizadores tradicionales del DOM** (IDs, XPaths clásicos, selectores CSS) de Selenium.

####  Solución Implementada
El equipo de QA desarrolló un script auxiliar en Python encargado de mapear y extraer las **coordenadas físicas relativas** de cada elemento visual generado por el lienzo de Flet. Posteriormente, mediante la clase `ActionChains` de Selenium, se automatizaron las interacciones simulando clics y envíos de texto basados en estas coordenadas precisas.

Se automatizaron con éxito dos de los flujos de mayor criticidad y recurrencia diaria:
1. **Registrar Sugerencias de Empleados**
2. **Registrar Empleado Nuevo**

---

### 4.2 Pruebas No Funcionales (Carga y Estrés)

Se realizaron pruebas de rendimiento utilizando **Locust** para evaluar el comportamiento del sistema ante un incremento progresivo de concurrencia de usuarios simultáneos.

* **Comportamiento del Servidor / Disponibilidad:** El sistema demostró una robusta resiliencia arquitectónica, manteniendo una disponibilidad cercana al **90%** bajo cargas extremas de más de **3,500 usuarios concurrentes** y registrando **0% de errores de ejecución** (sin caídas críticas de proceso) a los **1,000 usuarios simultáneos**.
* **Degradación del Rendimiento (Saturación):** Se identificó un punto de saturación crítico entre los **700 y 1,000 usuarios concurrentes**. La tasa de procesamiento se estancó en un máximo de **44 solicitudes por segundo (RPS)**, provocando un aumento exponencial en los tiempos de respuesta:
  * **Percentil 50 (P50):** 18 segundos de tiempo de respuesta.
  * **Percentil 95 (P95):** 24 segundos de tiempo de respuesta.

```
[ Carga de Usuarios Simultáneos ]
  0 -> 700 usuarios   ======> Rendimiento Óptimo / Latencia Baja
700 -> 1000 usuarios  ======> Degradación Significativa (Saturación del Servidor)
1000+ usuarios        ======> Tiempos de Respuesta Críticos (18s - 24s) / Disponibilidad 90%
```

* **Diagnóstico Técnico:** Aunque la aplicación no colapsa, la latencia observada rompe los umbrales de usabilidad aceptables, degradando la experiencia del usuario final debido a la ralentización en las consultas a la base de datos local bajo concurrencia masiva.

---

##  5. Herramientas Utilizadas

* **TestCase Studio:** Utilizada en la fase de **Smoke Test** para registrar de forma automatizada las acciones de usuario (clics, ingresos de datos y capturas de pantalla integradas), acelerando la documentación de evidencias funcionales.
* **GitHub Issues:** Plataforma centralizada para el control, categorización por prioridad (Crítica, Alta, Media, Baja), asignación y seguimiento del ciclo de vida de los bugs detectados.
* **Selenium WebDriver:** Framework de automatización empleado para mitigar el error humano en pruebas de regresión repetitivas mediante scripts capaces de simular las interacciones de usuario final sobre el lienzo de Flet.
* **Locust:** Herramienta de pruebas de carga distribuida basada en código Python, utilizada para simular la concurrencia masiva y obtener las métricas de rendimiento y límites del servidor.

---

##  6. Plan de Trabajo (Planeado vs. Real)

### 6.1 Planeado
Definición de hitos temporales para el análisis de requerimientos, diseño de casos de prueba, ejecución de ciclos funcionales (Smoke, Ciclo 1, Ciclo 2), automatización de scripts, pruebas de rendimiento y fase de certificación final.

### 6.2 Real
El seguimiento del proyecto y ejecución de tareas se administró de manera transparente a través de la herramienta Planner. Las estadísticas finales reflejan variaciones debido al tiempo extendido en el análisis de incidencias y re-ejecución de pruebas por bloques de código no corregidos.

* **Enlace al Tablero de Control:** [Planner - PlanDeTrabajo](https://planner.microsoft.com/) *(Nota: Reemplazar por enlace definitivo)*

---

##  7. Conclusión y Dictamen de Calidad

Tras concluir el Ciclo 3 y habiendo analizado los resultados de las fases de pruebas funcionales, automatizadas y de rendimiento bajo el oráculo del sistema de gestión **"Papelería GO-MI"**, el Equipo 4 emite un dictamen formal de:

### 🛑 DICTAMEN: NO LIBERACIÓN (NO APTO PARA PRODUCCIÓN)

#### Fundamentación Técnica:

1. **Inmadurez del Sistema e Incompletitud Funcional:** A pesar de encontrarnos en la fase de certificación final (Ciclo 3), el software presenta un bloqueo de nivel alto debido a la **ausencia total del módulo "Eliminar Producto"**, lo que rompe el ciclo operativo básico del negocio de inventarios especificado en los requisitos.
2. **Deficiencias en Validación de Datos:** El sistema mantiene brechas graves en la integridad de datos, permitiendo el guardado de parámetros que resultan en **stock negativo (números rojos)** y aceptando entradas de texto ilimitadas en las descripciones sin restricciones en el frontend, lo cual pone en riesgo la estabilidad de la base de datos embebida y rompe la estética de la UI.
3. **Experiencia de Usuario Comprometida (UX/UI):** La persistencia de fallos de usabilidad menores, la falta de avisos de confirmación claros ante operaciones exitosas y el contraste deficiente en las alertas de estado reducen drásticamente la fidelidad de la aplicación.
4. **Riesgo Crítico de Rendimiento bajo Carga:** Las pruebas con Locust revelaron que, bajo escenarios de alta demanda comercial (700-1000 usuarios), el servidor se satura elevando los tiempos de respuesta hasta los **18 y 24 segundos**. Un sistema automatizado no puede ser liberado si introduce tiempos de espera que superan considerablemente a los procesos manuales tradicionales.

#### Recomendaciones de Salida:
Se recomienda **congelar la liberación del software** y retornar el proyecto a la fase de desarrollo para cumplir estrictamente con los siguientes puntos antes de una nueva evaluación de QA:
* Implementar el 100% de los módulos ausentes (*Eliminar Producto*).
* Incorporar validaciones y restricciones duras en el backend contra números negativos en campos de inventario y precios.
* Aplicar máscaras de caracteres y límites (*maxlength*) en los campos de texto del lienzo de Flet.
* Optimizar los índices de consulta en la base de datos MySQL embebida para abatir los tiempos de respuesta ante escenarios de alta concurrencia.
