# TAREA-INDIVIDUAL
EJERCICIO 11

Algoritmo 1: Renumeración de horas extra - Solución de principio

Algoritmo **horas_extra**
* Establece la renumeración de "horas_ext" adicionales para un salario mensual bruto de "salario_mensual_bruto"

**Entrada**
    salario_mensual_bruto : **REAL**
        * Importe del salario mensual bruto
    horas_ext : **ENTERO**
        * Cantidad de horas extra del mes a pagar

**precondición**
    salario_mensual_bruto > 0
    horas_ext ≥ 0

**constante**
    CANTIDAD_SEMANAS : **ENTERO** - 52
        * Cantidad de semanas de trabajo 
    CANTIDAD_HORAS_SEMANA : **ENTERO** - 35
        * Cantidad legal de horas de trabajo semanales 
    CANTIDAD_HORAS_MAX_1 : **ENTERO** - 8
        * Umbral de cambio de precio de remuneración
    PRECIO_1 : **REAL** - 1,25
        * Tarifa de remuneración de CANTIDAD_HORAS_MAX_1 primeras horas extra
    PRECIO_2 : **REAL** - 1,50
        * Tarifa de remuneración de las otras horas extra

**variable**
    horas_ext_1 : **ENTERO**
        * Cantidad de horas extra con PRECIO_1 %
    horas_ext_2 : **ENTERO**
        * Cantidad de horas extra con PRECIO_2 %
    precio_hora : **REAL**
        * Precio hora de la remuneración bruta básica

**realización**
    calcular el precio_hora de la remuneración bruta básica

    **Resultado** - precio_hora x (inf(horas_ext, CANTIDAD_HORAS_MAX_1) x PRECIO_1 + sup(horas_ext – CANTIDAD_HORAS_MAX_1, 0) x PRECIO_2)

**postcondición**
...
**fin horas_extra**
