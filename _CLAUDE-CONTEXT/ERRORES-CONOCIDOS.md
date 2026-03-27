# ⚠️ ERRORES CONOCIDOS — Fruteria Pro

> Lee ANTES de intentar corregir bugs para no repetir trabajo ya hecho.

---

## ✅ RESUELTOS

### Etiquetas no respetaban tamaño (v3.0)
- **Causa:** `imprimirEtiquetas()` no leía el select de tamaño
- **Fix:** `szMap` con dimensiones + `onchange="renderEtiquetasPreview()"` al select
- **Commit:** `5406453`

### Cobro Rápido sin soporte Bs
- **Fix:** Modal con selector USD/Bs y conversión con `STATE.tasa`

### Módulos Clientes, Proveedores, Devoluciones faltaban
- **Fix:** Agregados con lógica completa — commit `edf9458`

---

## 🔴 A VIGILAR

### Claves localStorage mezcladas
- Algunos accesos usan `DB.get('clientes')` sin prefijo `fp_`
- **Correcto:** `DB.get('fp_clientes')` o la clave que defina cada módulo
- Verificar consistencia si un módulo no carga datos

### Iron Lock reforzado puede duplicar validación
- Parche FPRO ejecuta después del sistema original
- **Síntoma conflicto:** Loop de login o modal que no cierra
- **Fix:** Revisar que `validarLicencia()` no se llame dos veces

### Push siempre a `master` no `main`
- `git push origin main` falla en este repo
- **Siempre usar:** `git push origin master`

### Modal Etiquetas es dinámico
- `#modalEtiquetas` se crea en `abrirEtiquetas()`, no existe en HTML inicial
- No llamar `openModal('modalEtiquetas')` directamente

---

## 🟡 COMPORTAMIENTOS NORMALES (no son bugs)

- KPIs en $0 al abrir sin ventas del día → normal
- Sidebar colapsado en móvil → responsive CSS
- Tasa por defecto 40 Bs/$ → configurar en app
- Demo vence exactamente 5 días → no es configurable
- Datos se borran si el usuario limpia el navegador → localStorage limitación

---

## 🔵 BUGS DASHBOARD (v2.0, aún vigentes)

| Problema | Solución |
|---|---|
| Gráfico barras no aparece | `#dash-barchart` debe estar activo en DOM |
| Top 5 vacío con ventas | `venta.fecha` debe iniciar con fecha ISO de hoy |
| Estado caja incorrecto | Refrescar página, `renderCaja()` lee localStorage directo |

---

## 🔵 BUGS CAJA

| Problema | Solución |
|---|---|
| "Abrir Caja" no responde | Ya hay caja abierta en `fp_caja_apertura` |
| Declaración no imprime | `window.print()` bloqueado en el navegador |
| Ventas no aparecen en resumen | Revisar zona horaria en `new Date(venta.fecha)` |

---

*Actualizado: 2026-03-26*
