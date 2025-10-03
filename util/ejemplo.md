
---

## ✅ ¿Qué vamos a hacer?

Una app sencilla que:

* Muestra una **ventana gráfica (Swing)** con un botón.
* Al hacer clic en el botón, muestra un mensaje.
* Tiene una **estructura compatible para empaquetar como `.exe` con Launch4j** desde IntelliJ.
* Está lista para agregar **validación de licencia más adelante** si quieres.

---

## 🧰 Requisitos

* **IntelliJ IDEA (Community o Ultimate)**
* **JDK 17 (o 8 mínimo)**
* **Launch4j** (para el `.exe`, lo vemos después)

---

## 🏗️ Paso 1: Crear el proyecto en IntelliJ

1. Abre IntelliJ → `File > New > Project`
2. Selecciona:

   * **Language**: Java
   * **Build System**: IntelliJ (sin Maven/Gradle para mantenerlo simple)
   * **JDK**: Selecciona JDK 17 o 8
3. Nombre del proyecto: `MiAppJavaSwing`

---

## 📁 Estructura del proyecto

Tu proyecto se verá así:

```
MiAppJavaSwing/
 └── src/
     └── Main.java
```

---

## ✍️ Paso 2: Código de la aplicación

Copia esto en `src/Main.java`:

```java
import javax.swing.*;

public class Main {
    public static void main(String[] args) {
        // Estilo nativo
        try {
            UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
        } catch (Exception e) {
            e.printStackTrace();
        }

        // Crear ventana
        JFrame frame = new JFrame("Mi App Java Swing");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(400, 200);

        // Crear botón
        JButton button = new JButton("Haz clic aquí");
        button.addActionListener(e -> JOptionPane.showMessageDialog(frame, "¡Hola desde Java!"));

        // Agregar botón a la ventana
        frame.getContentPane().add(button);
        frame.setLocationRelativeTo(null); // Centrar
        frame.setVisible(true);
    }
}
```

---

## 🧪 Paso 3: Ejecutar para probar

Haz clic derecho en `Main.java` → `Run Main.main()`

✅ Deberías ver una ventana con un botón y un mensaje emergente.

---

## 📦 Paso 4: Empaquetar como `.jar` ejecutable

### Desde IntelliJ:

1. Ve a `File > Project Structure > Artifacts`
2. Haz clic en el **+** → `JAR > From modules with dependencies`
3. Selecciona tu clase `Main`
4. Marca **"Extract to the target JAR"** para incluir todo.
5. En **Output directory**, elige dónde guardar el `.jar`
6. Aplica y haz clic en OK

Luego:

* Ve a `Build > Build Artifacts > Build`

✅ Se generará un `.jar` ejecutable en `out/artifacts/MiAppJavaSwing_jar/`.

Puedes ejecutarlo con doble clic (si tienes JRE configurado) o con:

```bash
java -jar MiAppJavaSwing.jar
```

---

## 🛠️ Paso 5: Convertir a `.exe` con Launch4j (una vez)

### 1. Descarga Launch4j

Desde: [http://launch4j.sourceforge.net/](http://launch4j.sourceforge.net/)

No requiere instalación, solo descomprimir.

### 2. Configura Launch4j:

* **Output file**: `MiApp.exe`
* **Jar**: tu `.jar` generado en `out/artifacts/...`
* **Classpath**: Déjalo vacío (si ya está todo en el `.jar`)
* **Main class**: Automáticamente detectado del `.jar`
* **JRE version**: `1.8.0` o `17.0.0` (según tu JDK)
* **Icon** (opcional): Puedes poner un `.ico` personalizado

✔️ Presiona **"Build wrapper"**

✅ Tendrás `MiApp.exe`, listo para distribución.

---

## 📌 Siguiente paso opcional

Si quieres:

* Agregar **validación de licencia al iniciar**
* Hacer un **instalador** con íconos y accesos directos
* Usar **jpackage** para incluir JRE (sin necesidad de Java en el cliente)

Te puedo ayudar con eso también, paso a paso.

---

## ✅ Resumen

| Tarea                        | Herramienta                                  |
| ---------------------------- | -------------------------------------------- |
| Crear GUI con botón          | Java Swing                                   |
| Ejecutar desde IntelliJ      | `Run`                                        |
| Empaquetar `.jar` ejecutable | `Project Structure > Artifacts`              |
| Convertir a `.exe`           | [Launch4j](http://launch4j.sourceforge.net/) |

---
