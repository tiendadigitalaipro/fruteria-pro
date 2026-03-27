# 🔒 SKILLS SEGURIDAD — Fruteria Pro Iron Lock

---

## 🛡️ ESTRUCTURA DE PROTECCIÓN

```
#loginScreen   → pantalla licencia (display:flex por defecto)
#app           → oculto hasta validar (display:none)
#demoBlock     → overlay fullscreen al vencer demo (z-index: 999999)
```

---

## 🔑 CÓDIGOS MASTER (hardcodeados)

```
FPRO-DEMO-2024   → Master demo
FPRO-ABIG-2024   → Master PRO
FPRO-ZYNC-2024   → Master PRO alternativo
FP-ADMIN-2026    → Admin original
FP-PRO-ZYNC      → PRO original
FP-DEMO-2026     → Demo estática (vence 2026-12-31)
```

---

## ⏱️ SISTEMA DEMO — 5 DÍAS EXACTOS

```javascript
vence.setDate(vd.getDate() + 5)  // ← NO CAMBIAR NUNCA
```

**Storage:**
```
fp_demo_activated_[btoa(code)] = btoa({ ts: Date.now(), h: hash })
```

**Verificación triple:**
1. Hash de integridad local
2. worldtimeapi.org si hay internet
3. Re-check `setInterval(checkDemoExpiry, 60000)` cada minuto

---

## 🔑 LICENCIAS GENERADAS

**Formato:**
```
PRO:  FP-PRO-[RANDOM6]
DEMO: FP-DEMO-[RANDOM6]
```

**Storage:** `fp_licencias_generadas` (array)

**Funciones:**
```javascript
generarLicencia()      // PRO con duración seleccionable
generarLicenciaDemo()  // DEMO 5 días fijos
activarConCodigoPro()  // Activa en el dispositivo actual
```

---

## 🪟 Z-INDEX STACK

```
999999 → #demoBlock
 99999 → #loginScreen
  9999 → modales dinámicos (modalEtiquetas, modalCobroRapido)
  1000 → .modal-overlay
```

---

## 🚨 REGLAS DE ORO

1. NUNCA cambiar `+ 5` en el timer demo
2. NUNCA modificar los códigos MASTER
3. NUNCA agregar botón de cierre al `#demoBlock`
4. NUNCA hacer bypass del loginScreen

---

## 🔐 CONTRASEÑA ADMIN

- Se solicita en Configuración → Gestión de Licencias
- Buscar `adminPwOkBtn` (~línea 830) para encontrarla en el código
- No exponer en logs ni commits

---

## 🔄 RESET DE EMERGENCIA

```javascript
// En consola F12 del navegador:
localStorage.clear(); location.reload();
// ⚠️ Borra TODOS los datos — exportar backup JSON primero
```

---

*Actualizado: 2026-03-26 · A2K Digital Studio*
