# CineMetrics-ETL-Pipeline
Pipeline automatizado de extracción, transformación y carga (ETL) en Python que consume la API de TMDB para generar datasets financieros de cine y analizar el ROI en Power BI.

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
