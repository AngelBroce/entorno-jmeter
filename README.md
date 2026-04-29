# Laboratorio: Prueba de Carga con JMeter 🚀

Este repositorio contiene la configuración y automatización de una prueba de carga y rendimiento utilizando **Apache JMeter**, dirigida al sitio web de pruebas [SauceDemo](https://saucedemo.com/).

La prueba está automatizada completamente mediante **GitHub Actions** para que se ejecute en la nube sin consumir recursos locales.

## 📂 Contenido del Repositorio

*   **`mi_prueba.jmx`**: Es el archivo principal (Test Plan) de JMeter. Contiene toda la lógica de la prueba:
    *   Petición HTTP tipo `GET` a la ruta `/` de `saucedemo.com`.
    *   Duración de la prueba: **1 minuto continuo**.
    *   Tiempo de Ramp-up: **5 segundos**.
    *   Temporizador constante (Tiempo de pensamiento): **300ms** entre peticiones.
    *   El número de usuarios virtuales (threads) está parametrizado para recibirse dinámicamente.

*   **`.github/workflows/jmeter-test.yml`**: Es el flujo de automatización. Se encarga de preparar un entorno Linux, instalar Java y JMeter, ejecutar la prueba en modo "No-GUI" (desde consola) y recolectar los resultados.

## ⚙️ ¿Cómo ejecutar la prueba?

Gracias a la integración con GitHub Actions, puedes ejecutar esta prueba con diferentes cargas de usuarios sin necesidad de tener JMeter instalado en tu computadora:

1. Ve a la pestaña **[Actions](../../actions)** de este repositorio.
2. En la barra lateral izquierda, selecciona el flujo de trabajo **"JMeter Performance Test"**.
3. Haz clic en el botón gris que dice **"Run workflow"** a la derecha.
4. Aparecerá un campo solicitando el **"Número de usuarios virtuales (threads)"**. (El valor por defecto es 10).
5. Escribe el número deseado y presiona el botón verde **"Run workflow"**.

La prueba tomará poco más de 1 minuto en ejecutarse.

## 📊 ¿Cómo ver los resultados?

Una vez que la prueba finalice (aparecerá un ícono verde de éxito), haz clic sobre esa ejecución. Desplázate hacia la parte inferior de la página hasta la sección llamada **"Artifacts"**. 

Ahí podrás descargar dos archivos:
1. **`jmeter-html-report`**: Un archivo `.zip` que contiene un Dashboard HTML interactivo. Descomprímelo y abre el archivo `index.html` para ver gráficos, porcentajes de error y tiempos de respuesta.
2. **`jmeter-raw-results`**: Contiene el archivo crudo `resultados.jtl` (JMeter Test Log). Es el registro exacto de cada petición. Puedes usarlo para importarlo posteriormente en tu aplicación de escritorio de JMeter si deseas hacer análisis adicionales.
