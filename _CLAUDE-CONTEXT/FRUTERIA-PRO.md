# 🍃 FRUTERIA-PRO — LEE ESTE ARCHIVO PRIMERO

## Descripción del Proyecto
FruteriaPro es un sistema POS (Punto de Venta) completo para fruterías y verduleras.
Funciona 100% offline — sin servidor, sin Firebase, sin conexión a internet requerida.

---

## Ruta Principal
```
C:\Users\ASUS\Downloads\fruteria-pro\fruteria-pro.html
```

## Archivos
| Archivo | Descripción |
|---------|-------------|
| `fruteria-pro.html` | Aplicación completa (único archivo) |
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

## Funcionalidades
- ✅ Punto de Venta (POS) con carrito de compras
- ✅ Búsqueda de productos en tiempo real
- ✅ Filtro por categoría
- ✅ Agregar/editar/eliminar productos
- ✅ Control de inventario con alertas de stock mínimo
- ✅ Descuentos por venta
- ✅ Múltiples métodos de pago (Efectivo $, Bs, Pago Móvil, Zelle, Binance, Transferencia, Débito/Crédito, Mixto)
- ✅ Cálculo automático de vuelto
- ✅ Historial de ventas con filtros por fecha y método
- ✅ Ajuste de stock (+/- / establecer)
- ✅ Reportes: top productos, ventas por método, alertas de stock
- ✅ Exportar historial en CSV
- ✅ Backup de datos en JSON
- ✅ Imprimir recibo
- ✅ Configuración de tienda (nombre, dirección, teléfono, RIF)
- ✅ Sidebar colapsable
- ✅ 100% responsive (móvil/tablet/desktop)

---

## Métodos de Pago Disponibles
💵 Efectivo $ | 💴 Efectivo Bs | 📱 Pago Móvil | 🏦 Zelle | 🟡 Binance Pay | 🔄 Transferencia | 💳 Punto Débito/Crédito | 🔀 Mixto

---

## Diseño
- Colores: Verde oscuro (#1b4332) sidebar + naranja (#f77f00) acento
- Fondo: Tonos verdes suaves (#f0f7f0)
- Tarjetas de productos con emojis grandes
- Estilo supermercado moderno, limpio y fresco

---

## Errores Comunes y Soluciones

| Error | Solución |
|-------|---------|
| "No se encontraron productos" | Verifica el filtro de categoría o borra la búsqueda |
| Productos sin precio | Editar el producto desde Inventario |
| Datos perdidos al cambiar navegador | Los datos se guardan POR navegador en localStorage |
| App en blanco al abrir | Usa Chrome, Edge o Firefox (no IE) |
| Stock no baja al vender | Confirmar la venta completa con el botón verde del modal |
| La tasa no actualiza el carrito | Abrir/cerrar el modal de cobro para refrescar |

---

## Para Claude — Contexto Técnico
- **localStorage keys**: `fp_productos`, `fp_ventas`, `fp_config`
- **Archivo único**: toda la lógica CSS+HTML+JS está en `fruteria-pro.html`
- **No hay build process**: editar el HTML directamente
- **Para agregar productos**: editar el array `PRODUCTOS_DEFAULT` en el `<script>`
- **Para agregar categorías**: editar el array `CATEGORIAS` y agregar productos correspondientes
- **Para cambiar colores**: modificar las variables CSS en `:root { ... }`
