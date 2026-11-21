Guia Práctica Odoo: Préstamo de equipo

- Nombre: Alan Geovany Carranza Stevenson
- Número de cuenta: 0501200507001

## Respuestas

### Paso 1

1. Al desmarcar Activo, el equipo se oculta, pero no se elimina. Así no se pierde la información de los préstamos anteriores y se puede volver a activar.
2. copy=False evita que se copie el código de inventario al duplicar un equipo. Así cada equipo tiene su propio código.

### Paso 2

1. _name crea el modelo de préstamos. `_inherit = ["mail.thread"]` permite guardar mensajes y cambios en el historial.
2. tracking=True guarda los cambios del estado del préstamo y muestra quién los hizo y cuándo.

### Paso 3

1. "prestamo.linea" es el modelo donde están los equipos del préstamo. "prestamo_id" lo conecta con el préstamo correspondiente.
2. Sí, las líneas también se eliminan porque tienen ondelete="cascade".

### Paso 4

1. Ocultar un botón no es suficiente. También hay que revisar las condiciones en el código para evitar que alguien use el método sin cumplir las reglas.
2. prestamo.linea_ids.equipo_id obtiene todos los equipos del préstamo y write() permite cambiar su estado al mismo tiempo.

### Paso 5

1. El domain solo muestra los equipos disponibles al seleccionarlos. Pero hay que volver a revisar su estado cuando se confirma el préstamo.
2. @api.constrains revisa los datos al guardar. En cambio, action_prestar hace sus revisiones cuando se presiona el botón Prestar.

### Paso 6

1. Al mover una tarjeta en el kanban, puede cambiar el estado del equipo automáticamente, sin utilizar los botones.
2. No se crea una columna nueva en contactos. Odoo muestra los préstamos relacionados con ese contacto mediante el campo partner_id.