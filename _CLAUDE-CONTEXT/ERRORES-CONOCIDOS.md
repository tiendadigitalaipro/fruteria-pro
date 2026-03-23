# ⚠️ ERRORES CONOCIDOS — FruteriaPro

## v2.0 — Módulos nuevos

### Dashboard
| Problema | Solución |
|----------|---------|
| KPIs muestran $0.00 al abrir | Es normal si no hay ventas del día; los datos se cargan de `fp_ventas` |
| Gráfico de barras no aparece | Verificar que el div `#dash-barchart` esté en el DOM (page-dashboard activo) |
| Top 5 vacío con ventas del día | Las ventas deben tener `fecha` que inicie con la fecha de hoy en ISO |

### Módulo de Caja
| Problema | Solución |
|----------|---------|
| Botón "Abrir Caja" no responde | Verifica que no haya ya una caja abierta en localStorage `fp_caja_apertura` |
| Declaración de cierre no imprime | `window.print()` puede estar bloqueado; revisar permisos del navegador |
| Resumen del turno no incluye ventas recientes | El filtro usa `new Date(venta.fecha) >= new Date(apertura.fecha)`; revisar zonas horarias |
| "Caja cerrada" aparece aunque esté abierta | Refrescar la página; `renderCaja()` lee de localStorage directamente |

### Métodos de pago (10 métodos)
| Problema | Solución |
|----------|---------|
| Pago Mixto no muestra panel | Verificar que `selPago('mixto', el)` active `#mixto-panel` con `display:block` |
| Historial muestra ID en vez de nombre | `venta.metodo` guarda el label con emoji; `venta.metodoId` guarda el ID interno |
| Filtro de historial no filtra Mixto | Usar opción "🔀 Pago Mixto" — busca `venta.metodo.startsWith('🔀')` |

### Generador de Licencias
| Problema | Solución |
|----------|---------|
| Licencia PRO generada no funciona al login | `validarLicencia()` busca en `fp_licencias_generadas`; verificar que se guardó correctamente |
| DEMO generada no bloquea al vencer | Verificar clave `fp_demo_activated_[btoa(code)]` en localStorage |
| Timer DEMO incorrecto tras cambiar fecha del sistema | `worldtimeapi.org` detecta manipulación de fecha local si hay internet |
| Modal PRO no muestra resultado | `gel('lic-pro-form').style.display='none'` debe ejecutarse en `generarLicPro()` |

### Protección DEMO
| Problema | Solución |
|----------|---------|
| Overlay `#demoBlock` no aparece al vencer | `checkDemoExpiry()` debe llamarse en `DOMContentLoaded` + cada 60 segundos |
| Badge de countdown no se ve | `#demo-badge` inicia con `display:none`; solo aparece si el usuario tiene DEMO activa |
| ESC cierra el overlay | El listener de ESC en `showDemoBlock()` usa `e.preventDefault()` + `capture:true` |
| DEMO estática `FP-DEMO-2026` no bloquea antes de diciembre | Solo se bloquea si `new Date(lic.vence) < new Date()`; antes de esa fecha es válida |

## v1.0 — Problemas base

| Error | Solución |
|-------|---------|
| "No se encontraron productos" | Verifica el filtro de categoría o borra la búsqueda |
| Productos sin precio | Editar el producto desde Inventario |
| Datos perdidos al cambiar navegador | Los datos se guardan POR navegador en localStorage |
| App en blanco al abrir | Usa Chrome, Edge o Firefox (no IE) |
| Stock no baja al vender | Confirmar la venta completa con el botón verde del modal |
| La tasa no actualiza el carrito | Abrir/cerrar el modal de cobro para refrescar |
| Datos borrados al limpiar caché | Exportar backup JSON regularmente desde Configuración |
