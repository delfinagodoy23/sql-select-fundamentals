# sql-select-fundamentals

Este repositorio contiene consultas SQL básicas realizadas sobre la tabla sales de TechStore. El objetivo de la práctica es utilizar SELECT, seleccionar columnas específicas y aplicar alias con AS para presentar los datos de una forma más clara para el equipo de finanzas.

¿Por qué es mala práctica usar SELECT * en producción?

Aunque SELECT * puede ser útil durante la exploración inicial de una tabla, no suele ser recomendable en ambientes de producción. Una de las razones es el rendimiento. Si una tabla tiene muchas columnas, SELECT * recupera información que quizás no sea necesaria para el análisis. Esto puede aumentar el volumen de datos transferidos y consumir más recursos de la base de datos.
También afecta la mantenibilidad. Si en el futuro se agregan nuevas columnas a la tabla, una consulta con SELECT * comenzará a devolverlas automáticamente aunque el reporte no las necesite. En cambio, seleccionar explícitamente las columnas permite saber exactamente qué información utiliza la consulta. Otro aspecto importante es la seguridad. Una tabla podría incorporar posteriormente información sensible que no debería formar parte de un reporte. Si utilizamos SELECT *, esa información podría aparecer automáticamente en los resultados.

Por ejemplo, en lugar de:

SELECT *
FROM sales;

para un reporte de finanzas es preferible solicitar únicamente la información necesaria:

SELECT
    customer_id,
    product_id,
    total_amount
FROM sales;

¿Por qué son importantes los alias para un stakeholder no técnico?

Los nombres utilizados dentro de una base de datos suelen estar pensados para desarrolladores o analistas y no necesariamente para usuarios de negocio. Los alias permiten cambiar temporalmente el nombre de una columna en el resultado de una consulta sin modificar la estructura original de la tabla.

Por ejemplo:

SELECT
    total_amount AS monto_total
FROM sales;

La columna original se llama total_amount, pero para una persona del área de finanzas el nombre monto_total resulta más fácil de interpretar. De esta manera, los alias ayudan a que los resultados sean más claros, legibles y comprensibles para stakeholders que no necesitan conocer los nombres técnicos utilizados dentro de la base de datos.
