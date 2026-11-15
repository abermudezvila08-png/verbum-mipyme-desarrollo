# VERBUM MIPYME DESARROLLO

**Gestión de inventario, ventas y clientes para microempresas · PWA instalable · licencia con prueba de 30 días**

VERBUM Tech Solution · La Habana, Cuba · V1.1

## Descripción

Aplicación en un único archivo `index.html` (PWA sin dependencias externas). Funciona sin conexión, los datos se guardan solo en el dispositivo y se instala como app nativa en Android ("Añadir a pantalla de inicio" / "Instalar aplicación").

### Módulos

- **Inicio**: métricas (valor del inventario, ventas del mes, cobrado, pendiente de cobro, stock bajo).
- **Inventario**: productos con precios de compra/venta, stock y mínimo de alerta.
- **Ventas**: líneas de productos, descuento de stock, medio de cobro (Efectivo, Transfermóvil, EnZona, Otro), estado cobrado/pendiente.
- **Clientes**: pendiente de cobro acumulado por cliente.
- **Datos**: respaldo JSON con huella SHA-256, importación, impresión, borrado con doble confirmación.
- **Bitácora** y **Config** (con diagnóstico, licencia y código de dispositivo).

## Licenciamiento

- Al primer arranque se registra la instalación: **30 días de prueba**.
- Vencido el plazo, la app se bloquea y muestra el **código de dispositivo** (p. ej. `ABCD-EFGH`).
- El vendedor genera la **clave de activación** con un generador externo (no incluido en este repo): la clave es una función SHA-256 del secreto interno y del código del dispositivo, y queda **activa de forma permanente** para ese dispositivo.
- Los datos del cliente no se pierden al vencer la prueba; se reactivan al entrar la clave.
- Nota honesta: al ser HTML, el código es visible; la protección es práctica, no criptográficamente absoluta. Si el cliente borra los datos del navegador, la prueba reinicia (y también pierde sus datos, lo que desincentiva el truco).

## Estructura

```
/
├── index.html              # app completa (PWA + licenciamiento)
├── manifest.json           # manifiesto PWA
├── verbum-mipyme.sw.js     # service worker (caché offline)
├── icons/                  # iconos 192/512 + maskable
└── README.md
```

## Publicación

**Render** (sitio estático): build command vacío, publish directory `./`.

**Instalación en Android**: abrir la URL pública en Chrome → menú ⋮ → "Instalar aplicación" (o "Añadir a pantalla de inicio"). Aparece el icono VMD en el lanzador y corre a pantalla completa, sin barra del navegador.

## Verificación de operatividad

Sitio estático: `GET /` → 200 y carga la app; `GET /manifest.json` → 200; `GET /verbum-mipyme.sw.js` → 200.
