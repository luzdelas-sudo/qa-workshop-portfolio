# Risk Matrix

## Nombre del Producto 
JpetStore Demo

## La matriz de Riesgo propuesta es la Siguiente

| ID | Riesgo | Impacto | Probabilidad | Nivel | Justificación |
|---|---|---|---|---|---|
| R1 | Validaccion de Stock existente al generar las compras, asi como un stock comprometido. | 5 | 4 | 20 | No avisa que los productos estan agotados, generando cobros indebidos, procesos de cancelación y demasiada insatisfacción por parte de los clientes. |
| R2 | Errores visible sin mensajes claros (Error 500 en pantalla de usuario). | 4 | 4 | 16 |  Obliga al usuario a definir nuevamente los productos que requiere comprar, pero tampoco deja completar la compra. Ya que no se completa el alta de usuario. |
| R3 | En el registro no estan indicados los valores requeridos | 3 | 4 | 12 | No hace facil la navegacion. Los probables compradores abandonan la compra para evitar el registro, por carecer de ayuda suficiente. |
| R4 | Inconsistencia de datos de inventario entre la API y la aplicación Web debido a la falta de sincronización en tiempo real. | 4 | 3 | 12 | Al ser dos sistemas independientes sin integración confirmada, los cambios realizados en la API pueden no verse reflejados en la interfaz Web, mostrando información falsa a los compradores. |
| R5 | Queda definido el ultimo valor por mas que se retorne al menu dificultando la navegacion. | 4 | 3 | 12 | Bloquea la captación de nuevos clientes en la plataforma, impidiéndoles avanzar hacia el proceso de pago y afectando directamente los ingresos del negocio. |