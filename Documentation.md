# Proyecto ABC: grado de satisfacción de sus empleados. `Documentación`.

## 1. Contexto:

La empresa ABC Corporation nos ha encargado desarrollar un proyecto de análisis de datos para conocer el grado de satisfacción de sus empleados. Para ello nos ha proporcionado una base de datos con información sobre sus empleados como departamento al que pertenecen, puesto, salario, años en la empresa y nivel educativo, entre otras.

## 2. Análisis exploratorio de los datos:

Hemos comenzado el proyecto realizando un EDA para conocer los datos y la relación entre ellos y poder hacer una limpieza que nos permita tener una visualización más limpia y fácil de manejar. 

### 2.1. Eliminación de columnas:
Tras una primera exploración encontramos algunas columnas que no nos aportan información relevante para el objetivo de nuestro análisis, por lo que tomamos la decisión de eliminarlas con el fin de tener datos con información clave para el estudio:

- `numberchildren`: la eliminamos porque tiene un 100% de nulos.

- `sameasmonthlyIncome`: la eliminamos porque es igual que monthly income.

- `employeecount`: valor constante de 1. No aporta información.

- `HourlyRate`: eliminamos porque la información es redundante. Ya tenemos  `daylyrate` , `MonthlyRate` y `salary` que son columnas proporcionales que reportan exactamente la misma información pero manifestada en una medida temporal diferente.

- `Over18`: redundante. Todos son `yes` o nulos.

- `YearsInCurrentRole`: 97% de nulos.

- `RoleDepartament`: Comprobamos que esta columna era resultado de la unión de dos columnas ya existentes (`job title` y `department`)

### 2.2. Renombrado de columnas:

 Hemos renombrado las columnas para unificar el formato y darles un nombre más intuitivo en función del dato que contienen. 

### 2.3. Eliminación de duplicados:

Asimismo, encontramos filas con información duplicada basándonos en el employee_number, que es la primary key de la tabla, hemos eliminado la duplicidad quedándonos con el primer dato introducido. 


### 2.4. Creación de categorías:

También hemos asignado categorías a las columnas para poder filtrar por su tipo  de información. Las categorías han sido las siguientes:

- `personal` : 'employee_number',  'gender', 'birth_year',  'age', 'marital_status', 'dist_home'

- `job`: 'job_title','department', 'departured','year_at_comp', 'standard_hours', 'remote', 'business_travel', 'over_time',  'job_level',  'stock_opt_level', 'traning_times_last_year',  'perf_rate','year_last_promotion', 'year_current_mngr'.

- `education` =    'education_field', 'education_scale'

- `income` = 'annual_salary', 'monthly_income', 'daily_rate', 'perc_salary_hike'

- `satisfaction` =  'env_sat_rate', 'job_involvement', 'job_sat_rate',  'relationship_sat_rate',  'work_life_balance'

- `emp_bgd` (employee background) =   'num_comp_worked', 'tot_working_year'


## 3. Análisis y modificación de datos:

Tras realizar una primera limpieza general hemos comenzado con un análisis inicial de los datos para posteriormente analizarlos en profundidad por las categorías que hemos formado.

Otro paso importante ha sido la realización y análisis de un Heatmap que nos ha permitido conocer el grado de correlación entre las diferentes variables, este gráfico tendrá relevancia para la gestión de nulos y el conocimiento de la correlación de veriables que nos pueda aportar una visión clara sobre el objetivo del estudio.

También hemos visualizado y comprendido la información estadística sobre las columnas por categorías: personal, trabajo, salario, educación, satisfacción y experiencia laboral. 


### 3.1. Modificaciones:

Comenzamos una limpieza en profundidad tomando decisiones basadas en el análisis previo de los datos: 

- Modificamos el formato de algunas columnas para que sea adecuado a la información que contienen, como `convertir a tipo numérico` columnas como 'employee_number','age' o 'education_scale'. Y a `tipo categórico` valores que tenían una escala como 'gender' y 'remote'.

- Modificamos errores tipográficos en la columna '`marital_status`': 'Marreid'.


- Cambiamos a positivos valores numéricos de la columna `'dist_home' `que estaban erróneos.

- En la columna '`department`' tratamos en un principio de rellenarlos con la columna '`RoleDepartment`' separando su información en dos, sin éxito ya que tenía exactamente los mismos nulos. 

- formato mayúsculas: algunas columnas como la de `job title`, tenía los datos escritos de la siguiente forma: [' resEArch DIREcToR ' ' ManAGeR ' ' ManaGER ' ... ' sAlES ExECUTivE ', ' SaLes ExecUtIVe ' ' mAnUfactURInG DiRECTOr ']. Corregimos el formato, poniendo todos los datos con la primera letra en mayúsculas y el resto en minúscula.

- `edad`: para esta columna, reemplazamos valores que estaban en formato string a objeto. Por ejemplo: `'thirty-two': 32`.

- `género`: para esta columna, reemplazamos los 0 por "M", y los 1, por "F".

- `remote`: para esta columna, hicimos lo mismo, los True y 1 fueron reemplazados por "yes" y los False y "0" por "No".

### 3.2. Imputación de nulos:

En el análisis general hemos observado la cantidad de nulos que tiene cada columna y analizado en profundidad estos datos para tomar las decisiones oportunas sobre su tratamiento.

Pasamos al tratamiento de los valores nulos, en este paso hemos tenido que analizar en profundidad la información de las columnas y su relación con otras para tomar decisiones sobre cómo gestionarlos.

- Para alguna columnas pudimos realizar una imputación de los datos con el `método KNNI`, como es el caso de la columna '`age`' que pudimos completar sus nulos con la columna '`birth_year`'. 


- De la misma manera que pudimos completar los datos nulos de `salario` con las columnas '`monthly_income'`, '`daily_rate`', '`annual_salary`', ya que todas tenían una relación directa entre sí.

- Cambio de los nulos por `unknown`:
    - Columna `department`: Tras analizar otras columnas para vimos que  podíamos completar esta columna con la columna de  `job role` de cada empleado, siempre que esta tuviera datos. Para ello hicimos el siguiente diccionario:
    
    ```python
        dict ={"Research & Development": ["Healthcare Representative", "Laboratory Technician", "Manufacturing Director", "Research Scientist", "Research Director"],
                        "Sales": ["Sales Executive", "Sales Representative"],
                        "Human Resources": ["Human Resources"],
                        "Unknown": ["Manager"]} #manager no tiene un departamento específico
    ```

    Para los empleados que fuera posible, completamos la columna de `department` con la columna de `jobrole`.  Para los que no era posible: aquellos cuyo role fuera `manager` y aquellas cuya columna de `jobrole` fuera nula,  tomamos la decisión de cambiarlo por '`unknown`'. 

    
    - Cambio de nulos por `unknown`: seguimos este mismo método para los nulos en '`marital_status`', '`business_travel`', '`over_time`' y '`education_field`'.

## 4. Creación de BBDD con conector:

Procedimos a la creacion de una base de datos para poder facilitársela a la empresa ABC.


## 5. Estudio sobre el grado de satisfacción de los empleados:

En este punto donde ya contamos con una base de datos limpia y completa y un profundo conocimiento de esta, procedemos a extraer información concluyente sobre nuestro objetivo: `el grado de satisfacción de los empleados.`

Para ello creamos una serie de hipótesis sobre qué variables pueden tener relación con el grado de satisfacción:

- Tiempo en la empresa, experiencia total, jornada completa o media jornada, el salario, la distancia del trabajo a casa


