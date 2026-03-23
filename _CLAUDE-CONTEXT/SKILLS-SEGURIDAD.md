# 🔐 SKILLS-SEGURIDAD — Licencias y Acceso

## FruteriaPro — Licencias hardcodeadas

| Código | Tipo | Vence |
|--------|------|-------|
| `FP-ADMIN-2026` | ADMIN | 2027-12-31 |
| `FP-PRO-ZYNC`   | PRO   | 2027-12-31 |
| `FP-DEMO-2026`  | DEMO  | 2026-12-31 |

**Licencia admin principal:** `FP-ADMIN-2026`

## Sesión
- Clave localStorage: `fp_session`
- Campos: `{ shop, code, tipo, loginAt }`
- Para cerrar sesión: `localStorage.removeItem('fp_session')` + `location.reload()`

## Licencias dinámicas (v2.0)

- El admin puede generar licencias PRO y DEMO desde ⚙️ Configuración → 🔑 Gestión de Licencias
- Se guardan en localStorage: `fp_licencias_generadas` (array)
- Formato PRO: `FP-PRO-[6 chars]` | Formato DEMO: `FP-DEMO-[6 chars]`
- El `validarLicencia()` busca primero en hardcoded, luego en `fp_licencias_generadas`

### Lógica de DEMO (5 días — protección triple)

**Paso 1 — Registro de activación (primer login con DEMO generada):**
- Clave: `fp_demo_activated_[btoa(code)]`
- Valor: `btoa(JSON.stringify({ ts: Date.now(), h: ((ts*1234567891)%999983).toString(36) }))`

**Paso 2 — Verificación en cada carga:**
- Decodifica con `atob()` y valida hash de integridad
- Si `Date.now() - ts >= 432000000` ms (5 días exactos) → `showDemoBlock()`
- Si el hash no coincide (posible manipulación) → `showDemoBlock()`

**Paso 3 — Verificación con servidor:**
- `fetch('https://worldtimeapi.org/api/timezone/America/Caracas')` con timeout
- Si el servidor dice que han pasado 5 días → `showDemoBlock()`
- Si falla el fetch (sin internet) → confía en localStorage

**Re-check continuo:**
- `setInterval(checkDemoExpiry, 60000)` — verifica cada minuto mientras la app está abierta

### Overlay de bloqueo `#demoBlock`
- `position: fixed; inset: 0; z-index: 999999`
- Sin botón X, sin cierre por ESC, bloquea scroll (`document.body.style.overflow='hidden'`)
- Mensaje: "⏰ Tu período de prueba de 5 días ha finalizado"
- Botón único: "💬 Contactar para adquirir PRO" → WhatsApp de ZYNC
- La DEMO estática `FP-DEMO-2026` usa su fecha de vencimiento `2026-12-31` (sin timer de 5 días)

### Badge regresiva en topbar
- Elemento: `<span id="demo-badge" class="demo-badge">`
- Texto: `⏳ Demo: Xd Xh Xm restantes`
- Actualización: `setInterval` cada 60 segundos

## Datos protegidos en localStorage
- `fp_productos` — catálogo de productos
- `fp_ventas` — historial de ventas
- `fp_config` — configuración de tienda
- `fp_licencias_generadas` — licencias emitidas por el admin
- `fp_caja_apertura` — turno de caja activo
- `fp_caja_cierres` — historial de cierres
- NUNCA eliminar estas claves sin exportar backup primero

## Reset de emergencia
- Abrir consola F12 y ejecutar: `localStorage.clear(); location.reload()`
- Esto borra TODOS los datos — hacer backup primero

## Notas
- Sin Firebase, funciona 100% offline
- Validación en frontend (hardcoded + localStorage generadas)
- z-index del loginScreen: 99999
- z-index del demoBlock: 999999
