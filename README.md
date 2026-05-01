# 🎮 Taller Ahorcado en Java

Este repositorio contiene el desarrollo del juego **Ahorcado** en Java.

El proyecto permite practicar el uso de **cadenas de texto**, **arreglos**, **métodos**, lectura de archivos **CSV**, manejo de entradas por consola y organización del código en diferentes clases.

Las palabras del juego estarán organizadas por categorías y se cargarán desde el archivo `palabras.csv`.

---

## 👥 Integrantes del equipo

| Nombre | Usuario GitHub |
|---|---|---|
| Juan Jose Alzate Escudero | 
| Juan Pablo Velez Lopera |

> Cada integrante debe realizar commits propios dentro del repositorio.

---

## 📌 Nombre del repositorio

El repositorio debe llamarse:

```text
taller_ahorcado
```

---

## 📁 Arquitectura del proyecto

La estructura sugerida del proyecto es la siguiente:

```text
taller_ahorcado/
│
├── Main.java
├── Juego.java
├── CargadorCSV.java
├── ConsolaInput.java
├── Palabra.java
├── palabras.csv
└── README.md
```

---

## 🧩 Clases principales del proyecto

### `Main.java`

Es el punto de entrada del programa.

Se encarga de mostrar el menú principal y permitir que el usuario seleccione las opciones disponibles.

Funciones principales:

- Mostrar el menú principal.
- Permitir iniciar una partida.
- Mostrar instrucciones.
- Mostrar tabla de récords.
- Salir del programa.

---

### `Juego.java`

Contiene la lógica principal del juego.

Se encarga de controlar el desarrollo de la partida, los intentos, las letras ingresadas y el resultado final.

Funciones principales:

- Seleccionar una categoría.
- Elegir una palabra aleatoria.
- Mostrar el avance de la palabra.
- Validar letras ingresadas.
- Controlar errores.
- Determinar si el jugador gana o pierde.
- Permitir pedir pista con costo de un intento.

---

### `CargadorCSV.java`

Clase encargada de leer el archivo `palabras.csv`.

Esta clase usa:

- `BufferedReader`
- `FileReader`
- `String.split()`

Su función principal es cargar las palabras del archivo CSV y convertirlas en una lista de datos que pueda utilizar el juego.

---

### `ConsolaInput.java`

Clase de apoyo para leer datos ingresados por el usuario desde la consola.

Se utiliza para capturar información como:

- Nombre del jugador.
- Opciones del menú.
- Categoría seleccionada.
- Letras ingresadas durante la partida.

---

### `Palabra.java`

Clase que representa cada palabra del juego.

Cada objeto de esta clase debe tener:

- Categoría.
- Palabra.
- Pista.

Ejemplo:

```java
Palabra palabra = new Palabra("ANIMALES", "elefante", "mamífero grande de orejas grandes");
```

---

## 📄 Formato del archivo `palabras.csv`

El archivo `palabras.csv` debe tener el siguiente formato:

```csv
categoria,palabra,pista
ANIMALES,elefante,mamífero grande de orejas grandes
ANIMALES,leon,animal salvaje de la sabana
PAISES,colombia,país suramericano bañado por dos océanos
PAISES,guatemala,país centroamericano con volcanes
ANIMALES,nutria,animal acuático con cola larga
```

---

## 🗂️ Categorías obligatorias

El archivo CSV debe incluir mínimo **10 palabras por categoría**.

Categorías obligatorias:

- `ANIMALES`
- `TECNOLOGIA`
- `PAISES`
- `COLOMBIA`
- `PROGRAMACION`

En total, el archivo debe tener mínimo **50 palabras**.

También se pueden agregar más categorías para hacer el juego más interesante.

---

## 🔄 Flujo del juego

El funcionamiento general del juego es el siguiente:

1. El usuario inicia el programa.
2. El programa pide el nombre del jugador.
3. Se muestra el menú principal.
4. El usuario selecciona la opción **Jugar**.
5. El programa muestra las categorías disponibles.
6. El usuario selecciona una categoría.
7. El sistema escoge una palabra aleatoria de esa categoría.
8. La palabra se muestra con guiones bajos.
9. El usuario ingresa una letra por turno.
10. Si la letra es correcta, se revelan sus posiciones.
11. Si la letra es incorrecta, se suma un error.
12. El usuario puede pedir una pista, pero pierde un intento.
13. El juego termina cuando:
    - El usuario completa la palabra.
    - El usuario acumula 6 errores.

---

## 🕹️ Menú principal

El programa debe mostrar un menú similar al siguiente:

```text
===== JUEGO DEL AHORCADO =====

1. Jugar
2. Ver instrucciones
3. Tabla de récords
4. Salir

Seleccione una opción:
```

