# Modelación y simulación de las ventas diarias de una refaccionaria mediante MCMC

Tarea 2 de Simulación Estocástica. Maestría en Estadística Aplicada, Facultad de Ciencias Exactas, Universidad Juárez del Estado de Durango.

## Objetivo

Estimar la venta neta diaria esperada de la refaccionaria, su incertidumbre y la probabilidad de superar 50,000 MXN mediante Monte Carlo vía cadenas de Markov. El importe de 50,000 es ilustrativo del ejercicio.

## Datos y variable

La variable es el importe neto vendido por día, en pesos mexicanos, para días con movimientos registrados. Se utiliza la base de datos exportada desde una base depurada de SICAR con la exclusión acordada de 12 notas de crédito.

El archivo abarca del 25 de septiembre de 2021 al 25 de septiembre de 2026. El modelo se ajusta con los 310 días registrados de septiembre de 2025 a agosto de 2026. Se conservan los tres saldos negativos de ese periodo. Las 55 fechas sin registros se mantienen identificadas en la base de datos. La inferencia se refiere a días con movimientos.

Las 22 fechas observadas del 1 al 25 de septiembre de 2026 se reservan para evaluación temporal.

## Método

Se implementa Metropolis–Hastings multivariado para una regresión con errores Student de 5 grados de libertad. Incluye efectos de día de semana, tendencia lineal y un componente anual. La dispersión se estima por separado para lunes–viernes y sábados.

Se utilizan cuatro cadenas, 20,000 iteraciones por cadena y 4,000 iteraciones de calentamiento. Se conservan 64,000 estados. La semilla maestra es 42. El notebook presenta los parámetros iniciales, la selección de la propuesta, R-hat, ESS, MCSE, ACF, comprobación predictiva y validación con fechas posteriores.

## Archivos

| Archivo | Contenido |
|---|---|
| [Tarea_2_MCMC_Ventas_diarias.ipynb](Tarea_2_MCMC_Ventas_diarias.ipynb) | Notebook ejecutado y documentado, con los apartados 0–12, tablas y siete figuras interpretadas. |
| [Ventas_diarias_para_MCMC.csv](Ventas_diarias_para_MCMC.csv) | Fechas, ventas netas y número de movimientos. |
| README.md | Objetivo, método e instrucciones.|


## Alcance

Las cantidades monetarias son nominales y la simulación está condicionada al calendario de días registrados. El notebook documenta la amplitud de los intervalos, los límites del modelo simétrico Student y el desempeño frente a una referencia por día de semana.

