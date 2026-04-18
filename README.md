<<<<<<< HEAD
# 🏀 BasketStats Pro

Plataforma de análisis y seguimiento de estadísticas globales de baloncesto. Muestra datos de **180 jugadores** distribuidos en **6 ligas internacionales** con promedios de la temporada 2024-25.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

---

## 📸 Vista previa

| Función | Descripción |
|---------|-------------|
| Tabla interactiva | 180 jugadores con PTS, REB, AST |
| Filtro por liga | NBA, Euroliga, ACB, BSL, VTB, LNB Pro A |
| Búsqueda inteligente | Por nombre, equipo, posición o rangos (`pts > 25`) |
| Ordenamiento | Clic en cualquier cabecera para ordenar asc/desc |

---

## 🗂 Estructura del proyecto

```
basketstast1/
├── server.js             # Servidor Express (punto de entrada)
├── package.json          # Dependencias y scripts de inicio
├── public/               # Archivos estáticos
│   ├── index.html        # Página principal
│   ├── style.css         # Estilos y diseño responsive
│   └── script.js         # Lógica: datos, filtros, ordenamiento
├── README.md             # Este archivo
└── .vscode/              # Configuración del editor
```

### Archivos principales

| Archivo | Responsabilidad |
|---------|----------------|
| `server.js` | Servidor Node.js con Express. Sirve archivos estáticos desde `public/`. Puerto configurable vía variable de entorno `PORT`. |
| `package.json` | Dependencias (`express`) y script de inicio (`npm start`). |
| `public/index.html` | Estructura semántica HTML5. Hero section, toolbar de filtros, tabla de datos y footer con fuentes. Usa **Lucide Icons** y **Google Fonts** (Fira Sans / Fira Code). |
| `public/style.css` | Variables CSS custom, diseño responsive, paleta deportiva azul/naranja, badges por liga, animaciones de entrada, y estados hover/focus accesibles. |
| `public/script.js` | Array de 180 jugadores (30 por liga × 6 ligas). Motor de búsqueda inteligente con parser que detecta ligas, posiciones y rangos numéricos (`pts > 20`, `reb < 5`). Sistema de ordenamiento multi-columna. |

---

## ⚙️ Tecnologías y configuración

| Tecnología | Uso |
|-----------|-----|
| **HTML5** | Estructura semántica |
| **CSS3** | Custom Properties, Grid, Flexbox, animaciones |
| **JavaScript** (Vanilla) | Lógica de datos y DOM, sin frameworks |
| **Node.js + Express** | Servidor web para producción y Render |
| **Lucide Icons** | Iconografía SVG vía CDN |
| **Google Fonts** | Fira Sans + Fira Code |

### Dependencias

```bash
npm install   # Instala Express
```

### Dependencias externas (CDN)

```
https://unpkg.com/lucide@latest     → Iconos
https://fonts.googleapis.com/...    → Tipografías
```

---

## 🚀 Cómo ejecutar localmente

```bash
# 1. Instalar dependencias
npm install

# 2. Iniciar el servidor
npm start

# 3. Abrir en el navegador
# http://localhost:3000
```

El servidor usa el puerto definido en la variable de entorno `PORT`, o `3000` por defecto.

---

## 🌐 Despliegue en Render

### Paso a paso

1. **Crear cuenta** en [render.com](https://render.com) (gratis)
2. Clic en **"New" → "Web Service"**
3. **Conectar repositorio** de GitHub: `LeonelAc/basketstast1`
4. **Configurar el servicio:**

| Campo | Valor |
|-------|-------|
| **Name** | `basketstats-pro` |
| **Region** | Oregon (US West) |
| **Branch** | `main` |
| **Runtime** | `Node` |
| **Build Command** | `npm install` |
| **Start Command** | `node server.js` |
| **Plan** | Free |

5. Clic en **"Deploy Web Service"**
6. Esperar a que termine el deploy (~1-2 minutos)
7. Acceder a la URL pública generada por Render:
   ```
   https://basketstats-pro.onrender.com
   ```

### Variables de entorno (Render las configura automáticamente)

| Variable | Valor | Descripción |
|----------|-------|-------------|
| `PORT` | *(automático)* | Render asigna el puerto automáticamente |

### Actualizaciones automáticas

Cada vez que hagas `git push origin main`, Render re-despliega automáticamente.

---

## 📋 Logs y depuración

### Logs en Render

1. Ir al **Dashboard de Render** → seleccionar el servicio
2. Clic en la pestaña **"Logs"**
3. Ver en tiempo real los logs del servidor:
   ```
   BasketStats Pro corriendo en http://localhost:PORT
   ```
4. Los errores (500, 404, crash) aparecen aquí con stack trace

### Logs en local

```bash
# Iniciar servidor y ver logs en terminal
npm start
# Output: BasketStats Pro corriendo en http://localhost:3000
```

### Consola del navegador

```
F12 → Console (o Cmd+Option+J en macOS)
```

| Evento | Cómo verificarlo |
|--------|-----------------|
| Carga de datos | Verificar que la tabla muestra 180 filas al iniciar |
| Filtros activos | Los chips de filtro aparecen debajo de la barra de búsqueda |
| Errores de iconos | Revisar si Lucide carga correctamente en la consola |
| Conteo de resultados | El contador "X resultados encontrados" se actualiza en tiempo real |

### Network tab (rendimiento)

```
F12 → Network → Recargar la página
```

Verificar que cargan correctamente:
- `lucide` (iconos)
- `Fira Sans` (fuente)
- `Fira Code` (fuente mono)
- `script.js`, `style.css` (archivos locales)

---

## 📤 Cómo subir cambios al repositorio

### Primera vez (clonar y configurar)

```bash
git clone https://github.com/LeonelAc/basketstast1.git
cd basketstast1
```

### Subir cambios

```bash
# Ver qué archivos cambiaron
git status

# Agregar todos los cambios
git add .

# Crear un commit con mensaje descriptivo
git commit -m "Descripción de los cambios"

# Subir al repositorio remoto
git push origin main
```

### Flujo completo de ejemplo

```bash
# 1. Editar archivos...
# 2. Verificar cambios
git diff

# 3. Agregar y commitear
git add .
git commit -m "feat: agregar filtro por nacionalidad"

# 4. Subir
git push origin main
```

### Convenciones de commits recomendadas

| Prefijo | Uso |
|---------|-----|
| `feat:` | Nueva funcionalidad |
| `fix:` | Corrección de bug |
| `style:` | Cambios de estilos CSS |
| `docs:` | Cambios en documentación |
| `refactor:` | Refactorización de código |

---

## 🏟 Ligas incluidas

| Liga | País | Jugadores |
|------|------|-----------|
| NBA | Estados Unidos | 30 |
| Euroliga | Europa | 30 |
| ACB | España | 30 |
| BSL | Turquía | 30 |
| VTB United League | Rusia | 30 |
| LNB Pro A | Francia | 30 |

---

## 📝 Licencia

Demo analítica con fines educativos. Datos simulados basados en rendimiento real de la temporada 2024-25.

© 2026 BasketStats Pro
=======
# basketstats-pro
>>>>>>> 3666f1cf38cc6d35fbc46f712d5177509b52a44f
