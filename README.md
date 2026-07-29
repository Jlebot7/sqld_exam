Justificación del Diseño de la Base de Datos
1. Integridad de Entidad y Dominio 🛡️
Para garantizar que la base de datos no reciba información incompleta o duplicada, se aplicaron restricciones estrictas en los campos clave:

Llaves Primarias (PK): Se definieron identificadores únicos como VIN para Vehículos, Client_ID para Clientes y Seller_ID para Vendedores.

Restricción UNIQUE: Aplicada a campos como el Phone y Email del cliente para evitar el registro múltiple de una misma persona en el sistema (CRM).

Restricción NOT NULL: Exigida en atributos operativos indispensables, asegurando que no existan registros "fantasma" (por ejemplo, todo vehículo debe tener marca, modelo y estado).

2. Exactitud Histórica y Financiera 💰
El diseño separa la información del inventario de la información transaccional para proteger los datos financieros en el tiempo:

Se creó una tabla intermedia Detalle_Venta que incluye el campo Discount.

La tabla Venta almacena los valores calculados al momento de la compra (Subtotal, Tax, Total). Esto "congela" los montos, garantizando que futuras actualizaciones en el precio de lista (Price) de la tabla Vehiculo no alteren el histórico contable.

3. Flexibilidad en las Reglas de Negocio ⚙️
El modelo se adapta a la realidad operativa del concesionario. En la tabla Mantenimiento, la llave foránea VIN es obligatoria (todo servicio requiere un auto), pero el Client_ID se dejó como opcional (permite valores nulos). Esto hace posible registrar mantenimientos internos a vehículos nuevos que aún no han sido vendidos.
