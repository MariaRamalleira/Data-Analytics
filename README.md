# 📊 Dashboard de Análisis de Ventas - Supermercado EE.UU.

> Dashboard y análisis exploratorio del rendimiento histórico de ventas (2015-2018).

---

## 📝 1. Descripción del Proyecto
Este proyecto consiste en el desarrollo de un análisis descriptivo y Dashboard interactivo enfocado en evaluar el comportamiento comercial de un supermercado en Estados Unidos. El objetivo principal es transformar datos brutos de transacciones en información útil para entender el rendimiento del negocio. 

El análisis se centra en identificar patrones de consumo en meses específicos, concentraciones geográficas de la facturación, preferencias logísticas en los envíos y la distribución de los ingresos según el perfil del comprador y las categorías de producto.

---

## 📂 2. Estructura del Proyecto
Organización de los archivos y componentes que forman parte del flujo de trabajo:

├── supermarket.csv/       # Base de datos original de transacciones del supermercado.
├── dashboard/             # Archivo de hojas de cálculo con las tablas dinámicas y Dashboard visual.
├── /                      # Informe ejecutivo final con la redacción del análisis.
└── README.md              # Documentación general del proyecto (este archivo).

## ⚙️ 3. Instalación y Requisitos
Para interactuar y explorar el proyecto de forma local, se requieren las siguientes herramientas:

* **Software Requerido:** Google Sheets.
* **Requisitos del Sistema:** Soporte para la ejecución de tablas dinámicas, segmentadores de datos (filtros) y mapas de geolocalización nativos.

---

## 🛠️ 4. Proceso de Limpieza y Transformación de Datos
Antes de realizar cualquier análisis, se llevó a cabo una rigurosa fase de auditoría y preparación para garantizar la calidad y consistencia del conjunto de datos:

* **Tratamiento de Valores Nulos:** Se detectaron campos vacíos en la columna de código postal. Al no afectar directamente a las métricas del análisis de ventas, se transformaron a `0` para evitar celdas vacías por buenas prácticas de gestión de datos.
* **Formateo de Variables:**
  * 📅 **Fechas:** Se unificaron en el formato correspondiente.
  * 💵 **Monedas:** Se aplicó formato de moneda (dólares estadounidenses `$`) a la columna de ingresos, configurando el punto para los miles y la coma para los decimales (`$X.XXX,XX`).
  * 🔢 **Números:** Las variables cuantitativas se estandarizaron como enteros o decimales según correspondiera.
* **Optimización de Interfaz:**
  * 🔽 Se crearon listas desplegables de validación de datos para estandarizar los campos fijos: *Segmento*, *Categoría*, *Ship Mode* y *Región*, evitando errores de escritura.
  * 📝 En las *Subcategorías*, al haber un volumen muy alto de opciones, se mantuvieron intencionadamente en texto plano para evitar saturar al usuario con un menú desplegable poco práctico.

---

## 📈 5. Análisis Descriptivo y Tablas Dinámicas
El conocimiento del negocio se consolidó mediante múltiples tablas dinámicas estructuradas de la siguiente manera:

* **💰 Ingresos Totales:** Suma acumulada de las ventas desde 2015 hasta 2018 (se utiliza el concepto "Ingresos" para clarificar que mide el dinero generado y no la cantidad de artículos).
* **🛒 Cálculo del Ticket Medio Real:** Dado que un mismo `Order ID` (Pedido único) puede aparecer repetido en varias filas si contiene diferentes artículos, se implementó un cálculo en dos fases para evitar sesgos:
  1. Se creó una tabla dinámica intermedia que agrupó el total del dinero gastado por cada `Order ID` único.
  2. A partir de ese consolidado, se calculó el promedio para obtener el importe medio real de cada pedido único.
* **📍 Métricas Complementarias:** Tablas independientes para cruzar ingresos por estados de EE.UU., volumen de pedidos totales (**9.800**) frente a únicos (**4.922**), facturación por categorías/subcategorías (ordenadas de mayor a menor), ventas mensuales históricas, métodos de envío (`COUNT`) e ingresos según el tipo de cliente.

