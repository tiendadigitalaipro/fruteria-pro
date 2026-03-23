# ⚠️ LEE ESTE ARCHIVO PRIMERO ANTES DE BUSCAR BUGS

# Errores Conocidos — FruteriaPro

## Stack tecnológico
- HTML5 puro + CSS3 + JavaScript vanilla
- Sin frameworks, sin dependencias externas
- Sin Firebase — funciona 100% offline
- localStorage para persistencia

## Cómo abrir la app
- Doble clic en ABRIR-FRUTERIA.bat
- O abrir fruteria-pro.html directo en el navegador
- No necesita servidor local (no hay Firebase Auth)

## Errores comunes y soluciones

### ❌ La app no carga / pantalla en blanco
- Causa: Error JavaScript al arrancar
- Diagnóstico: F12 → Console → buscar error en rojo
- Solución más común: localStorage corrupto → F12 → localStorage.clear(); location.reload();

### ❌ Los productos no se guardan
- Causa: localStorage lleno o bloqueado por el navegador
- Verificar: F12 → Application → Local Storage → buscar fp_productos
- Solución: Exportar datos, limpiar caché, reimportar

### ❌ El carrito no calcula bien en Bs
- Causa: La tasa de cambio no está configurada
- Solución: Ir a Configuración → actualizar tasa Bs/$

### ❌ Búsqueda no encuentra productos
- Causa: El producto está desactivado o con stock 0
- Solución: Ir a Inventario → verificar estado del producto

### ❌ No imprime el recibo correctamente
- Causa: Bloqueador de popups del navegador
- Solución: Permitir popups para este sitio

### ❌ Los emojis no se ven correctamente
- Causa: Fuente del sistema no soporta emojis
- Solución: Usar Chrome o Edge (mejor soporte de emojis)

## Archivos del proyecto
| Archivo | Función |
|---------|---------|
| fruteria-pro.html | APP COMPLETA — todo en un solo archivo |
| ABRIR-FRUTERIA.bat | Abre la app con doble clic |
| _CLAUDE-CONTEXT/ | Contexto para Claude — leer siempre primero |

## Estructura del código en fruteria-pro.html
- Líneas 1-XXX: HTML estructura y estilos CSS
- Líneas XXX-XXX: Datos de productos (PRODUCTS array)
- Líneas XXX-XXX: Lógica del carrito y POS
- Líneas XXX-XXX: Lógica de inventario
- Líneas XXX-XXX: Historial y reportes
- Líneas XXX-XXX: Configuración y backup
- Para encontrar una función: Ctrl+F y buscar "function nombreFuncion"
