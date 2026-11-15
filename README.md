# VERBUM MIPYME DESARROLLO

**Gestión de inventario, ventas y clientes para microempresas · offline-first · HTML autónomo sin dependencias**

VERBUM Tech Solution · La Habana, Cuba · V1.0

## Descripción

Plataforma de gestión para microempresas en un único archivo `index.html`, sin frameworks ni dependencias externas. Funciona sin conexión y los datos se guardan solo en el dispositivo (localStorage).

### Módulos

- **Inicio**: métricas del negocio (valor del inventario, ventas del mes, cobrado, pendiente de cobro, stock bajo).
- **Inventario**: catálogo de productos con precios de compra y venta, control de stock con mínimo de alerta.
- **Ventas**: registro con líneas de productos, descuento automático de stock, medio de cobro (Efectivo, Transfermóvil, EnZona, Otro) y estado del cobro (cobrado/pendiente) con conciliación manual.
- **Clientes**: listado con pendiente de cobro acumulado por cliente.
- **Datos**: respaldo JSON con huella SHA-256, importación, impresión/PDF y borrado total con doble confirmación.
- **Bitácora**: registro automático de cada movimiento.
- **Config**: datos del negocio y diagnóstico del sistema.

## Estructura

```
/
├── index.html   # aplicación completa (autónoma)
└── README.md
```

## Publicación

Funciona en cualquier alojamiento de archivos estáticos.

**GitHub Pages**: activar Pages sobre la rama `main`, raíz `/`.

**Render** (sitio estático):
- Build command: (ninguno)
- Publish directory: `./`
- La URL pública de la app es el propio `index.html` servido en la raíz.

## Verificación de operatividad

Al ser un sitio estático no hay endpoint de servidor; la comprobación es que la URL responda HTTP 200 y cargue la aplicación:

- `GET /` → 200 y carga VERBUM MIPYME DESARROLLO
- Los datos se guardan localmente: un dispositivo no ve los datos de otro (privacidad por diseño).

## Notas

- Sin datos simulados: la app arranca vacía con datos reales del usuario.
- Los respaldos exportados no contienen credenciales.
