# 📊 Cuadro de Mando Integral Divisional (Balanced Scorecard + Clustering K-Means)

## 🎯 Finalidad del Proyecto y Problemática de Negocio
Evaluar la actuación de múltiples centros de responsabilidad distribuidos geográficamente suele generar **parálisis por análisis** en la alta dirección. Cuando una corporación debe controlar decenas de filiales, analizar planillas financieras individuales de forma aislada impide ver el comportamiento holístico y estratégico de los gerentes de división.

Basado estrictamente en las **Unidades 8 y 9 (Evaluación de Actuación, Centros de Responsabilidad y Cuadro de Mando Integral) de la cátedra de Costos y Gestión II (FCE-UNC)**, este proyecto ofrece una solución analítica de vanguardia. Diseña un **Balanced Scorecard automatizado** que evalúa a las sucursales cruzando la **Perspectiva Financiera** (métricas de *Rendimiento sobre la Inversión - RSI* e *Ingreso Residual*, penalizando a los gerentes según una tasa de costo de capital del 15%) con la **Perspectiva de Procesos Internos** (*% de Entregas a Tiempo*). Para evitar la auditoría manual, se inyecta un modelo de **Machine Learning No Supervisado** que agrupa y segmenta automáticamente las sucursales por su verdadero nivel real de desempeño y management.

### ¿Cuál es la diferencia de trabajar sin este sistema?
* **Sin el sistema:** El directorio de la empresa revisa 80 filas de Excel de forma plana. Un gerente puede mostrar un RSI aceptable aisladamente, pero ocultar una destrucción crítica de valor económico debido a activos ociosos o cuellos de botella logísticos.
* **Con el sistema:** El algoritmo de clustering fusiona todas las dimensiones y traza fronteras estadísticas exactas. Mapea y tiñe el mapa corporativo de forma automática, permitiendo a la gerencia general enfocar sus recursos y auditorías internas exclusivamente en los centros clasificados en estado crítico.

---

## 🛠️ Tecnologías Utilizadas
* **Lenguaje Principal:** Python (Desarrollado en Google Colab con analítica predictiva avanzada).
* **Algoritmo de Inteligencia Artificial:** Scikit-Learn (Clustering K-Means y escalamiento estadístico `StandardScaler`).
* **Base de Datos en la Nube:** Neon SQL (Motor PostgreSQL 16), estructurado bajo el esquema independiente `proyecto3_scorecard`.
* **Visualización de Negocios:** Power BI Desktop (Cuadro de Mando Integral Corporativo).

---

## 🔑 Configuración del Entorno y Seguridad (Secrets)
Para proteger los canales de infraestructura en la nube y evitar la exposición pública de credenciales de producción en repositorios abiertos, el código implementa **buenas prácticas de seguridad de Google Colab**.

> ⚠️ **IMPORTANTE:** Para ejecutar el cuaderno correctamente, debes ir al menú lateral izquierdo de tu entorno de Google Colab, hacer clic en el icono de la llave 🔑 (**Secrets**), añadir una nueva variable llamada `NEON_DB_URL` y pegar allí tu cadena de conexión encriptada de Neon SQL (`postgresql://...`). No olvides activar el interruptor de "Notebook access".

---

## 🔄 Flujo de Trabajo y Fases del Desarrollo

1. **Fase 1: Instalación de Librerías y Configuración del Entorno:** Importación de dependencias de preprocesamiento estadístico avanzadas y algoritmos de agrupamiento de la suite `sklearn`.
2. **Fase 2: Conexión Segura a Neon SQL utilizando Secrets:** Autenticación fluida e independiente hacia el clúster unificado de la base de datos central en la nube.
3. **Fase 3: Simulación de Centros de Responsabilidad:** Creación de indicadores para 80 sucursales en Argentina con variabilidad real de activos y utilidades operativas. Se programan a nivel de código las fórmulas obligatorias de control de gestión: **RSI** e **Ingreso Residual** (restando la tasa de costo de capital corporativo fijada en 15%).
4. **Fase 4: Machine Learning No Supervisado (Clustering K-Means):** Debido a las diferencias de escala entre tasas decimales y activos millonarios, se aplica un escalador estándar (`StandardScaler`) para normalizar los datos. Se entrena el algoritmo K-Means para agrupar matemáticamente las operaciones en 3 niveles de gestión.
5. **Fase 5: Ingesta Idempotente en Neon SQL (Método Drop & Create):** Carga estructurada de la matriz del Balanced Scorecard con su nueva columna de clusters adjunta dentro del esquema `proyecto3_scorecard`, vaciando instancias anteriores para evitar colisiones.
6. **Fase 6: Creación de Vista Analítica para Power BI:** Construcción de la vista `v_bi_cuadro_mando`. Mediante sentencias lógicas en el servidor Postgres, traduce los fríos clusters numéricos (`0, 1, 2`) en dimensiones estratégicas de negocio legibles para el directorio ("Unidad Estrella", "Desempeño Estándar", "Desempeño Crítico").
7. **Fase 7: Auditoría Visual y Descarga Local:** Renderizado de gráficos de dispersión (`scatterplot`) en Python para validar las fronteras de K-Means antes de explotar la información y opción de descarga automática en formato CSV.

---

## 💾 Documentos y Archivos de Salida
* 📄 **`proyecto3_scorecard.cuadro_mando_centros`:** Tabla física con los activos, utilidades e indicadores de gestión guardada en la nube de Neon SQL.
* 👁️ **`proyecto3_scorecard.v_bi_cuadro_mando`:** Vista SQL analítica refinada con alias profesionales e interpretación de clusters para Power BI.
* 📊 **`Reporte_3_Balanced_Scorecard.pbix`:** Archivo de Power BI Desktop independiente (*Balanced Scorecard Divisional*) estructurado con KPIs ejecutivos corporativos, segmentación interactiva por regiones de Argentina y formato condicional de alertas.
* 📝 **`cuadro_mando_gestion.csv`:** Archivo plano descargable con el dataset final unificado para validaciones rápidas fuera de la base de datos.
