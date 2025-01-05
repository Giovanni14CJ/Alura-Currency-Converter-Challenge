# Alura-Currency-Converter-Challenge

![Movimiento Browniano](src/BackGround.jpeg)

A continuación se muestra el Challenge propuesto por Alura para el curso de Programación Orientada a 
Objetos en Java, en el cual se desarrolla una aplicación que simula un conversor de divisas.

## Descripción del Challenge

Este proyecto es una aplicación de consola Java que permite convertir montos entre diferentes monedas utilizando las 
tasas de cambio en tiempo real provistas por la API de Exchange Rate. Debes ingresar al package `src` y ejecutar el
archivo `Principal.java` para iniciar la aplicación.

## Funcionalidades
- Conversión predefinida entre monedas populares:
   - Dólar (USD) a Peso Argentino (ARS).
   - Peso Argentino (ARS) a Dólar (USD).
   - Dólar (USD) a Real Brasileño (BRL).
   - Real Brasileño (BRL) a Dólar (USD).
   - Dólar (USD) a Peso Colombiano (COP).
   - Peso Colombiano (COP) a Dólar (USD).
- Conversión personalizada entre dos monedas proporcionadas por el usuario.
- Consultas a una API externa para recuperar tasas de conversión actualizadas.

## Clases principales

### 1. `Principal`
El punto de entrada de la aplicación. Muestra un menú interactivo al usuario y permite seleccionar entre diversas opciones de conversión.
Se conecta con las demás clases para realizar las conversiones.

### 2. `ConvertirMoneda`
Encargada de:
- Realizar la lógica de conversión utilizando tasas de cambio recuperadas desde `ConsultarMoneda`.
- Pedir datos al usuario (cantidad a convertir, códigos de moneda base y objetivo).
- Mostrar los resultados.

### 3. `ConsultarMoneda`
Se conecta con la API de Exchange Rate a través de solicitudes HTTP para obtener tasas de cambio actualizadas entre monedas.

### 4. `Monedas`
Modelo que representa los datos de las monedas, incluyendo:
- Código de la moneda base.
- Código de la moneda objetivo.
- Tasa de conversión.

## Cómo Funciona
1. El usuario selecciona una opción desde un menú interactivo.
2. Dependiendo de la opción seleccionada:
   - Se realiza una conversión automática predefinida.
   - O bien, se solicita al usuario ingresar los códigos de dos monedas para realizar una conversión personalizada.
3. `ConsultarMoneda` recoge la tasa de conversión actual desde la API y la pasa al proceso de cálculo.
4. El resultado se muestra en pantalla.

## Requisitos
- **Java 22** o superior.
- Conexión a internet (para obtener las tasas de cambio).

## Configuración
1. Clona este repositorio:
   ```bash
   git clone <https://github.com/Giovanni14CJ/Alura-Currency-Converter-Challenge.git>
   ```
2. Asegúrate de tener configurada la variable de entorno `JAVA_HOME` con un JDK compatible (Java 22+).

## Personalización
Este proyecto utiliza la API pública de `ExchangeRate-API`. Puedes cambiar la clave de API para personalizar las consultas.  
Edita el código de la clase `ConsultarMoneda` y reemplaza la clave actual:
```java
URI direccion = URI.create("https://v6.exchangerate-api.com/v6/{TU_CLAVE_API}/pair/" + monedaBase + "/" + monedaTarget);
```

## Créditos
Este proyecto utiliza las siguientes tecnologías:
- API de Exchange Rate para tasas de cambio.
- [Google Gson](https://github.com/google/gson) para serialización/deserialización de JSON.
- Java HTTP Client para manejo de peticiones HTTP.