El menú debe ejecutarse dentro de un ciclo `do-while`, para que el usuario pueda volver al menú después de jugar o consultar instrucciones.

---

## ⚙️ Métodos requeridos

El proyecto debe separar la lógica en métodos con nombres claros y descriptivos.

Algunos métodos sugeridos son:

### `mostrarAhorcado(int errores)`

```java
mostrarAhorcado(int errores)
```

Este método muestra el estado visual del juego de acuerdo con la cantidad de errores cometidos por el jugador.

---

### `mostrarPalabra(char[] estado)`

```java
mostrarPalabra(char[] estado)
```

Este método imprime las letras descubiertas y los guiones bajos de las letras que aún no han sido adivinadas.

Ejemplo:

```text
_ e _ _ _ _ o
```

---

### `validarLetra(char letra, String palabra, char[] estado)`

```java
validarLetra(char letra, String palabra, char[] estado)
```

Este método verifica si la letra ingresada por el usuario está dentro de la palabra secreta.

Debe retornar un valor `boolean`:

- `true` si la letra existe en la palabra.
- `false` si la letra no existe en la palabra.

---

### `seleccionarPalabraAleatoria(String[] lista, int categoria)`

```java
seleccionarPalabraAleatoria(String[] lista, int categoria)
```

Este método selecciona una palabra aleatoria de la categoría escogida por el usuario.

Para esto se puede usar `Math.random()`.

---

### `estaCompleta(char[] estado)`

```java
estaCompleta(char[] estado)
```

Este método verifica si el jugador ya completó toda la palabra.

Debe retornar:

- `true` si la palabra ya está completa.
- `false` si todavía faltan letras por descubrir.

---

### `verificarEasterEgg(String nombre)`

```java
verificarEasterEgg(String nombre)
```

Este método verifica si el nombre ingresado por el jugador activa el modo secreto del juego.

Debe retornar un valor `boolean`.

---

## 📌 Lectura del CSV en Java

Ejemplo base para leer el archivo `palabras.csv`:

```java
try {
    BufferedReader br = new BufferedReader(new FileReader("palabras.csv"));
    String linea = br.readLine(); // Saltar encabezado

    while ((linea = br.readLine()) != null) {
        String[] partes = linea.split(",");

        String categoria = partes[0];
        String palabra = partes[1];
        String pista = partes[2];

        // Aquí se puede agregar la palabra a una lista
    }

    br.close();

} catch (IOException e) {
    System.out.println("Error al leer el archivo CSV.");
}
```

Es importante manejar la excepción `IOException` usando `try-catch`, para evitar que el programa se cierre si el archivo no se encuentra o no puede leerse.

---

## 🧠 Uso de Strings y funciones

Durante el desarrollo del taller se aplican conceptos importantes de Java.

---

### ¿Qué es un `String`?

Un `String` es una cadena de texto.

Se utiliza para guardar datos como:

- Nombre del jugador.
- Categorías.
- Palabras.
- Pistas.
- Mensajes del juego.

Ejemplo:

```java
String palabra = "elefante";
```

---

### Diferencia entre `String` y `char[]`

Un `String` representa una cadena completa de texto.

Un `char[]` es un arreglo de caracteres individuales.

Ejemplo de `char[]`:

```java
char[] estado = {'_', '_', '_', '_', '_', '_', '_', '_'};
```

En el juego, el `char[]` puede usarse para mostrar el avance de la palabra.

---

## 🔤 Métodos de `String` usados

| Método | Función |
|---|---|
| `split()` | Divide una cadena en partes |
| `toLowerCase()` | Convierte el texto a minúsculas |
| `charAt()` | Obtiene un carácter en una posición |
| `length()` | Devuelve la cantidad de caracteres |

---

### Ejemplo de `split()`

```java
String linea = "ANIMALES,elefante,mamífero grande";
String[] partes = linea.split(",");

System.out.println(partes[0]); // ANIMALES
System.out.println(partes[1]); // elefante
System.out.println(partes[2]); // mamífero grande
```

---

### Ejemplo de `toLowerCase()`

```java
String texto = "ELEFANTE";
String resultado = texto.toLowerCase();

System.out.println(resultado); // elefante
```

---

### Ejemplo de `charAt()`

```java
String palabra = "leon";
char letra = palabra.charAt(0);

System.out.println(letra); // l
```

---

### Ejemplo de `length()`

```java
String palabra = "colombia";
int cantidad = palabra.length();

System.out.println(cantidad); // 8
```

---

## 🎲 Uso de `Math.random()`

Para seleccionar una palabra aleatoria se puede usar:

