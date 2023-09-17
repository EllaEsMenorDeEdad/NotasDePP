# Guía para optimizar códigos de java según los criterios de Emilio

## Introducción

En esta guía está ordenado el paso a paso de cómo se tiene que resolver la parte de java del parcial. Se recomienda leerla completa antes de empezar a resolverlo.

## Procedimiento

### 1. Entender el código

Existe una herramienta de copilot que lee e interpreta el código. De igual forma, se recomienda leer el código manualmente.

### 2. Dar buenos nombres

Renombrar test, funciones y varibles para que tengan nombres descriptivos. No importa si son largos, importa que se entienda qué hace cada cosa. (Se recomienda usar camelCase y revisar las convenciones de qué cosas comienzan con mayúscula y cuáles no).

>Mayúscula: Clases, file names.\
>Minúscula: Funciones, variables, parámetros, atributos, tests.

### 3. Refactorizar constantes

Cambiar variables repetidas por constantes generales.

```java
private static final int cantidadDeDias = 7;
```

### 4. Inline functions

Cambiar funciones repetidas por una sola función general usando inline.

```java
private static int sumar(int num1, int num2) {
    return num1 + num2;
}
```

> Tanto los refactors como los inline se tienen que ubicar al final del código.

### 5. Reemplazar fors

Cambiar fors por .stream(). Tienen que ser funciones lambda.

```java
for (int i = 0; i < lista.size(); i++) {
    // ...
}
```

```java
lista.stream().forEach(elemento -> {
    // ...
});
```

>Dejar los ifs cómo están, no es requerimiento sacarlos.

### 6. Reemplazar Try and Cach

Cambiar try and cach por asserts equals y una función labda.

```java
try {
    assertEquals(1, 1);
} catch (Exception e) {
    e.printStackTrace();
}
```

```java
assertThrows(Exception.class, () -> {
    assertEquals(1, 1);
});
```

### 7. Implementar hash

Cuando hay un equals se tiene que implementar un hash. Esto hace que el equals sea más eficiente.

```java
@Override
public int hashCode() {
    return Objects.hash(nombre, apellido, edad);
}
```

## Ordenar el código

1. Imports
2. Atributos: públicos, privados
3. Constructores especializados
4. Constructores
5. Métodos: públicos, privados
6. Métodos auxiliares: inline y refactors
7. Getters y setters
