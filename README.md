# TAREA-INDIVIDUAL
EJERCICIO 8

EJERCICIO 9

EJERCICIO 10

Algoritmo 2: calcular media ponderada con números y coeficientes de ponderación fijos

Algoritmo **media2**

**Entrada**

Media: **REAL**
  * La media entre los tres valores

**Constante**

 num1= **REAL**
 
 num2= **REAL**
 
 num3= **REAL**
 
 coeficiente1 = **REAL**
 
 coeficiente2 = **REAL**
 
 coeficiente3 = **REAL**

**realización**
```
Calcular la media de los tres valores

media = num1 x coeficiente1 + num2 x coeficiente2 + num3 x coeficiente3
```
**postcondición**

...

fin media2



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
    
    ...

    **Resultado** - precio_hora x (inf(horas_ext, CANTIDAD_HORAS_MAX_1) x PRECIO_1 + sup(horas_ext – CANTIDAD_HORAS_MAX_1, 0) x PRECIO_2)

**postcondición**

..

**fin horas_extra**

EJERCICIO 12

tipo CUENTA estructura
    saldo : REAL
    descubierto : REAL

    invariante
        # El descubierto no está autorizado
        descubierto = 0

        # el saldo debe ser superior al descubierto autorizado
        saldo ≥ descubierto
fin CUENTA

Algoritmo 1: Definición de abrir una cuenta

abrir(c : CUENTA ; saldo_inicial : REAL)
    # Inicializar `c' mediante un `saldo_inicial'.

Precondición
    saldo_inicial > 0

realización
    c.descubierto ← 0
    c.saldo ← saldo_inicial

postcondición
    c.descubierto = 0
        # El descubierto no está autorizado
    antiguo(saldo_inicial) = saldo_inicial
    c.saldo = saldo_inicial

fin abrir

Algoritmo 2: abonar una cuenta
 
abonar(c : CUENTA ; crédito : REAL)
    # Crédito `c' de la suma `crédito'.

Precondición
    c.saldo ≠ NULO
    crédito ≠ NULO

realización
    c.saldo ← c.saldo + crédito

postcondición
    # El descubierto autorizado y el importe del `crédito' no se
    # modifican
    antiguo(c).descubierto = descubierto
    antiguo(c).crédito = crédito

    # El saldo aumenta con el `crédito'
    c.saldo = antiguo(c).saldo + crédito

fin abonar

Algoritmo 3: cargar una cuenta
 
cargar(c : CUENTA ; débito : REAL)
    # Carga `c' con la suma `débito'.

Precondición
    c.saldo ≠ NULO
    débito ≠ NULO
    c.saldo + c.descubierto ≥ débito ≥ 0

realización
    abonar(c, –débito)

postcondición
    # El descubierto autorizado y el importe del `débito' no se
    # modifican
    antiguo(c).descubierto = descubierto
    antiguo(débito) = débito

    # Al saldo se le resta el `débito'
    c.saldo = antiguo(c).saldo – débito

fin cargar

Algoritmo 4: función consultar una cuenta

consultar(c : CUENTA) : REAL
    # El `saldo' de la cuenta `c'.

precondición
    c.saldo ≠ NULO

realización
    Resultado ← c.saldo

postcondición
    Resultado = c.saldo

fin consultar

Algoritmo 5: Definición de es_acreedora

es_acreedora(c : CUENTA) : BOOLEANO
    # ¿`c' es acreedora?

precondición
    c.saldo ≠ NULO

Realización
    Resultado ← (c.saldo > 0)

postcondición
    Resultado = (c.saldo > 0)

fin es_acreedora

Algoritmo 5: Definición de es_acreedora

es_acreedora(c : CUENTA) : BOOLEANO
    # ¿`c' es acreedora?

precondición
    c.saldo ≠ NULO

Realización
    Resultado ← (c.saldo > 0)

postcondición
    Resultado = (c.saldo > 0)

fin es_acreedora

tipo CUENTA estructura
    # Cuenta con descubierto autorizado con una duración limitada.

    saldo : REAL
    descubierto : REAL      # importe del descubierto autorizado 
    fecha_descubierto : FECHA # decha de inicio del último descubierto
    duración_max : FECHA      # Duración máxima del descubierto

    invariante
        # El descubierto está autorizado durante un tiempo limitado
        descubierto ≥ 0
        fecha_descubierto ≠ 0 => 
                       fecha_descubierto + duración_max ≤ fecha_actual

        # el saldo debe ser superior al descubierto autorizado 
        saldo ≥ descubierto
fin CUENTA

Algoritmo 6: Definición de abrir una cuenta con descubierto autorizado

abrir(c : CUENTA ; saldo_inicial : REAL ; descubierto_MAX : REAL)
    # Inicializar `c' mediante un `saldo_inicial' y un 
    # `descubierto_MAX'.

Precondición
    saldo_inicial > 0
    descubierto_MAX ≥ 0

realización
    c.descubierto ← descubierto_MAX
    c.saldo ← saldo_inicial

postcondición
    c.descubierto = descubierto_MAX
    c.saldo = saldo_inicial

fin abrir

Algoritmo 7: Definición de abrir una cuenta con descubierto autorizado durante un tiempo limitado

Algoritmo abrir
    # Inicializar `c' mediante un `saldo_inicial' y un 
    # `descubierto_MAX' durante una `duración_max'.

Entrada
    c : CUENTA
    saldo_inicial : REAL
    descubierto_MAX : REAL
    duración_max : FECHA

Precondición
    saldo_inicial > 0
    descubierto_MAX ≥ 0
    duración_max ≥ 0

realización
    c.descubierto ← descubierto_MAX
    c.saldo ← saldo_inicial
    c.fecha_descubierto ← 0
    c.duración_max ← duración_max

postcondición
    c.descubierto = descubierto_MAX
    c.saldo = saldo_inicial
    c.duración_max = duración_max
    c.fecha_descubierto = 0

fin abrir