```java
int indice = (int)(Math.random() * lista.size());
```

Esto permite seleccionar una posición al azar dentro de la lista de palabras disponibles.

---

## 🧪 Ejemplo de selección aleatoria

```java
ArrayList<String> palabras = new ArrayList<>();

palabras.add("elefante");
palabras.add("leon");
palabras.add("nutria");

int indice = (int)(Math.random() * palabras.size());

String palabraSeleccionada = palabras.get(indice);

System.out.println(palabraSeleccionada);
```

---

## 🎯 Lógica del juego

La lógica del juego se basa en comparar cada letra ingresada con las letras de la palabra secreta.

Ejemplo:

```java
public boolean validarLetra(char letra, String palabra, char[] estado) {
    boolean acierto = false;

    for (int i = 0; i < palabra.length(); i++) {
        if (palabra.charAt(i) == letra) {
            estado[i] = letra;
            acierto = true;
        }
    }

    return acierto;
}
```

---

## ✅ Verificar si la palabra está completa

```java
public boolean estaCompleta(char[] estado) {
    for (int i = 0; i < estado.length; i++) {
        if (estado[i] == '_') {
            return false;
        }
    }

    return true;
}
```

---

## 🖥️ Mostrar la palabra en pantalla

```java
public void mostrarPalabra(char[] estado) {
    for (int i = 0; i < estado.length; i++) {
        System.out.print(estado[i] + " ");
    }

    System.out.println();
}
```

---

## 🎨 Colores ANSI

Se pueden usar colores ANSI en consola para diferenciar mensajes importantes.

Ejemplo:

```java
public static final String VERDE = "\u001B[32m";
public static final String ROJO = "\u001B[31m";
public static final String RESET = "\u001B[0m";
```

Ejemplo de uso:

```java
System.out.println(VERDE + "¡Ganaste!" + RESET);
System.out.println(ROJO + "Perdiste la partida." + RESET);
```

---

## 🥚 Bonus: Easter Egg

El juego incluye un bonus llamado **Modo Dios**.

Al iniciar la partida, el programa pide el nombre del jugador.

Si el nombre ingresado es exactamente:

```text
XACARANA
```

Se activa un modo especial.

Este modo puede incluir:

- Un mensaje especial de celebración.
- Una categoría oculta llamada `SECRETOS`.
- Palabras geek.
- La primera letra de la palabra revelada automáticamente.

---

## 🔐 Categoría secreta

La categoría secreta puede llamarse:

```text
SECRETOS
```

Ejemplos de palabras para esta categoría:

```text
DARTHVADER
KONAMI
MATRIX
TARDIS
ZELDA
```

---

## 🧩 Método del Easter Egg

```java
public boolean verificarEasterEgg(String nombre) {
    return nombre.equals("XACARANA");
}
```

También se puede usar:

```java
public boolean verificarEasterEgg(String nombre) {
    return nombre.equalsIgnoreCase("XACARANA");
}
```

La diferencia es que `equalsIgnoreCase()` no tiene en cuenta mayúsculas o minúsculas.

---

## 🏆 Tabla de récords

El programa puede incluir una tabla de récords donde se guarden los mejores resultados de los jugadores.

Datos sugeridos:

| Jugador | Categoría | Palabra | Resultado | Errores |
|---|---|---|---|---|
| Ana | ANIMALES | elefante | Ganó | 2 |
| Luis | PAISES | colombia | Ganó | 1 |
| María | TECNOLOGIA | teclado | Perdió | 6 |

---

## ▶️ Cómo ejecutar el proyecto

### 1. Clonar el repositorio

```bash
git clone https://github.com/usuario/taller_ahorcado.git
```

---

### 2. Entrar a la carpeta del proyecto

```bash
cd taller_ahorcado
```

---

### 3. Compilar los archivos Java

```bash
javac *.java
```

---

### 4. Ejecutar el programa

```bash
java Main
```

---

## 💡 Ejemplo de partida

```text
Ingrese su nombre:
Carlos

===== JUEGO DEL AHORCADO =====

1. Jugar
2. Ver instrucciones
3. Tabla de récords
4. Salir

Seleccione una opción:
1

Seleccione una categoría:

1. ANIMALES
2. TECNOLOGIA
3. PAISES
4. COLOMBIA
5. PROGRAMACION

Categoría seleccionada: ANIMALES

Palabra:
_ _ _ _ _ _ _ _

Ingrese una letra:
e

Correcto.

Palabra:
e _ e _ _ _ _ e
```

---

## 📚 Preguntas teóricas del taller

Al finalizar el taller se deben poder responder las siguientes preguntas:

