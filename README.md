# Analytix — Reporte Gerencial CCTV

Dashboard interactivo de monitoreo gerencial para clientes CCTV de **Analytix (GSS)**.

## Características

- **Sincronización bidireccional con GitHub**: lee y escribe `data/clientes.json` directamente vía GitHub API
- **Edición en vivo**: click en cualquier cliente para editar todos sus campos, guardar = commit automático
- **Agregar / Eliminar clientes**: cambios se reflejan inmediatamente en el repositorio
- **Auto-sync cada 60s**: si otro miembro del equipo cambia el JSON, el dashboard se actualiza
- **Tema dark/light** con persistencia en localStorage
- **KPIs en tiempo real**: clientes, componentes, conexiones, salud del portafolio
- **Gráficos Chart.js**: distribución por sector, top 5, estado general
- **Export CSV/JSON** desde el dashboard
- **GitHub Pages ready**: funciona como sitio estático, sin backend

## Estructura

```
analytix-dashboard/
├── index.html              ← Dashboard principal
├── data/
│   └── clientes.json       ← Fuente de datos (sincronizada)
├── README.md
└── .gitignore
```

## Setup

### 1. Crear repositorio en GitHub

```bash
git init
git add .
git commit -m "Initial: Analytix Dashboard"
git remote add origin https://github.com/TU_USUARIO/analytix-dashboard.git
git push -u origin main
```

### 2. Habilitar GitHub Pages

En el repo → **Settings → Pages → Source: main / root** → Save.
El dashboard estará en `https://TU_USUARIO.github.io/analytix-dashboard/`

### 3. Crear Personal Access Token (PAT)

1. GitHub → **Settings → Developer settings → Personal access tokens → Fine-grained tokens**
2. **New token**:
   - Nombre: `analytix-dashboard`
   - Expiration: 90 días o Custom
   - Repository access: **Only select repositories** → seleccionar `analytix-dashboard`
   - Permissions → **Contents**: Read and write
3. Copiar el token generado

### 4. Configurar en el dashboard

1. Abrir el dashboard en el navegador
2. Click en **⚙ Config** en el header
3. Llenar:
   - **Repositorio**: `tu-usuario/analytix-dashboard`
   - **Ruta del JSON**: `data/clientes.json` (ya viene por defecto)
   - **GitHub Token**: pegar el PAT
4. Click **💾 Guardar y conectar**

El token se almacena **solo en tu navegador** (localStorage). Nunca se envía a otro servidor que no sea `api.github.com`.

## Uso

| Acción | Cómo |
|--------|------|
| **Ver detalle** | Click en un cliente |
| **Editar** | Click → modificar campos → **💾 Guardar y sincronizar** |
| **Agregar** | Botón **＋ Agregar cliente** |
| **Eliminar** | Click en cliente → **🗑 Eliminar** (con confirmación) |
| **Forzar sync** | Botón **🔄 Sync** en el header |
| **Cambiar tema** | Toggle 🌙/☀️ en el header |

Cada acción de escritura genera un commit automático en el repositorio con mensaje descriptivo.

## Equipo

| Nombre | Cargo | Clientes |
|--------|-------|----------|
| Rafa | Líder Técnico | Nissan Colviseg, Entel, Colviseg, Gimnasio |
| Oscar R | Analista Senior | Claro, Cannon, GBC, Titan Plaza, Ladrillera |
| David L | Analista | Gecolsa, Reencafe, Nutresa, Sterigenic |

## Stack

- HTML5 + CSS3 (variables, glass morphism, responsive)
- Chart.js (doughnut, bar horizontal, stacked bar)
- GitHub REST API v3 (Contents endpoint)
- Cero dependencias de build — un solo archivo HTML

---

**Analytix — GSS** · Monitoreo CCTV · 2026
