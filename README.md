# Mis Hábitos — app para Kimberly

App de Android 100% offline: hábitos diarios y tareas de un solo día, notificaciones
que insisten cada 12 minutos hasta que las atiendes, reprogramación automática al
posponer (se asigna sola al siguiente lapso libre del día), estadísticas de
cumplimiento por hábito, y una sección de notas/diario. El primer aviso del día y el
último incluyen un recordatorio extra para revisar/editar tus tareas.

Ya viene precargada con tu horario (ejercicio 6:30am, bloques de trabajo 9-2 y 3-6
con descansos activos rotando, estudio/familia alternando 7-10pm, resumen 10pm).
Puedes editar, agregar o quitar cualquier tarea desde la app.

## Cómo obtener el APK instalable (gratis, sin computadora potente)

1. Crea una cuenta gratuita en [github.com](https://github.com) si no tienes una.
2. Crea un repositorio nuevo (botón verde "New"), ponle el nombre que quieras
   (ej. `mis-habitos`), y déjalo como está (no hace falta marcar nada especial).
3. Dentro del repo recién creado, usa "Add file" → "Upload files" y arrastra
   **todo el contenido** de esta carpeta (incluyendo la carpeta oculta `.github`,
   asegúrate de que se suba junto con lo demás — si al arrastrar no aparece,
   sube primero todo lo demás y luego crea manualmente el archivo
   `.github/workflows/build-apk.yml` con "Create new file" pegando su contenido).
4. Dale "Commit changes".
5. Ve a la pestaña **Actions** del repositorio. Debería aparecer un flujo llamado
   "Compilar APK" corriendo solo. Si no corre automáticamente, entra a él y dale
   "Run workflow".
6. Espera unos 3-5 minutos a que termine (ícono verde ✔).
7. Entra a esa ejecución terminada, baja hasta "Artifacts" y descarga
   `habitos-debug-apk` (es un .zip que contiene el `app-debug.apk`).
8. Pasa ese APK a tu celular (por correo, Drive, cable USB, como prefieras) y ábrelo.
   Android te va a pedir permitir "instalar apps de fuentes desconocidas" para ese
   origen — actívalo solo para esa instalación.
9. Al abrir la app por primera vez, acepta el permiso de notificaciones y, si te lo
   pide, activa "Alarmas y recordatorios" en Ajustes — esto es lo que garantiza que
   las notificaciones no fallen aunque no tengas internet.

## Si la compilación falla   

Copia el mensaje de error de la pestaña Actions (la parte en rojo) y compártelo;
con eso se puede corregir el código y volver a intentar. Es normal que un proyecto
escrito sin poder compilarlo en el momento necesite un ajuste menor la primera vez.

## Estructura del proyecto

- `app/src/main/java/com/kimberly/habitos/data` — modelos y base de datos local (Room).
- `.../repo` — lógica de negocio: generar el día, posponer, estadísticas, y la
  precarga inicial de tu horario (`Seeder.kt`).
- `.../scheduling` — alarmas del sistema (offline), notificaciones y sus botones
  de acción ("Hecho" / "Posponer").
- `.../ui` — pantallas: Hoy, Estadísticas, Notas (Jetpack Compose).
