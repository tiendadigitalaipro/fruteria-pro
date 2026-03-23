# ⚠️ LEE ESTE ARCHIVO ANTES DE MODIFICAR SEGURIDAD

# Skills de Seguridad — FruteriaPro

## Protecciones implementadas en fruteria-pro.html

### 1. PIN de acceso (localStorage)
- La app puede tener un PIN de 4 dígitos configurable
- Guardado en localStorage como: fp_pin
- Para activarlo: buscar función checkPin() o setupPin()

### 2. Datos protegidos en localStorage
- fp_productos — catálogo de productos
- fp_ventas — historial de ventas
- fp_config — configuración de tienda
- fp_inventario — stock actual
- NUNCA eliminar estas claves sin exportar backup primero

### 3. Backup de seguridad
- Exportar backup: botón en Configuración → "Exportar JSON"
- Importar backup: Configuración → "Importar JSON"
- Hacer backup antes de cualquier modificación grande

### 4. Reset de emergencia
- Si la app queda bloqueada: abrir consola F12 y ejecutar:
  localStorage.clear(); location.reload();
- Esto borra TODOS los datos — hacer backup primero

## Errores de seguridad comunes

### ❌ Datos borrados al limpiar caché
- Causa: localStorage se borra con "Limpiar datos del sitio"
- Solución: Exportar backup JSON regularmente

### ❌ App bloqueada por PIN olvidado
- Solución: F12 → Console → localStorage.removeItem('fp_pin'); location.reload();

### ❌ Productos duplicados al importar backup
- Causa: Importar encima de datos existentes
- Solución: Hacer reset primero, luego importar