---

## 🖥️ 6. Resultados y Conclusiones
A partir de las tablas dinámicas se construyó un Dashboard interactivo compuesto por un bloque de control de **KPIs principales** y **6 visualizaciones gráficas**:

### 📌 Tarjetas de KPIs Principales
* **Ingresos (Ventas Totales):** $2,41M facturados en el histórico, reflejando un negocio con buena fuerza en el mercado.
* **Pedidos Totales:** 9.800 líneas de órdenes procesadas (agrupadas en 4.922 pedidos únicos, lo que significa que el cliente lleva una media de dos productos por compra).
* **Ticket Medio:** Un gasto promedio por compra de $490,57, indicando un valor por carrito elevado.

### 📊 Conclusiones del Negocio Extraídas de los Gráficos
1. **🗺️ Concentración Geográfica (Gráfico de Mapa):** Las ventas no están distribuidas de forma equitativa. El estado de **California** se posiciona como el líder absoluto y motor económico del supermercado.
2. **🍩 Preferencia de Categorías (Gráfico de Donut):** El dinero acumulado se concentra principalmente en **Furniture (Muebles)** como líder indiscutible, seguido por *Technology* en segundo lugar y *Office Supplies* en tercer puesto (esta última aporta el peso más bajo en facturación debido a sus bajos precios unitarios).
3. **📊 Productos Destacados (Gráfico Top 5 Subcategorías):** El gráfico toma de forma dinámica las primeras 5 filas de la tabla ordenada, aislando los productos que más ingresos generan.
4. **📈 Tendencia Temporal (Gráfico de Líneas):** Se detecta una estacionalidad cíclica clara. Las ventas caen a mínimos históricos al principio de año (**enero y febrero**) debido a la cuesta post-vacacional, y crecen con fuerza a final de año (**septiembre a diciembre**), alcanzando su pico más alto por las campañas navideñas.
5. **🍩 Distribución Logística (Gráfico de Donut):** El método **Standard Class** acapara la inmensa mayoría de los envíos. Los clientes prefieren claramente asumir entregas más lentas a cambio de un coste de transporte económico o gratuito.
6. **🏛️ Perfil del Cliente (Gráfico de Columnas):** Al dividir las ventas por tipo de comprador, el segmento **Consumer (Consumidor Final)** destaca como el principal generador de ingresos del supermercado.

### 🎛️ Interactividad Dinámica
El panel incluye **4 segmentadores (filtros)** conectados a todos los elementos simultáneamente:
* `Filtro por Región` (Visión macro por zonas).
* `Filtro por City` (Auditoría de localidades específicas).
* `Filtro por Segmento` (Cambios de comportamiento según tipo de comprador).
* `Filtro por Categoría` (Aislamiento de métricas para un sector de producto concreto).

---

## 🚀 7. Próximos Pasos
Si el proyecto sigue en desarrollo o se expande en el futuro, las ideas de mejora son:
1. **Calcular la ganancia real:** En vez de mirar solo el dinero que entra en caja, añadir lo que nos cuestan los productos, los envíos, etc. Para saber el beneficio real que nos queda.
2. **Estrategia de Venta Cruzada:** Diseñar promociones para el momento del pago para que el usuario compre más items y así elevar el número de productos comprados por transacción, aprovechando que la media actual es de dos por carrito.
3. **Optimización de Campañas en Q1:** Desarrollar promociones específicas e incentivos durante enero y febrero para mitigar la caída estacional y suavizar la cuesta de inicio de año.

---

## 👥 8. Autores y Contribuciones
* **Desarrollador del Proyecto:** María Ramalleira
* **Contribuciones:** Las contribuciones son bienvenidas. Si deseas proponer mejoras en las fórmulas de cálculo o en el diseño visual del Dashboard, por favor abre un *pull request* o una *issue* en este repositorio. Gracias!
