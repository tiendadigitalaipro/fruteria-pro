# 🍎 FRUTERIA PRO — LEE ESTE ARCHIVO PRIMERO

> Evita gastar tokens leyendo las 3030+ líneas del HTML. Usa este archivo como referencia rápida.

---

## 🎯 ROL DEL AGENTE
Eres el Agente Técnico Senior de Fruteria Pro, un POS para fruterías venezolanas por A2K Digital Studio. Archivo principal: `fruteria-pro.html` (~3030 líneas). Todo CSS+HTML+JS inline en un solo archivo.

---

## 📁 ESTRUCTURA DEL PROYECTO

```
fruteria-pro/
├── fruteria-pro.html         ← App principal (~3030 líneas) — ARCHIVO ÚNICO
├── ABRIR-FRUTERIA.bat
├── README.md
└── _CLAUDE-CONTEXT/
    ├── FRUTERIA-PRO.md       ← Arquitectura y referencia rápida
    ├── ERRORES-CONOCIDOS.md  ← Bugs y soluciones
    └── SKILLS-SEGURIDAD.md   ← Iron Lock y licencias
```

---

## 🏗️ ESTRUCTURA INTERNA DEL HTML

| Bloque | Líneas aprox. | Descripción |
|---|---|---|
| CSS global + variables | 1 – 250 | :root vars, estilos completos |
| Login Screen | 323 – 360 | `#loginScreen` pantalla de licencia |
| Demo Block Overlay | 342 – 360 | `#demoBlock` fullscreen bloqueo |
| App Principal HTML | 361 – 650 | `#app` sidebar + topbar + páginas |
| Modales HTML | 651 – 1010 | modalProducto, modalCobro, modalCliente, modalFiado, modalDevolucion |
| JS principal | 1011 – 2870 | Toda la lógica |
| Funciones Etiquetas | 2870 – 2937 | abrirEtiquetas, renderEtiquetasPreview, imprimirEtiquetas |

---

## 📱 PÁGINAS ACTIVAS

| ID | Módulo |
|---|---|
| `#page-dashboard` | Dashboard / KPIs |
| `#page-pos` | Punto de Venta |
| `#page-inventario` | Inventario + botón Etiquetas |
| `#page-historial` | Historial de ventas |
| `#page-devoluciones` | Devoluciones |
| `#page-clientes` | Clientes / Fiados |
| `#page-proveedores` | Proveedores |
| `#page-reportes` | Reportes |
| `#page-caja` | Gestión de Caja |
| `#page-configuracion` | Configuración |

---

## 🎨 DISEÑO VISUAL (Mercado Tropical)

```css
--bg:#f0f7f0          /* Fondo principal verde muy claro */
--sidebar:#1b4332     /* Sidebar verde oscuro bosque */
--accent:#2d6a4f      /* Acento verde */
--accent2:#52b788     /* Acento secundario */
--orange:#f77f00      /* Naranja activo/botones */
--card:#ffffff        /* Tarjetas blancas */
--text:#1a2e1a        /* Texto oscuro */
--border:#c8e6c9      /* Bordes verdes */
```
Fuente: `'Segoe UI', system-ui, sans-serif`

---

## 💾 LOCALSTORAGE KEYS (prefijo `fp_`)

| Clave | Contenido |
|---|---|
| `fp_productos` | Array productos |
| `fp_ventas` | Array ventas |
| `fp_config` | nombre, tasa, rif, telefono |
| `fp_session` | shop, code, tipo, loginAt |
| `fp_licencias_generadas` | Licencias generadas admin |
| `fp_demo_activated_[btoa]` | Timestamp activación demo |
| `fp_caja_apertura` | Apertura activa |
| `fp_caja_cierres` | Historial cierres |
| `fp_clientes` | Clientes y fiados |
| `fp_proveedores` | Proveedores |
| `fp_pagos_proveedores` | Pagos a proveedores |
| `fp_devoluciones` | Devoluciones registradas |

---

## 🔑 FUNCIONES CLAVE

| Función | Línea aprox. | Descripción |
|---|---|---|
| `showPage(page,el)` | ~1046 | Navega entre páginas |
| `renderInventario()` | ~1100 | Renderiza inventario |
| `procesarVenta()` | ~1350 | Procesa venta POS |
| `abrirCobro()` | ~1300 | Abre modal cobro |
| `abrirCaja()` | ~1700 | Apertura caja |
| `cerrarCaja()` | ~1750 | Cierre caja |
| `abrirCobroRapido()` | ~2200 | ⚡ Cobro sin registrar |
| `renderClientes()` | ~2500 | Módulo clientes/fiados |
| `renderProveedores()` | ~2700 | Módulo proveedores |
| `renderDevoluciones()` | ~2400 | Módulo devoluciones |
| `abrirEtiquetas()` | ~2870 | Modal etiquetas |
| `imprimirEtiquetas()` | ~2900 | Imprime con tamaño |
| `generarLicencia()` | ~1900 | Genera licencia PRO |
| `generarLicenciaDemo()` | ~1930 | Genera demo 5 días |

---

## 💳 MÉTODOS DE PAGO

USD: Efectivo $, Zelle, Binance Pay, Otras Divisas
Bs: Efectivo Bs, Pago Móvil, Transferencia Bs, Débito, Crédito
Especiales: Fiado, Pago Mixto

---

## 📤 REPO GITHUB

- **Repo:** `tiendadigitalaipro/fruteria-pro`
- **Branch:** `master` ⚠️ (NO main)
- **Local:** `C:\Users\ASUS\Downloads\fruteria-pro\`

```bash
cd "C:\Users\ASUS\Downloads\fruteria-pro"
git add fruteria-pro.html
git commit -m "descripción"
git push origin master
```

---

## ⚠️ REGLAS PARA CLAUDE

1. Lee este archivo PRIMERO — no abrir el HTML completo
2. Usa `Read` solo en el rango de líneas necesario
3. Usa `Grep` para buscar funciones exactas
4. Push siempre a `master` (no `main`)
5. Ver SKILLS-SEGURIDAD.md para Iron Lock
6. Ver ERRORES-CONOCIDOS.md antes de corregir bugs
7. NUNCA reducir funcionalidades existentes

---

*Actualizado: 2026-03-26 · Fruteria Pro v3.0 · A2K Digital Studio*
