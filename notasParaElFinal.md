# Notas para el final de Paradigmas de la programación

## con Emilio Oca

## Paso 1

### Entender la consigna

Este paso consiste en comprender la herramienta que se está por hacer y qué es lo que realmente pide. Estas cosas que nos pide las vamos a anotar en un block de notas para armarnos una checklist.

>Importante: Darse cuenta que es lo que NO nos pide la consigna para no atrasarse en nada inútil.

__Ejemplo:__

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

__En este ejemplo podríamos hacer esta checklist:__

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

__Ejemplo:__

Investigamos que en la consigna nos ofrecen las librerías `java.time.LocalDate` y `java.time.DayOfWeek`. En estas ya existen las clases fecha y día de la semana, por lo que no tenemos que hacerlas nosotros.

- [ ] Registrar feriados puntuales
- [ ] Registrar feriados semanales
- [ ] Registrar periodos de feriados
- [ ] Consultar si un día es feriado
- [x] Clase fecha (`java.time.LocalDate`)
- [x] Clase día de la semana (`java.time.DayOfWeek`)
- [ ] Clase período

## Paso 3

### Hacemos TDD

Dentro de nuestra checklist Buscamos la cosa más básica que debe de estar implementada y cuando la tengamos, tenemos que pensar en que es lo más básico que debería de hacer (o que nó debería de hacer). Con eso hacemos el primer test.

__Ejemplo:__

En este caso, lo más básico que debería de hacer es registrar feriados puntuales. Entonces hacemos el primer test.

```java
@Test
public void test00registrarFeriadoPuntual() {
    Agenda agenda = new Agenda();
    agenda.registrarFeriado(LocalDate.of(2021, 5, 25));
    assertTrue(agenda.esFeriado(LocalDate.of(2021, 5, 25)));
}
```

## Paso 4

### Hardcodeamos la respuesta

Aquí tenemos que hacer que el test pase de la forma más rápida posible. Para eso, hardcodeamos la respuesta. También podemos comenzar a hacer una estructura mínima de nuestro código para montar la base de los siguientes testst.

__Ejemplo:__

```java
public class Agenda {
    public void registrarFeriado(LocalDate fecha) {
    }

    public boolean esFeriado(LocalDate fecha) {
        return true;
    }
}
```

- [x] Registrar feriados puntuales
- [ ] Registrar feriados semanales
- [ ] Registrar periodos de feriados
- [ ] Consultar si un día es feriado
- [x] Clase fecha (`java.time.LocalDate`)
- [x] Clase día de la semana (`java.time.DayOfWeek`)
- [ ] Clase período

## Paso 5

### Volvemos al paso 3

Ahora que tenemos un test que pasa, volvemos al paso 3 y buscamos la siguiente cosa más básica que debería de hacer. Si a la hora de tratar de hacer que pase nuestro test rompemos el anterior, entonces buscamos una forma menos harcodeada de hacerlo.

__Ejemplo:__

En este caso, lo siguiente más básico que debería de hacer es registrar feriados semanales. Entonces hacemos el segundo test.

```java
@Test
public void test01registrarFeriadoSemanal() {
    Agenda agenda = new Agenda();
    agenda.registrarFeriado(DayOfWeek.SUNDAY);
    assertTrue(agenda.esFeriado(LocalDate.of(2021, 5, 30)));
}
```

```java
public class Agenda {
    private List<LocalDate> feriadosPuntuales = new ArrayList<>();
    private List<DayOfWeek> feriadosSemanales = new ArrayList<>();

    public void registrarFeriado(LocalDate fecha) {
        feriadosPuntuales.add(fecha);
    }

    public void registrarFeriado(DayOfWeek dia) {
        feriadosSemanales.add(dia);
    }

    public boolean esFeriado(LocalDate fecha) {
        return feriadosPuntuales.contains(fecha) || feriadosSemanales.contains(fecha.getDayOfWeek());
    }
}
```

- [x] Registrar feriados puntuales
- [x] Registrar feriados semanales
- [ ] Registrar periodos de feriados
- [ ] Consultar si un día es feriado
- [x] Clase fecha (`java.time.LocalDate`)
- [x] Clase día de la semana (`java.time.DayOfWeek`)
- [ ] Clase período

>Comentario: de esta forma vamos complejizando nuestro código de a poco. Siempre buscando la forma más simple de hacerlo.

## Paso 6

### Refactorizamos nuestro código y nuestros test

Para esto hice anteriormente para el parcial el paso a paso de cómo refactorizar nuestro código y nuestros test. Lo pueden encontrar en el archivo [`notasParaElParcial.md`](https://github.com/EllaEsMenorDeEdad/NotasDePP/blob/main/notasParaElParcial.md).
