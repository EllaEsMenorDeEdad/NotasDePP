# Notas para el final de Paradigmas de la programación

## con Emilio Oca

## Paso 1

### Entender la consigna

Este paso consiste en comprender la herramienta que se está por hacer y qué es lo que realmente pide. Estas cosas que nos pide las vamos a anotar en un block de notas para armarnos una checklist.

>Importante: Darse cuenta que es lo que NO nos pide la consigna para no atrasarse en nada inútil.

## Ejemplo

Se busca construir una agenda que permita registrar feriados y consultar si un día es
feriado.
Debe poder registrarse:

- feriados puntuales, por ejemplo 25 de mayo de 2023.
- feriados semanales, por ejemplo, los Domingos.
- periodos de feriados, por ejemplo, del 2 al 29 de enero de 2024
La agenda debe poder responder,
- es feriado, por ejemplo, es feriado el 25 de mayo de 2023
Debe realizarse mediante TDD en forma iterativa incremental.
Aplicando todos los criterios vistos en clase hasta ahora.
Hint:
Considere java.time.LocalDate para las fechas y java.time.DayOfWeek para los días de
la semana. Son modelos de fechas y días ya incluidos en las librerías de Java,
precarios pero funcionales y útiles para el parcial.

### En este ejemplo podríamos hacer esta checklist:

- [ ] Registrar feriados puntuales
- [ ] Registrar feriados semanales
- [ ] Registrar periodos de feriados
- [ ] Consultar si un día es feriado
- [ ] Clase fecha
- [ ] Clase día de la semana
- [ ] Clase período

>Comentario: NO pide que hagamos una función para remover feriados. Entonces no malgastamos nuestro tiempo en hacerlo. Puede que parezca lógico tenerlo, pero acá no aprobamos por pensar, aprobamos por seguir ordenes (cómo los milicos)

## Paso 2

### Investigar librerías

En el caso de que en la consigna nos ofrezcan usar alguna o varias librerías, investigar que hacen y cómo podríamos usarlas para facilitar nuestro código. Tenemos que estar revisando nuestra checklist para ver si alguna función ya está hecha por la librería

### Ejemplo

Investigamos que en la consigna nos ofrecen las librerías `java.time.LocalDate` y `java.time.DayOfWeek`. En estas ya existen las clases fecha y día de la semana, por lo que no tenemos que hacerlas nosotros.

- [ ] Registrar feriados puntuales
- [ ] Registrar feriados semanales
- [ ] Registrar periodos de feriados
- [ ] Consultar si un día es feriado
- [x] Clase fecha
- [x] Clase día de la semana
- [ ] Clase período

## Paso 3

### Hacemos TDD

Dentro de nuestra checklist tenemos que darnnos cuenta de qué es lo más básico que debe hacer (o que no debería hacer)