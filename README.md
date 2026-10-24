# 📦 Control de Inventario

Programa de gestión de inventario para pequeños negocios. Funciona en el navegador (Chrome, Edge o Firefox), **sin instalar nada y sin internet**.

## Contenido de la carpeta

```
inventario/
├── index.html      ← EL PROGRAMA (ábrelo con doble clic)
├── lib/            ← librerías para exportar a Excel y PDF (no las borres)
└── README.md       ← esta guía
```

## Instalación (2 pasos)

1. Descarga o copia **toda la carpeta `inventario`** a tu computadora (por ejemplo, al Escritorio). Mantén `index.html` y la carpeta `lib` juntos.
2. Haz **doble clic en `index.html`**. Se abrirá en tu navegador. ¡Listo!

> Opcional: haz clic derecho en `index.html` → *Enviar a → Escritorio (crear acceso directo)* para abrirlo más rápido.

## Importante: dónde se guardan tus datos

Los datos se guardan **permanentemente dentro del navegador** de ese computador. Eso significa:

- ✅ No se pierden al cerrar el programa ni al apagar la computadora.
- ⚠️ Usa siempre **el mismo navegador** y el mismo usuario de Windows/Mac. Si abres el programa en otro navegador, verás datos vacíos.
- ⚠️ Si borras los “datos del sitio/cookies” del navegador, se borra el inventario.
- 👉 **Haz un respaldo con frecuencia**: botón **⬇ Guardar respaldo** (arriba a la derecha). Guarda el archivo `.json` en un lugar seguro (USB, Drive). Para recuperarlo usa **⬆ Restaurar respaldo**.

## Productos de ejemplo

La primera vez que abres el programa vienen **5 productos de ejemplo** (con algunas ventas, una compra y cuentas de ejemplo) para que pruebes todo:

| Código | Producto | Costo | Precio |
|---|---|---|---|
| P-0001 | Arroz blanco 1 kg | 0,80 | 1,20 |
| P-0002 | Aceite de cocina 1 L | 2,50 | 3,60 |
| P-0003 | Azúcar 1 kg | 0,70 | 1,00 |
| P-0004 | Jabón de baño | 0,45 | 0,90 |
| P-0005 | Refresco 2 L | 1,10 | 1,75 |

Cuando termines de probar, pulsa **🗑 Borrar todo** (arriba a la derecha) para empezar con tu inventario real.

## Cómo crear tu primer producto

1. En la pestaña **Productos**, pulsa **+ Nuevo producto**.
2. Llena el formulario:
   - **Descripción**: por ejemplo `Harina de trigo 1 kg`.
   - **Cantidad inicial**: cuántas unidades tienes hoy (ej. `30`).
   - **Avisar si hay menos de**: el programa te alertará cuando la existencia llegue a ese número.
   - **Costo por unidad**: lo que te cuesta a ti (ej. `0.90`).
   - **Precio unitario de venta** (opcional): lo que cobras al cliente (ej. `1.40`). Si lo dejas vacío, el producto se guarda sin precio y podrás ponerlo después con *Editar*.
3. Pulsa **Guardar**. El producto recibe automáticamente su código (`P-0006`, `P-0007`…).

El programa **no te dejará** guardar si: hay campos vacíos, la cantidad es negativa, el precio, si lo escribes, no es válido (no puede ser negativo) o ya existe otro producto con la misma descripción.

## Cómo usar cada pestaña

**Productos**: lista con existencia, costo, precio, margen de ganancia, valor del inventario, valor de venta y lo que está por cobrar/pagar de cada producto. Arriba verás los totales y las **alertas de existencia baja** (también se marcan en naranja). Puedes **buscar**, **Editar** y **Eliminar** (siempre pide confirmación).

**Movimientos**:
- **Registrar entrada (compra)**: suma a la existencia. Si marcas *a crédito*, escribe el proveedor y se crea automáticamente una **cuenta por pagar**. El costo del producto se recalcula como promedio entre lo que tenías y lo que compraste.
- **Registrar salida (venta)**: resta de la existencia (no permite vender más de lo que hay). Si marcas *a crédito*, escribe el cliente y se crea una **cuenta por cobrar**.
- **Anular**: deshace un movimiento mal registrado.

**Cuentas por cobrar / Cuentas por pagar**: lista con cliente o proveedor, monto, fecha y estado (*Pendiente* / *Pagado*). Usa **Marcar como pagado** cuando se salde. También puedes crear cuentas manuales y filtrar por estado.

**Reporte**: tabla de todos los productos con totales (valor del inventario, total por cobrar, total por pagar y **balance neto = inventario + por cobrar − por pagar**), con fecha y hora de emisión. Botones: **Exportar a Excel (.xlsx)**, **Exportar a PDF** e **Imprimir**.

## Personalización rápida

- **Símbolo de moneda**: abre `index.html` con el Bloc de notas, busca `const MONEDA = '$';` y cámbialo (por ejemplo `'Bs'`, `'S/'`, `'€'`).
- El código está comentado en español y dividido en secciones (cálculos, productos, movimientos, cuentas, reporte, respaldo).

## Posibles mejoras futuras

- **Usuarios con contraseña** y permisos (por ejemplo, un empleado que solo registra ventas).
- **Códigos de barras**: lector USB o cámara del celular para buscar/vender escaneando.
- **Facturación**: facturas y recibos imprimibles con número correlativo, datos del cliente e impuestos.
- Base de datos en servidor o en la nube para usar el sistema desde varias computadoras y celulares.
- Abonos parciales en las cuentas, fechas de vencimiento y avisos de cuentas vencidas.
- Categorías y proveedores por producto, historial de precios y gráficos de ventas.
- Copias de seguridad automáticas.
