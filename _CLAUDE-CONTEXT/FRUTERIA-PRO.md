# 🍃 FRUTERIA-PRO — LEE ESTE ARCHIVO PRIMERO

## Descripción del Proyecto
FruteriaPro es un sistema POS (Punto de Venta) completo para fruterías y verduleras.
Funciona 100% offline — sin servidor, sin Firebase, sin conexión a internet requerida.
**Versión actual: v2.0**

---

## Ruta Principal
```
C:\Users\ASUS\Downloads\fruteria-pro\fruteria-pro.html
```

## Archivos
| Archivo | Descripción |
|---------|-------------|
| `fruteria-pro.html` | Aplicación completa (único archivo, ~2137 líneas en v2.0) |
| `ABRIR-FRUTERIA.bat` | Abre la app en el navegador con doble clic |

## Cómo Abrir
- **Opción 1:** Doble clic en `ABRIR-FRUTERIA.bat`
- **Opción 2:** Doble clic en `fruteria-pro.html` directamente
- **No necesita servidor** — abre directo en el navegador

---

## Tecnología
- HTML + CSS + JavaScript puro (sin frameworks)
- Sin dependencias externas
- Datos guardados en `localStorage` del navegador (clave prefijo: `fp_`)
- Sin Firebase, sin backend, sin internet

---

## Categorías y Productos (74 total)

| Categoría | Productos | Cantidad |
|-----------|-----------|----------|
| 🍉 Frutas Tropicales | Cambur, Piña, Mango, Melón, Patilla, Coco, Durazno, Cerezas, Arándanos, Fresas, Uvas, Naranja, Limón, Lima, Manzana Roja, Manzana Verde, Pera, Aceituna, Tomate, Pimentón, Ají, Aguacate, Berenjena, Maíz, Kiwi, Mora, Tamarindo, Melocotón, Mandarina, Toronja, Guanábana, Guayaba, Lechosa/Papaya, Plátano Macho, Parchita | 35 |
| 🥦 Verduras y Hortalizas | Brócoli, Lechuga, Repollo, Cilantro, Perejil, Cebolla, Ajo, Zanahoria, Apio, Pepino, Vainita, Espinaca, Ensalada Mixta, Remolacha, Batata, Papa, Celery, Coliflor, Arvejas, Puerro, Albahaca, Hierbabuena, Tomillo, Orégano, Romero | 25 |
| 🍠 Tubérculos y Raíces | Yuca, Ocumo, Mapuey, Papa Criolla, Rábano, Cebollín, Nabo | 7 |
| 🫘 Granos y Semillas | Caraotas Negras, Frijoles, Lentejas, Arroz, Maíz Pilado, Garbanzos, Frijol Blanco | 7 |

---

## Moneda
- Precio base en **Dólares ($)**
- Conversión automática a **Bolívares (Bs)**
- Tasa configurable desde la app (botón 💱 arriba a la derecha)
- Tasa por defecto: 40 Bs/$

## Unidades de Medida
`kg`, `500g`, `250g`, `Unidad`, `Docena`, `Racimo`, `Bolsa`, `Caja`, `Litro`, `Manojo`

---

## Secciones del Sidebar (v2.0)

| Icono | Sección | Descripción |
|-------|---------|-------------|
| 📊 | **Dashboard** | KPIs, gráfico semanal, top 5, alertas |
| 🛒 | **Punto de Venta** | POS principal con carrito |
| 📦 | **Inventario** | Gestión de productos y stock |
| 📋 | **Historial** | Ventas registradas con filtros |
| 📊 | **Reportes** | Top productos, métodos de pago, stock |
| 🏧 | **Caja** | Apertura/cierre de turno + declaración |
| ⚙️ | **Configuración** | Datos tienda, tasa, licencias |

---

## Funcionalidades v2.0

### POS y Ventas
- ✅ Punto de Venta (POS) con carrito de compras
- ✅ Búsqueda de productos en tiempo real
- ✅ Filtro por categoría
- ✅ Agregar/editar/eliminar productos
- ✅ Control de inventario con alertas de stock mínimo
- ✅ Descuentos por venta
- ✅ **10 métodos de pago** (ver tabla abajo)
- ✅ **Pago Mixto**: divide el cobro entre 2 métodos con montos individuales
- ✅ Cálculo automático de vuelto
- ✅ Historial de ventas con filtros por fecha y método
- ✅ Ajuste de stock (+/- / establecer)
- ✅ Exportar historial en CSV
- ✅ Backup de datos en JSON
- ✅ Imprimir recibo

