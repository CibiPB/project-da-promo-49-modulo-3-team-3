# Proyecto de Análisis de Datos para ABC Corporation:
## Resumen:
En el entorno empresarial altamente competitivo de hoy en día, la toma de decisiones informadas es esencial para el éxito a largo plazo. La retención de empleados y la satisfacción en el trabajo son cuestiones críticas para cualquier organización, ya que afectan directamente a la productividady la rentabilidad de la empresa.
Con el objetivo de reducir la rotación de empleados y mejorar la satisfacción en el trabajo, la empresa ABC Corporation nos ha contratado para desarrollar un proyecto de análisis de datos. Nuestra misión es identificar factores clave que influyen en la satisfacción en el trabajo y, en última instancia, en la retención de empleados.
En este proyecto, presentaremos los resultados de nuestro análisis exploratorio de datos y analizaremos los resultados para proporcionar a ABC Corporation información valiosa que informe sus decisiones estratégicas.
## Fases del Proyecto:
### Fase 1: Análisis Exploratorio de Datos (EDA):
Antes de llevar a cabo el proyecto, es crucial comprender mejor el conjunto de datos y sus características. Para ello, se hace un análisis exploratorio detallado del conjunto de datos y entender qué información tenemos.
### Fase 2: Transformación de los Datos:
Esto incluiye la limpieza de datos, la conversión de tipos de datos y la aplicación de reglas empresariales específicas. Las transformaciones se realizarán mediante funciones de Python que se aplicarán a los datos extraídos. Algunas de las transformaciones que se han hecho son:
*   La columna 'Gender' tiene valores de 0 y 1, los cuales son poco intuitivos, por lo que se han reemplazado por "Male" y "Female", o "M" y "F".
*   Algunas columnas, como la columna 'DailyRate' son columnas que incluyen valores numéricos decimales. Pero en el DataFrame aparece como columna de tipo string. Por lo que se han realizado los cambios necesarios para convertirla en columna de tipo numérica.
*   Hemos evaluado si hay valores duplicados y analizado si tiene sentido eliminarlos o mantenerlos.
*   En cuanto a los valores inconsistentes podemos destacar la columna 'DistanceFromHome' ya que tiene valores negativos.
*   Asimismo, nos hemos encontrado con errores tipográficos en algunos valores de las columnas categóricas. Por ejemplo, en la columna 'MaritalStatus' ya que en vez de "Married" en algunas filas aparece "Marreid".
*   Y por último, había columnas redundantes, es decir, columnas que nos dan la misma información expresada de forma diferente.
### Fase 3: Visualizando los Datos:
  Se generan gráficos para explorar relaciones entre diversas variables, así como ayudar a resaltar tendencias, áreas de mejora y fortalezas dentro de la empresa.:
    *   **Boxplots:** Relación entre salario anual y género, así como entre horas estándar y salario anual por departamento.
    *   **Histogramas:** Distribución del salario anual según horas estándar por departamento.
    *   **Barplots:** Correlación entre años totales trabajados, nivel de trabajo y escala salarial.
    *   **Countplots:** Distribución del departamento según satisfacción de los empleados que viven lejos.
## Conclusión:
Este proyecto proporciona una visión detallada sobre los datos de recursos humanos, ayudando a identificar áreas clave para mejorar la gestión organizacional. Las visualizaciones generadas permiten una comprensión clara de los patrones internos y pueden ser utilizadas como base para tomar decisiones estratégicas.
