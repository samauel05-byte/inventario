# 📦 Control de Inventario

Programa de gestión de inventario para pequeños negocios. Funciona en el navegador (Chrome, Edge o Firefox), **sin instalar nada y sin internet**.

## Contenido de la carpeta

```
inventario/
├── index.html      ← EL PROGRAMA (ábrelo con doble clic)
├── lib/            ← librerías para exportar a Excel y PDF (no las borres)
├── ejemplos/       ← archivo de ejemplo para importar (inventario de un colmado)
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

## Primera vez

El programa arranca **en blanco**, sin productos ni movimientos. Empieza creando tu primer producto (ver abajo).

Si antes lo abriste en ese navegador y quedaron datos de prueba, pulsa **🗑 Borrar todo** (arriba a la derecha) para dejarlo vacío.

## Importar productos desde Excel o CSV

En la pestaña **Productos**, pulsa **⬆ Importar productos** y elige un archivo `.xlsx` o `.csv`.

- La primera fila debe tener los nombres de las columnas: **Descripción**, **Cantidad**, **Costo** (obligatorias), y **Precio de venta** y **Aviso de existencia baja** (opcionales). El programa reconoce también nombres parecidos como *Producto*, *Existencia* o *Costo unitario*.
- Pulsa **Plantilla** para descargar un Excel vacío con las columnas correctas.
- **El archivo funciona como base de datos**: los productos nuevos se crean (con su código automático) y los que ya existen, con la misma descripción, se **actualizan** con la cantidad, el costo, el precio y el aviso del archivo. Si dejas vacío el precio o el aviso, se conserva el que ya tenía el producto.
- Antes de importar, el programa te muestra cuántos productos son nuevos, cuántos se actualizarán y cuáles se omiten (cantidad o costo inválidos, o descripción repetida dentro del archivo).
- Importar **reemplaza** las cantidades de los productos existentes por las del archivo. Si registraste ventas o compras después de generar el archivo, esas cantidades se pisan: usa la importación para cargas iniciales o para ajustes de inventario.

### Archivo de ejemplo: inventario de un colmado

En `ejemplos/inventario_colmado.xlsx` hay un inventario de ejemplo con 68 productos típicos de un colmado (granos, enlatados, bebidas, higiene, etc.), con precios referenciales en pesos dominicanos. Impórtalo para probar el programa y bórralo con **🗑 Borrar todo** cuando quieras empezar con tus datos reales. En la versión publicada lo puedes descargar en `/ejemplos/inventario_colmado.xlsx`.

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