### Módulos nuevos (v2.0)
- ✅ **Dashboard** con 6 KPIs, gráfico de barras CSS 7 días, top 5 productos, alertas
- ✅ **Módulo de Caja**: apertura con billetes opcionales, cierre con diferencia sobrante/faltante, declaración imprimible
- ✅ **Generador de Licencias** en Configuración: PRO (vencimiento seleccionable) y DEMO (5 días exactos)
- ✅ **Protección DEMO** triple: hash de integridad + worldtimeapi.org + re-check cada minuto
- ✅ **Overlay de bloqueo** al vencer DEMO (fullscreen, z-index 999999, sin X ni ESC)
- ✅ **Badge regresiva** en topbar para licencias DEMO activas
- ✅ Configuración de tienda (nombre, dirección, teléfono, RIF)
- ✅ Sidebar colapsable
- ✅ 100% responsive (móvil/tablet/desktop)

---

## Métodos de Pago (v2.0 — 10 métodos)

| ID | Nombre | Moneda |
|----|--------|--------|
| `efectivo_usd` | 💵 Efectivo USD | USD |
| `efectivo_bs` | 💴 Efectivo Bs | BS |
| `pago_movil` | 📱 Pago Móvil | BS |
| `zelle` | 💙 Zelle | USD |
| `binance` | 🟡 Binance Pay | USDT |
| `transferencia` | 🏦 Transferencia | BS |
| `debito` | 💳 Débito | BS |
| `credito` | 💳 Crédito | BS |
| `divisas` | 💶 Otras Divisas | USD |
| `mixto` | 🔀 Pago Mixto | MIXTO |

---

## Módulo de Caja — Flujo

1. **Apertura**: Responsable + monto inicial $ y Bs + desglose billetes opcional → guarda en `fp_caja_apertura`
2. **Durante turno**: todas las ventas desde la fecha/hora de apertura se contabilizan
3. **Cierre**: muestra resumen por método, campo contado físico, diferencia = contado − esperado
4. **Declaración**: HTML imprimible con tabla de métodos, totales, firma cajero/supervisor → `window.print()`
5. Historial de cierres guardado en `fp_caja_cierres`

---

## Dashboard — Indicadores

| KPI | Fuente |
|-----|--------|
| 💰 Ventas hoy ($/Bs) | `fp_ventas` filtrado por fecha de hoy |
| 📦 Stock bajo/agotado | `fp_productos` donde `stock <= stockMin` |
| 🛒 Transacciones hoy | conteo de ventas del día |
| 💳 Método más usado hoy | moda de `venta.metodo` del día |
| 📈 Producto más vendido hoy | suma de `item.qty` por nombre del día |
| 🏧 Estado de caja | existe `fp_caja_apertura` en localStorage |

---

## Generador de Licencias — Flujo

- Acceso: `⚙️ Configuración → 🔑 Gestión de Licencias`
- **PRO**: nombre cliente + duración → genera `FP-PRO-[RANDOM6]` → copia + guarda en `fp_licencias_generadas`
- **DEMO**: auto-genera `FP-DEMO-[RANDOM6]` → timer 5 días desde primer uso → guarda en `fp_licencias_generadas`
- El `validarLicencia()` busca en hardcoded primero, luego en `fp_licencias_generadas`
- Ver `SKILLS-SEGURIDAD.md` para detalle de la lógica DEMO y protección triple

---

## Para Claude — Contexto Técnico

### localStorage keys completas (v2.0)
| Clave | Contenido |
|-------|-----------|
| `fp_productos` | Array de productos |
| `fp_ventas` | Array de ventas (objetos con metodo, metodoId, metodoMixto) |
| `fp_config` | `{ nombre, direccion, telefono, rif, tasa, moneda }` |
| `fp_session` | `{ shop, code, tipo, loginAt }` |
| `fp_licencias_generadas` | Array de licencias generadas por el admin |
| `fp_demo_activated_[btoa(code)]` | `btoa({ ts, h })` — timestamp de activación DEMO |
| `fp_caja_apertura` | Objeto de apertura activa (null si cerrada) |
| `fp_caja_cierres` | Array histórico de cierres de caja |

### Notas técnicas
- **Archivo único**: toda la lógica CSS+HTML+JS está en `fruteria-pro.html`
- **No hay build process**: editar el HTML directamente
- **Para agregar productos**: editar el array `PRODUCTOS_DEFAULT` en el `<script>`
- **Para agregar categorías**: editar el array `CATEGORIAS` y agregar productos correspondientes
- **Para cambiar colores**: modificar las variables CSS en `:root { ... }`
- **Venta mixto**: `venta.metodo` = label legible, `venta.metodoId` = id interno, `venta.metodoMixto` = `{ m1, a1, m2, a2 }`
- **Print CSS**: `@media print` oculta todo excepto `#receipt-content` (recibo) o `#caja-declaracion` (cierre caja)

---

## Diseño
- Colores: Verde oscuro (#1b4332) sidebar + naranja (#f77f00) acento
- Fondo: Tonos verdes suaves (#f0f7f0)
- Tarjetas de productos con emojis grandes
- Estilo supermercado moderno, limpio y fresco
