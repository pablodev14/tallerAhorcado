# 🎮 Taller Ahorcado en Java

Proyecto desarrollado en Java para crear el juego del **Ahorcado**.  
El objetivo es practicar el uso de **Strings**, **arreglos**, **métodos**, lectura de archivos **CSV** y organización del código en clases.

Las palabras del juego se cargan desde un archivo `palabras.csv` y están organizadas por categorías.

---

## 👥 Integrantes

| Nombre | Usuario GitHub |

| Juan Jose Alzate Escudero | 
| Juan Pablo Velez Lopera | 

> Cada integrante debe realizar commits propios.

---

## 📁 Estructura del proyecto

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

## 🧩 Clases del proyecto

### `Main.java`

Punto de entrada del programa.  
Contiene el menú principal con las opciones:

- Jugar
- Ver instrucciones
- Tabla de récords
- Salir

---

### `Juego.java`

Contiene la lógica principal del juego.

Se encarga de:

- Seleccionar categoría.
- Elegir palabra aleatoria.
- Validar letras.
- Mostrar progreso de la palabra.
- Controlar errores.
- Determinar victoria o derrota.
- Permitir pedir pista.

---

### `CargadorCSV.java`

Lee el archivo `palabras.csv` usando `BufferedReader`, `FileReader` y `split()`.

Su función es cargar las palabras, categorías y pistas para usarlas en el juego.

---

### `ConsolaInput.java`

Clase de apoyo para leer datos del usuario desde consola.

---

### `Palabra.java`

Representa una palabra del juego.

Cada palabra contiene:

- Categoría
- Palabra
- Pista

---

## 📄 Formato del archivo CSV

El archivo `palabras.csv` debe tener este formato:

```csv
categoria,palabra,pista
ANIMALES,elefante,mamífero grande de orejas grandes
ANIMALES,leon,animal salvaje de la sabana
PAISES,colombia,país suramericano bañado por dos océanos
PAISES,guatemala,país centroamericano con volcanes
```

---

## 🗂️ Categorías obligatorias

El CSV debe tener mínimo **10 palabras por categoría**.

Categorías requeridas:

- `ANIMALES`
- `TECNOLOGIA`
- `PAISES`
- `COLOMBIA`
- `PROGRAMACION`

Total mínimo: **50 palabras**.

---

## 🔄 Funcionamiento del juego

1. El usuario ingresa su nombre.
2. Se muestra el menú principal.
3. El usuario selecciona la opción **Jugar**.
4. Elige una categoría.
5. El programa selecciona una palabra aleatoria.
6. La palabra se muestra con guiones bajos.
7. El jugador ingresa una letra por turno.
8. Si acierta, se revelan las letras correctas.
9. Si falla, aumenta el número de errores.
10. El juego termina al completar la palabra o llegar a 6 errores.

---

## 🕹️ Menú principal

```text
===== JUEGO DEL AHORCADO =====

1. Jugar
2. Ver instrucciones
3. Tabla de récords
4. Salir

Seleccione una opción:
```

---

## ⚙️ Métodos principales

```java
mostrarAhorcado(int errores)
```

Muestra el dibujo del ahorcado según la cantidad de errores.

```java
mostrarPalabra(char[] estado)
```

Muestra las letras descubiertas y los guiones pendientes.

```java
validarLetra(char letra, String palabra, char[] estado)
```

Verifica si la letra ingresada está en la palabra.

```java
seleccionarPalabraAleatoria(String[] lista, int categoria)
```

Selecciona una palabra aleatoria usando `Math.random()`.

```java
estaCompleta(char[] estado)
```

Verifica si el jugador completó la palabra.

```java
verificarEasterEgg(String nombre)
```

Activa el modo secreto si el nombre ingresado es correcto.

---

## 📌 Lectura del CSV

Ejemplo básico:

```java
try {
    BufferedReader br = new BufferedReader(new FileReader("palabras.csv"));
    String linea = br.readLine();

    while ((linea = br.readLine()) != null) {
        String[] partes = linea.split(",");

        String categoria = partes[0];
        String palabra = partes[1];
        String pista = partes[2];
    }

    br.close();

} catch (IOException e) {
    System.out.println("Error al leer el archivo CSV.");
}
```

---

## 🧠 Conceptos usados

En este proyecto se trabajan los siguientes conceptos de Java:

- `String`
- `char[]`
- Métodos
- Arreglos
- Ciclos
- Condicionales
- `split()`
- `toLowerCase()`
- `charAt()`
- `length()`
- `Math.random()`
- Manejo de excepciones con `try-catch`

---

## 🥚 Bonus: Easter Egg

Si el jugador ingresa el nombre:

```text
XACARANA
```

Se activa el **Modo Dios**.

Este modo puede incluir:

- ASCII art especial.
- Categoría oculta `SECRETOS`.
- Palabras geek como `MATRIX`, `ZELDA`, `KONAMI`, `TARDIS`.
- Primera letra revelada automáticamente.

Método sugerido:

```java
public boolean verificarEasterEgg(String nombre) {
    return nombre.equals("XACARANA");
}
```

---

## ▶️ Cómo ejecutar el proyecto

### 1. Clonar el repositorio

```bash
git clone https://github.com/usuario/taller_ahorcado.git
```

### 2. Entrar a la carpeta

```bash
cd taller_ahorcado
```

### 3. Compilar

```bash
javac *.java
```

### 4. Ejecutar

```bash
java Main
```

---

## 📚 Preguntas teóricas

Al finalizar el taller se deben responder preguntas como:

- ¿Qué es un `String`?
- ¿Cuál es la diferencia entre `String` y `char[]`?
- ¿Para qué sirven `split()`, `toLowerCase()`, `charAt()` y `length()`?
- ¿Qué es un método en Java?
- ¿Qué diferencia hay entre un método `void` y uno con retorno?
- ¿Cómo funciona `Math.random()`?
- ¿Qué es un archivo CSV?
- ¿Por qué usar CSV en lugar de datos hardcodeados?

---

## ✅ Requisitos principales

- Crear el repositorio `taller_ahorcado`.
- Trabajar en grupo de 2 o 3 personas.
- Tener commits propios por integrante.
- Crear las clases principales del proyecto.
- Leer palabras desde `palabras.csv`.
- Usar mínimo 5 categorías.
- Usar mínimo 10 palabras por categoría.
- Implementar menú principal.
- Validar entradas incorrectas.
- Usar métodos con nombres descriptivos.
- Manejar errores con `try-catch`.
- Implementar el Easter Egg.

---

## 🧾 Conclusión

Este taller permite practicar conceptos fundamentales de Java mediante un juego interactivo.  
El proyecto fortalece el uso de métodos, cadenas de texto, arreglos, lectura de archivos CSV y organización del código en clases.

## Prueba Pull Shark #1

## Prueba Pull Shark #2

Segundo Pull Request de prueba.

Este cambio forma parte de una prueba de Pull Request.
