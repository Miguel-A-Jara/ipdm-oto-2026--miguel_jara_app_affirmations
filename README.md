# Affirmations — App de lista desplazable (Android + Jetpack Compose)

Proyecto de la ruta de aprendizaje **"Crea una Lista Desplazable"** del curso
*Android Basics with Compose* (Unidad 3, ruta 2). Reúne en un solo repositorio
los dos codelabs solicitados:

- **Ejercicio 2 — Cómo agregar una lista desplazable**
- **Ejercicio 3 — Cómo cambiar el ícono de la app**

> Materia: **IPDM — Otoño 2025**

La app muestra una lista de afirmaciones, donde cada elemento es una tarjeta
(`Card`) con una imagen y un texto, dentro de una lista con scroll (`LazyColumn`).

---

## Ejercicio 2 — Lista desplazable

Lo implementado:

- **`model/Affirmation.kt`**: `data class` que representa una afirmación. Usa las
  anotaciones `@StringRes` y `@DrawableRes` para guardar los IDs del texto y de la
  imagen (en lugar de los valores en sí).
- **`data/Datasource.kt`**: clase con `loadAffirmations()`, que arma y devuelve la
  `List<Affirmation>` con las 10 afirmaciones (texto + imagen).
- **`MainActivity.kt`**:
  - `AffirmationCard`: una `Card` con una `Column` que apila la `Image`
    (recortada con `ContentScale.Crop`, alto de 194.dp) y el `Text`.
  - `AffirmationList`: una `LazyColumn` que recorre la lista con `items()` para
    obtener el desplazamiento.
  - `AffirmationsApp`: punto de entrada que pasa `Datasource().loadAffirmations()`
    a la lista.
  - `@Preview` de la tarjeta para ver el resultado en Android Studio.

## Ejercicio 3 — Cambiar el ícono de la app

Lo implementado (usando *Image Asset Studio* del codelab):

- Ícono **adaptable** con dos capas: `ic_launcher_foreground.xml` (primer plano) y
  `ic_launcher_background.xml` (fondo), ambos como *vector drawables*.
- `mipmap-anydpi-v26/ic_launcher.xml` y `ic_launcher_round.xml` con el elemento
  `<adaptive-icon>` que combina ambas capas (Android 8.0 / API 26+).
- Bitmaps de respaldo en `mipmap-{mdpi,hdpi,xhdpi,xxhdpi,xxxhdpi}` (`.webp`) para
  versiones anteriores a API 26.
- Referencias `android:icon` y `android:roundIcon` ya declaradas en el
  `AndroidManifest.xml`.

El historial de Git refleja el reemplazo del ícono provisional por el ícono
definitivo, para que se vea el *antes/después* del ejercicio.

---

## Requisitos

- **Android Studio** (Ladybug o posterior recomendado)
- **JDK 17+**
- Android Gradle Plugin **8.8.0**, Kotlin **2.1.0**, Gradle **8.12**
- `compileSdk = 35`, `minSdk = 24`, `targetSdk = 35`

## Cómo ejecutar

1. Abrir la carpeta del proyecto en Android Studio (`File > Open`).
2. Esperar a que sincronice Gradle y se descarguen las dependencias.
3. Elegir un emulador o dispositivo físico y presionar **Run ▶**.

## Estructura del proyecto

```
app/src/main/
├── AndroidManifest.xml
├── java/com/example/affirmations/
│   ├── MainActivity.kt          # UI: AffirmationsApp / AffirmationList / AffirmationCard
│   ├── data/Datasource.kt       # Origen de datos (loadAffirmations)
│   ├── model/Affirmation.kt     # data class Affirmation
│   └── ui/theme/                # Theme.kt, Color.kt (Material 3)
└── res/
    ├── drawable/                # image1..image10 + capas del ícono
    ├── mipmap-anydpi-v26/       # <adaptive-icon>
    ├── mipmap-*dpi/             # bitmaps del ícono
    └── values/                  # strings.xml, themes.xml
```

## Historial de commits

1. `chore:` estructura base del proyecto (Gradle + Compose).
2. `feat:` ejercicio 2 — lista desplazable de afirmaciones.
3. `feat:` ejercicio 3 — cambiar el ícono de la app.
4. `docs:` este README.

---

## Créditos y licencia

Basado en el material oficial del curso **Android Basics with Compose** de Google
(*Affirmations app*), distribuido bajo **Apache License 2.0**. Se conservan las
cabeceras de licencia en cada archivo y el archivo `LICENSE`. Las imágenes y el
ícono provienen de los recursos del curso. Trabajo realizado con fines educativos.
