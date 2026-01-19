# CineMetrics: Análisis de Rentabilidad Cinematográfica 

**De la API al Dashboard:** Proyecto que explora la relación entre presupuestos de producción y éxito en taquilla.

Este repositorio combina ingeniería de datos y visualización de negocios para:
1.  **Automatizar** la extracción y limpieza de datos financieros desde la API de TMDB usando **Python**.
2.  **Analizar** patrones de inversión y retorno (ROI) mediante visualizaciones interactivas en **Power BI**.
   
# ¿Qué hace este script?
1.  **Conecta** a la API de *The Movie Database* (TMDB).
2.  **Busca** las películas más populares del momento.
3.  **Investiga** (hace una segunda petición) los detalles financieros de cada película, ya que esa información no viene en la lista general.
4.  **Limpia** los datos: Elimina películas que tienen presupuesto $0 o datos faltantes.
5.  **Calcula** el Beneficio Neto (Ingresos - Gastos).
6.  **Guarda** todo en un archivo CSV limpio listo para analizar.

# Tecnologías
* **Python 3.12**
* **Librerías:** `requests` (API), `csv` (Manejo de archivos), `time` (Rate limiting).
* **Seguridad:** Uso de `.gitignore` para protección de API Keys

## Instrucciones de Uso

1.  **Clonar el repositorio:**
    ```bash
    git clone [https://github.com/TU_USUARIO/CineMetrics-ETL-Pipeline.git](https://github.com/TU_USUARIO/CineMetrics-ETL-Pipeline.git)
    ```
2.  **Configurar Credenciales:**
    * Obtén tu API Key gratis en [TMDB](https://www.themoviedb.org/).
    * Cambia el nombre del archivo `config_example.py` a `config.py`.
    * Pega tu API Key dentro de ese archivo.
      
3.  **Ejecutar el script:**
    ```bash
    python main.py
    ```
## Resultado Final
El script creará la carpeta `data/` con el archivo `fact_peliculas_financiero.csv` conteniendo:
* `Titulo`, `Fecha`, `Presupuesto_USD`, `Ingresos_USD`, `Popularidad`, etc.


## Visualización y Análisis de Datos

Para este análisis, utilicé **Power BI** para filtrar y visualizar los datos extraídos previamente con Python.

### Gráfico de Dispersión: Inversión vs. Facturación
Pregunta a responder: 
1. ¿Gastar más presupuesto garantiza proporcionalmente mayores ingresos o existen rendimientos decrecientes?


### Insights Clave
![Gráficos](https://github.com/deniserosales/CineMetrics-ETL-Pipeline/blob/main/Imagenes_analisis_cine/Dashboard.png)
1.   Existe una **correlación positiva**; a medida que aumenta la inversión (eje X), tiende a aumentar la facturación (eje Y), aunque no es una regla estricta debido a la alta dispersión de los datos.
2.  Los proyectos con mayor retorno de inversión (ROI) parecen concentrarse en el rango de presupuesto de **$200M - $300M**. Es aquí donde encontramos los picos más altos de facturación (superando los $2.5 mil M).
3.  Curiosamente, las producciones más costosas del dataset (presupuestos >$500M, a la derecha del gráfico) **no** lograron los ingresos más altos. Esto sugiere que el riesgo financiero aumenta considerablemente después de cierto punto de gasto, sin garantizar un retorno proporcional.
4.  Joker e It prueban que la rentabilidad real (% ROI) viene de la gestión eficiente de costos.
