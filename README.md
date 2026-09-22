# 🧩 Tmux Configuration & Cheat Sheet (Guía Completa)

Guía completa de configuración, atajos de teclado, comandos de terminal (CLI), gestión de paneles y ventanas, modo copia estilo Vim y comandos de plugins instalados en este entorno.

> **Prefix:** `Ctrl + a` (reemplaza al estándar `Ctrl + b`)  
> **Navegación Vim/Tmux:** `Ctrl + h / j / k / l` (sin Prefix)  
> **Gestor de Sesiones Flotante:** `Prefix + o` (Tmux SessionX)

---

## 📑 Índice

1. [💻 Comandos de Terminal CLI (Gestión de Sesiones desde la Shell)](#1--comandos-de-terminal-cli-gestión-de-sesiones-desde-la-shell)
2. [⌨️ Atajos Esenciales y de Sistema](#2-️-atajos-esenciales-y-de-sistema)
3. [🪟 Gestión de Paneles (Splits, Navegación, Redimensión y Zoom)](#3--gestión-de-paneles-splits-navegación-redimensión-y-zoom)
4. [🗂️ Gestión de Ventanas](#4-️-gestión-de-ventanas)
5. [📋 Modo Copia y Portapapeles (Vim Style)](#5--modo-copia-y-portapapeles-vim-style)
6. [🔌 Plugins Instalados y sus Comandos](#6--plugins-instalados-y-sus-comandos)
   - [6.1 TPM (Tmux Plugin Manager)](#61-tpm-tmux-plugin-manager)
   - [6.2 tmux-sessionx (Navegador Fuzzy con Vista Previa)](#62-tmux-sessionx-navegador-fuzzy-con-vista-previa)
   - [6.3 christoomey/vim-tmux-navigator (Navegación Neovim ↔ Tmux)](#63-christoomeyvim-tmux-navigator-navegación-neovim--tmux)
   - [6.4 tmux-resurrect y tmux-continuum (Persistencia y Autoguardado)](#64-tmux-resurrect-y-tmux-continuum-persistencia-y-autoguardado)
   - [6.5 Catppuccin, Battery y Online Status (Tema y Barra de Estado)](#65-catppuccin-battery-y-online-status-tema-y-barra-de-estado)
7. [🖱️ Ratón y Terminal](#7-️-ratón-y-terminal)
8. [🚀 Instalación y Puesta en Marcha](#8--instalación-y-puesta-en-marcha)

---

## 1. 💻 Comandos de Terminal CLI (Gestión de Sesiones desde la Shell)

Comandos para ejecutar directamente en tu terminal (`zsh` / `bash` / `fish`) antes de entrar o para interactuar con sesiones activas de tmux:

| Comando                                     | Descripción                                                                              |
| :------------------------------------------ | :--------------------------------------------------------------------------------------- |
| `tmux`                                      | Inicia una nueva sesión anónima (con número incremental).                                |
| `tmux new -s <nombre>`                      | Inicia una nueva sesión con un nombre descriptivo.                                       |
| `tmux ls` _(o `tmux list-sessions`)_        | Lista todas las sesiones activas, número de ventanas y fecha de creación.                |
| `tmux a` _(o `tmux attach`)_                | Se reconecta a la última sesión utilizada.                                               |
| `tmux a -t <nombre>`                        | Se reconecta a la sesión específica indicada.                                            |
| `tmux a -d -t <nombre>`                     | Se conecta a la sesión y desconecta cualquier otro cliente activo (pantalla completa).   |
| `tmux kill-session -t <nombre>`             | Cierra y destruye la sesión especificada y todos sus procesos.                           |
| `tmux kill-server`                          | Cierra **todas** las sesiones y detiene el servidor de tmux por completo.                |
| `tmux source-file ~/.config/tmux/tmux.conf` | Recarga la configuración de tmux directamente desde la terminal.                         |
| `tmux has-session -t <nombre>`              | Comprueba si existe una sesión (útil para scripts, devuelve código de salida `0` o `1`). |

---

## 2. ⌨️ Atajos Esenciales y de Sistema

Todos los atajos que comienzan con `Prefix` requieren presionar **`Ctrl + a`**, soltarlo y luego presionar la tecla indicada.

| Atajo                       | Acción                     | Descripción                                                                                        |
| :-------------------------- | :------------------------- | :------------------------------------------------------------------------------------------------- |
| `Ctrl + a`                  | **Prefix**                 | Clave principal para activar atajos de tmux.                                                       |
| `Ctrl + a` luego `Ctrl + a` | **Send Prefix**            | Envía un `Ctrl + a` literal a la aplicación dentro del panel (útil para tmux anidados o readline). |
| `Prefix + r`                | **Recargar Configuración** | Vuelve a cargar `~/.config/tmux/tmux.conf` y muestra la notificación _"tmux config reloaded"_.     |
| `Prefix + :`                | **Línea de Comandos**      | Abre el prompt interactivo de comandos de tmux (`:set`, `:new`, etc.).                             |
| `Prefix + ?`                | **Listar Atajos**          | Muestra todos los atajos de teclado actualmente activos con su comando asociado.                   |
| `Prefix + d`                | **Detach (Desconectar)**   | Se desconecta de la sesión actual dejándola corriendo en segundo plano.                            |
| `Prefix + ~`                | **Historial de Mensajes**  | Muestra el registro de mensajes y alertas de tmux.                                                 |
| `Prefix + t`                | **Reloj Digital**          | Muestra un reloj grande en el panel actual (presiona cualquier tecla para salir).                  |

---

## 3. 🪟 Gestión de Paneles (Splits, Navegación, Redimensión y Zoom)

### División de Paneles (Splits)

Los nuevos paneles se crean automáticamente heredando el directorio de trabajo del panel actual (`pane_current_path`).

| Atajo         | Tipo de Split                 | Descripción                                                      |
| :------------ | :---------------------------- | :--------------------------------------------------------------- |
| `Prefix + \|` | **Horizontal (Lado a lado)**  | Divide la ventana en paneles verticales (izquierda / derecha).   |
| `Prefix + -`  | **Vertical (Arriba / abajo)** | Divide la ventana en paneles horizontales (superior / inferior). |

### Navegación entre Paneles (Integración Vim)

Gracias a `vim-tmux-navigator`, la navegación es instantánea **sin necesidad de presionar el Prefix**:

| Atajo (Directo) | Dirección     | Descripción                                                  |
| :-------------- | :------------ | :----------------------------------------------------------- |
| `Ctrl + h`      | **Izquierda** | Salta al panel/split izquierdo (en tmux o dentro de Neovim). |
| `Ctrl + j`      | **Abajo**     | Salta al panel/split inferior (en tmux o dentro de Neovim).  |
| `Ctrl + k`      | **Arriba**    | Salta al panel/split superior (en tmux o dentro de Neovim).  |
| `Ctrl + l`      | **Derecha**   | Salta al panel/split derecho (en tmux o dentro de Neovim).   |
| `Ctrl + \`      | **Previo**    | Alterna al último panel/split enfocado anteriormente.        |

> [!NOTE]  
> Si estás dentro de Neovim y tienes el plugin `vim-tmux-navigator` configurado, estos mismos atajos cruzan la frontera entre las ventanas de Neovim y los paneles de Tmux sin interrupción.

### Redimensionamiento de Paneles (Vim Style)

Estos atajos son repetibles (puedes presionar `Prefix` una vez y luego mantener o pulsar varias veces la tecla):

| Atajo        | Dirección     | Cambio de Tamaño                                         |
| :----------- | :------------ | :------------------------------------------------------- |
| `Prefix + h` | **Izquierda** | Reduce o expande el panel 5 columnas hacia la izquierda. |
| `Prefix + j` | **Abajo**     | Reduce o expande el panel 5 filas hacia abajo.           |
| `Prefix + k` | **Arriba**    | Reduce o expande el panel 5 filas hacia arriba.          |
| `Prefix + l` | **Derecha**   | Reduce o expande el panel 5 columnas hacia la derecha.   |

### Control Avanzado de Paneles

| Atajo                           | Acción                     | Descripción                                                                                                                     |
| :------------------------------ | :------------------------- | :------------------------------------------------------------------------------------------------------------------------------ |
| `Prefix + m` _(o `Prefix + z`)_ | **Toggle Zoom**            | Maximiza el panel activo a pantalla completa o lo restaura a su tamaño previo. Muestra el badge ` zoom` en la barra de estado. |
| `Prefix + x`                    | **Cerrar Panel**           | Mata el panel actual (pide confirmación `y/n`).                                                                                 |
| `Prefix + !`                    | **Extraer Panel**          | Convierte el panel activo en una nueva ventana independiente (_break pane_).                                                    |
| `Prefix + q`                    | **Identificar Paneles**    | Muestra los índices numéricos de cada panel en pantalla. Pulsa el número para saltar directamente.                              |
| `Prefix + {`                    | **Intercambiar Previo**    | Mueve el panel activo a la posición del panel anterior.                                                                         |
| `Prefix + }`                    | **Intercambiar Siguiente** | Mueve el panel activo a la posición del panel siguiente.                                                                        |
| `Prefix + Espacio`              | **Cambiar Disposición**    | Alterna cíclicamente entre disposiciones predefinidas (paneles iguales en horizontal, vertical, cuadrícula, etc.).              |

---

## 4. 🗂️ Gestión de Ventanas

Las ventanas funcionan como pestañas dentro de la sesión de Tmux:

| Atajo                 | Acción                     | Descripción                                                                                                      |
| :-------------------- | :------------------------- | :--------------------------------------------------------------------------------------------------------------- |
| `Prefix + c`          | **Nueva Ventana**          | Crea una nueva ventana vacía en la sesión actual.                                                                |
| `Prefix + ,`          | **Renombrar Ventana**      | Abre un diálogo para cambiar el nombre de la ventana en la barra de estado.                                      |
| `Prefix + &`          | **Cerrar Ventana**         | Cierra la ventana activa y todos sus paneles (pide confirmación `y/n`).                                          |
| `Prefix + p`          | **Ventana Anterior**       | Cambia a la ventana previa en la lista.                                                                          |
| `Prefix + 0` … `9`    | **Ir a Ventana N**         | Salta directamente a la ventana por su número de índice.                                                         |
| `Prefix + w`          | **Selector de Ventanas**   | Abre un árbol interactivo para buscar y cambiar de ventana o sesión.                                             |
| `Prefix + '`          | **Seleccionar por Índice** | Solicita teclear el índice de la ventana a la cual saltar.                                                       |
| `Prefix + .`          | **Mover Ventana**          | Permite reasignar el número de índice de la ventana actual.                                                      |
| `Alt + h` _(o `M-h`)_ | **Renumerar Ventanas**     | Ejecuta `move-window -r`, compactando los números de ventana sin huecos (ej: si quedan 1, 3, 5 pasan a 1, 2, 3). |
| `Prefix + f`          | **Buscar Ventana**         | Busca una ventana por nombre o contenido de texto.                                                               |

---

## 5. 📋 Modo Copia y Portapapeles (Vim Style)

La configuración utiliza `mode-keys vi` para moverse y seleccionar texto como en Vim.

### Activación y Navegación

- **Entrar en modo copia:** `Prefix + v` _(también funciona el nativo `Prefix + [`)_.
- **Salir / Cancelar:** `q` o `Escape`.

| Tecla (en modo copia)   | Movimiento                                                |
| :---------------------- | :-------------------------------------------------------- |
| `h` / `j` / `k` / `l`   | Mover cursor a izquierda / abajo / arriba / derecha.      |
| `w` / `b` / `e`         | Saltar palabra adelante / palabra atrás / fin de palabra. |
| `0` / `$`               | Saltar al inicio / final de la línea.                     |
| `^`                     | Primer carácter no blanco de la línea.                    |
| `g` _(o `gg`)_          | Ir al principio absoluto del historial de scrollback.     |
| `G`                     | Ir al final (última línea) del historial.                 |
| `Ctrl + u` / `Ctrl + d` | Desplazarse media página arriba / media página abajo.     |
| `Ctrl + b` / `Ctrl + f` | Desplazarse una página completa arriba / abajo.           |
| `/`                     | Buscar texto hacia adelante (abajo).                      |
| `?`                     | Buscar texto hacia atrás (arriba).                        |
| `n` / `N`               | Siguiente coincidencia / coincidencia previa de búsqueda. |

### Selección y Copia

| Tecla (en modo copia) | Acción                                                                                  |
| :-------------------- | :-------------------------------------------------------------------------------------- |
| `v`                   | Inicia la selección de caracteres (`begin-selection`).                                  |
| `Ctrl + v`            | Alterna modo de selección por bloque / rectángulo.                                      |
| `y`                   | Copia el texto seleccionado al buffer de tmux (`copy-selection`) y sale del modo copia. |

> [!TIP]  
> Se ha configurado `unbind -T copy-mode-vi MouseDragEnd1Pane` para que al soltar el ratón tras seleccionar texto no se cierre abruptamente la vista de copia.

### Pegado y Gestión de Búferes

| Atajo        | Acción             | Descripción                                                                     |
| :----------- | :----------------- | :------------------------------------------------------------------------------ |
| `Prefix + ]` | **Pegar Buffer**   | Pega el contenido copiado más recientemente en el panel activo.                 |
| `Prefix + #` | **Listar Búferes** | Muestra todos los fragmentos de texto almacenados en el historial de copias.    |
| `Prefix + =` | **Elegir Buffer**  | Menú interactivo para seleccionar y pegar cualquiera de los búferes anteriores. |

---

## 6. 🔌 Plugins Instalados y sus Comandos

Los plugins se gestionan con **Tmux Plugin Manager (TPM)** en la ruta `~/.config/tmux/plugins/`.

---

### 6.1 TPM (Tmux Plugin Manager)

Controla la instalación, actualización y limpieza de plugins.

| Atajo              | Acción         | Descripción                                                                |
| :----------------- | :------------- | :------------------------------------------------------------------------- |
| `Prefix + I`       | **Instalar**   | Descarga e inicializa nuevos plugins declarados en `tmux.conf`.            |
| `Prefix + U`       | **Actualizar** | Actualiza todos los plugins instalados a su última versión de git.         |
| `Prefix + Alt + u` | **Limpiar**    | Desinstala los plugins que ya no estén listados en el archivo `tmux.conf`. |

---

### 6.2 tmux-sessionx (Navegador Fuzzy con Vista Previa)

Gestor moderno de sesiones basado en `fzf` en ventana flotante con vista previa en vivo de paneles y navegación de directorios.

- **Atajo para abrir:** **`Prefix + o`**

#### Controles interactivos dentro de SessionX:

| Atajo (en popup)        | Acción                   | Descripción                                                                                                            |
| :---------------------- | :----------------------- | :--------------------------------------------------------------------------------------------------------------------- |
| `<Enter>`               | **Seleccionar / Crear**  | Cambia a la sesión seleccionada. Si el nombre escrito no existe, **crea una nueva sesión** con ese nombre al instante. |
| `Alt + Backspace`       | **Eliminar Sesión**      | Destruye la sesión seleccionada en la lista.                                                                           |
| `Ctrl + r`              | **Renombrar**            | Abre un prompt interactivo para cambiar el nombre de la sesión seleccionada.                                           |
| `Ctrl + w`              | **Modo Ventana**         | Cambia la vista para listar todas las **ventanas** de todas las sesiones con previsualización.                         |
| `Ctrl + e`              | **Modo Expandir (PWD)**  | Explora subdirectorios del directorio actual para crear una sesión en cualquiera de ellos.                             |
| `Ctrl + x`              | **Explorar `~/.config`** | Lista carpetas dentro de tu directorio de configuración para crear o abrir sesiones.                                   |
| `Ctrl + b`              | **Volver**               | Regresa a la lista principal de sesiones después de entrar en modo ventana o expandido.                                |
| `Ctrl + t`              | **Modo Árbol**           | Muestra la jerarquía completa en formato de árbol (sesiones y ventanas).                                               |
| `Ctrl + u` / `Ctrl + d` | **Scroll Preview**       | Sube o baja la previsualización del contenido del panel.                                                               |
| `Ctrl + p` / `Ctrl + n` | **Navegar Lista**        | Sube o baja en la lista de resultados de fzf (también flechas arriba/abajo).                                           |
| `?`                     | **Alternar Preview**     | Muestra u oculta la ventana lateral de vista previa.                                                                   |
| `<Esc>` / `Ctrl + c`    | **Cerrar**               | Sale del selector SessionX sin realizar cambios.                                                                       |

---

### 6.3 christoomey/vim-tmux-navigator (Navegación Neovim ↔ Tmux)

Permite saltar fluidamente entre paneles de tmux y splits de Neovim usando los mismos atajos sin pulsar Prefix:

| Atajo      | Acción                                              |
| :--------- | :-------------------------------------------------- |
| `Ctrl + h` | Foco a la izquierda (Tmux / Neovim).                |
| `Ctrl + j` | Foco hacia abajo (Tmux / Neovim).                   |
| `Ctrl + k` | Foco hacia arriba (Tmux / Neovim).                  |
| `Ctrl + l` | Foco a la derecha (Tmux / Neovim).                  |
| `Ctrl + \` | Alternar con el split / panel previamente enfocado. |

---

### 6.4 tmux-resurrect y tmux-continuum (Persistencia y Autoguardado)

Garantizan que tu entorno de trabajo (sesiones, ventanas, splits, directorios y contenido) sobreviva a reinicios del sistema.

#### Comportamiento Automático:

- **Autoguardado continuo:** Guarda el estado completo de tmux en segundo plano cada **15 minutos**.
- **Autorestauración:** Al arrancar el servidor de tmux, restaura de forma automática todas las sesiones, layouts y ventanas exactamente como las dejaste (`@continuum-restore "on"`).
- **Contenido de paneles:** Preserva y restaura el texto dentro de los paneles (`@resurrect-capture-pane-contents "on"`).

#### Atajos Manuales (Tmux Resurrect):

| Atajo               | Acción               | Descripción                                                                        |
| :------------------ | :------------------- | :--------------------------------------------------------------------------------- |
| `Prefix + Ctrl + s` | **Guardar Manual**   | Fuerza el guardado inmediato de todas las sesiones, paneles y contenidos en disco. |
| `Prefix + Ctrl + r` | **Restaurar Manual** | Restaura inmediatamente el último estado guardado en disco.                        |

---

### 6.5 Catppuccin, Battery y Online Status (Tema y Barra de Estado)

Personalización estética y monitoreo del sistema en la barra de estado inferior:

- **Tema Catppuccin Mocha:** Colores oscuros con acentos coloridos, separadores limpios (`│`) y formato minimalista.
- **Lado Izquierdo:**
  - ` #S`: Nombre de la sesión actual (cambia a fondo rojo llamativo al pulsar el `Prefix`).
  - ` <ruta>`: Directorio de trabajo del panel activo.
  - ` zoom`: Indicador amarillo visible únicamente cuando el panel actual está maximizado.
- **Centro:** Lista de ventanas numeradas con el proceso en ejecución (`automatic-rename on`). La ventana activa destaca con fondo melocotón (`peach`).
- **Lado Derecho:**
  - Icono de batería y porcentaje dinámico (resaltado en rojo si baja del 10%).
  - Conectividad Wi-Fi / Red: `󰖩 on` (morado) o `󰖪 off` (rojo invertido) según el estado de conexión.

---

## 7. 🖱️ Ratón y Terminal

- **Soporte de Ratón Activo (`mouse on`):**
  - Haz clic en cualquier panel para darle el foco.
  - Arrastra las líneas divisorias de los paneles para redimensionarlos con el cursor.
  - Usa la rueda del ratón para hacer scroll hacia arriba y entrar automáticamente al historial en modo copia.
  - Haz clic en los nombres de las ventanas en la barra de estado para cambiar de ventana.
- **Color Verdadero (24-bit True Color):**
  - Terminal configurada en `tmux-256color` con `xterm-256color:RGB`.
  - Soporte de `allow-passthrough on` para gráficos y renderizado avanzado (imágenes, kitty graphics protocol, etc.).

---

## 8. 🚀 Instalación y Puesta en Marcha

Para clonar y configurar este entorno en una máquina nueva:

1. **Instalar Tmux Plugin Manager (TPM):**

   ```bash
   git clone https://github.com/tmux-plugins/tpm ~/.config/tmux/plugins/tpm
   ```

2. **Asegurar dependencias recomendadas para plugins:**

   ```bash
   # En macOS con Homebrew:
   brew install fzf bat
   ```

3. **Iniciar Tmux:**

   ```bash
   tmux
   ```

4. **Instalar todos los plugins declarados:**
   - Presiona `Ctrl + a` seguido de `I` (mayúscula).
   - Espera a que TPM clone e instale los plugins.

5. **Recargar la configuración:**
   - Presiona `Ctrl + a` seguido de `r`.