1. ¿Qué es un `String` en Java y cómo se diferencia de un `char[]`?
2. ¿Qué métodos de `String` se usaron en el taller?
3. ¿Para qué sirven `split()`, `toLowerCase()`, `charAt()` y `length()`?
4. ¿Qué es un método en Java?
5. ¿Cuál es la diferencia entre un método `void` y uno con tipo de retorno?
6. ¿Qué es el paso por valor en Java?
7. ¿Cómo afecta el paso por valor a los arreglos?
8. ¿Qué es `StringBuilder`?
9. ¿Cómo se diferencia `StringBuilder` de un arreglo normal?
10. ¿Qué es la sobrecarga de métodos?
11. ¿Cómo funciona `Math.random()`?
12. ¿Qué es un archivo CSV?
13. ¿Por qué es útil usar CSV en lugar de datos hardcodeados?

---

## ✍️ Respuestas teóricas breves

### 1. ¿Qué es un `String`?

Un `String` es una cadena de texto utilizada para almacenar palabras, frases o mensajes.

---

### 2. ¿Qué es un `char[]`?

Un `char[]` es un arreglo de caracteres.  
Cada posición almacena una sola letra.

---

### 3. Diferencia entre `String` y `char[]`

Un `String` guarda texto completo.  
Un `char[]` permite modificar cada carácter por separado.

---

### 4. ¿Qué es un método?

Un método es un bloque de código que realiza una tarea específica.

---

### 5. Diferencia entre método `void` y método con retorno

Un método `void` ejecuta una acción pero no devuelve ningún valor.

Un método con retorno devuelve un resultado, como `int`, `boolean`, `String`, entre otros.

---

### 6. ¿Qué es el paso por valor en Java?

El paso por valor significa que Java envía una copia del valor a los métodos.

En el caso de objetos y arreglos, se copia la referencia, por eso se pueden modificar sus datos internos.

---

### 7. ¿Qué es `StringBuilder`?

`StringBuilder` es una clase que permite construir y modificar cadenas de texto de forma eficiente.

---

### 8. ¿Qué es la sobrecarga de métodos?

La sobrecarga ocurre cuando existen varios métodos con el mismo nombre, pero con diferentes parámetros.

Ejemplo:

```java
public void mostrarMensaje(String mensaje) {
    System.out.println(mensaje);
}

public void mostrarMensaje(String mensaje, int veces) {
    for (int i = 0; i < veces; i++) {
        System.out.println(mensaje);
    }
}
```

---

### 9. ¿Qué es un archivo CSV?

Un archivo CSV es un archivo de texto donde los datos están separados por comas.

Ejemplo:

```csv
categoria,palabra,pista
ANIMALES,leon,animal salvaje
```

---

### 10. ¿Por qué usar CSV?

Usar CSV permite agregar, quitar o modificar palabras sin cambiar directamente el código Java.

Esto hace que el programa sea más organizado y fácil de mantener.

---

## ✅ Requisitos del taller

El proyecto debe cumplir con los siguientes requisitos:

- Crear un repositorio en GitHub llamado `taller_ahorcado`.
- Trabajar en grupo de 2 o 3 personas.
- Actualizar el archivo `README.md`.
- Cada integrante debe tener commits propios.
- Separar responsabilidades en diferentes clases.
- Crear la clase `Main.java`.
- Crear la clase `Juego.java`.
- Crear la clase `CargadorCSV.java`.
- Crear la clase `ConsolaInput.java`.
- Crear la clase `Palabra.java`.
- Crear el archivo `palabras.csv`.
- Leer las palabras desde el CSV.
- Incluir mínimo 5 categorías.
- Incluir mínimo 10 palabras por categoría.
- Implementar menú principal.
- Implementar selección de categoría.
- Implementar selección de palabra aleatoria.
- Validar entradas inválidas.
- Usar métodos con nombres descriptivos.
- Implementar la opción de pedir pista.
- Manejar errores con `try-catch`.
- Usar colores ANSI en consola.
- Implementar el Easter Egg.
- Mostrar resultado de victoria o derrota.
- Agregar tabla de récords.

---

## 🧾 Conclusión

Este proyecto permite aplicar conceptos fundamentales de programación en Java mediante la creación de un juego interactivo.

Durante el desarrollo se practican temas como:

- Uso de `String`.
- Uso de `char[]`.
- Métodos.
- Arreglos.
- Lectura de archivos CSV.
- Manejo de excepciones.
- Organización del código por clases.
- Uso de ciclos y condicionales.
- Validación de entradas.
- Trabajo colaborativo con GitHub.

El objetivo principal es construir un programa funcional, organizado y fácil de mantener.
