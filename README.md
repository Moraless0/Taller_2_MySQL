# Librería El Mundo de Sofía

Este repositorio contiene el diseño de una base de datos para la gestión de inventario, ventas y clientes de una tienda de libros.

## ¿Qué hay aquí?

- **`Script_Libreria_Sofia.sql`**: script SQL listo para crear la base de datos `libreria_sofia`, sus tablas, relaciones, índices y restricciones en MySQL.
- **`Documentacion_Libreria_Sofia.pdf`**: documento con la explicación del diseño, las decisiones tomadas y las relaciones entre entidades.
- **`DIAGRAMA.png`**: diagrama UML E-R del modelo de datos.

## Diseño de la base de datos

La base de datos está organizada en torno a siete tablas principales:

- **autor**: guarda la información de los autores.
- **editorial**: catálogo de editoriales.
- **categoria**: clasificación de los libros.
- **libro**: registra los libros con su ISBN, título, precio y stock.
- **libro_autor**: tabla intermedia que permite que un libro tenga varios autores y un autor haya escrito varios libros.
- **cliente**: datos de los clientes registrados.
- **direccion**: direcciones asociadas a cada cliente, separadas para soportar múltiples envíos.
- **pedido**: cabecera de cada compra, con su estado, cliente y dirección de entrega.
- **detalle_pedido**: líneas del pedido, con los libros y cantidades compradas.
- **transaccion**: pago asociado a cada pedido, incluyendo método, monto y estado.

## Cómo ejecutar el script

1. Abrir MySQL Workbench o la terminal de MySQL.
2. Ejecutar el archivo `Script_Libreria_Sofia.sql`:

   ```bash
   mysql -u usuario -p < Script_Libreria_Sofia.sql
   ```

   O abrirlo directamente en MySQL Workbench y correrlo con el botón de ejecución.

3. La base de datos `libreria_sofia` se creará y estará lista para usarse.

## Algunas decisiones del diseño

- El ISBN es único por libro para evitar duplicados en el catálogo.
- El stock de cada libro se controla en la tabla `libro`, lo que permite luego implementar fácilmente la actualización automática al confirmar una venta.
- Los pedidos tienen un campo `estado` con valores como *pendiente*, *procesado*, *completado* o *cancelado* para seguir el flujo de la compra.
- Cada pedido genera una única transacción, lo que mantiene clara la relación entre venta y pago.
- Las direcciones están en su propia tabla porque un cliente puede tener más de una dirección de envío.

## Relación entre archivos

- El **diagrama** muestra de forma visual las entidades, atributos y relaciones.
- El **PDF** profundiza en la justificación del diseño, las restricciones y la representación UML.
- El **script SQL** es la implementación concreta del modelo en MySQL.

## Autor

Henry Morales
