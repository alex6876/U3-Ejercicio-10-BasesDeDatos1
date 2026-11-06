# Modelo Relacional de Bases de Datos 10



## Descripción



Este documento detalla el esquema y la estructura del modelo relacional de bases de datos para un sistema de gestión de transporte y flotas, enfocado en el control de vehículos, mantenimientos, talleres mecánicos, cargas de combustible, viajes, choferes y asignaciones de viaje.

---

## Estructura de Tablas y Atributos



### 1. Vehiculo



* **PK (Clave Primaria):** `id_Patente`


* **Atributos:**
* `Nro_Chasis`


* `Año_fabricación`


* `Marca`


* `Modelo`


* `Kilometraje_Actual`





### 2. Taller-Mecanico



* **PK (Clave Primaria):** `id_CUIT`


* **Atributos:**
* `nombre`


* `telefono`


* `especialidad`


* `direccion`





### 3. Mantenimiento



* **PK (Clave Primaria):** `id_Matenimiento`


* **Atributos:**
* `Tipo`


* `Fecha_ingreso`


* `descripción_trabajo`


* `Costo_Total`




* **FK (Claves Foráneas):**
* `id_CUIT` (asociado a la tabla Taller-Mecanico)


* `id_Patente` (asociado a la tabla Vehiculo)





### 4. Carga-de-combustible



* **PK (Clave Primaria):** `id_Carga`


* **Atributos:**
* `fecha`


* `litro_Cargados`


* `Costo_x_litros`


* `odometro`




* **FK (Claves Foráneas):**
* `id_Patente` (asociado a la tabla Vehiculo)





### 5. Viaje



* **PK (Clave Primaria):** `id_Viaje`


* **Atributos:**
* `Fecha_hora_salida`


* `Fecha_Hora_llegada`


* `Origen`


* `Destino`


* `Carga`




* **FK (Claves Foráneas):**
* `id_Patente` (asociado a la tabla Vehiculo)





### 6. Chofer



* **PK (Clave Primaria):** `id_Legajo`


* **Atributos:**
* `DNI`


* `nombre`


* `Fecha_nacimiento`


* `vencimiento_licencia`


* `Categoria_Licencia`





### 7. Asignación-viaje



* **PK (Clave Primaria):** `id_asignacion`


* **Atributos:**
* `observación`


* `Rol_Chofer`


* `Hora_confucción`




* **FK (Claves Foráneas):**
* `id_Viaje` (asociado a la tabla Viaje)


* `id_Legajo` (asociado a la tabla Chofer)





---

## Relaciones Principales



* **Vehiculo y Mantenimiento:** Un vehículo puede registrar múltiples mantenimientos realizados en talleres, vinculándose mediante la patente y el CUIT del taller.


* **Vehiculo y Carga-de-combustible:** Cada carga de combustible realizada se asocia a un vehículo específico a través de su `id_Patente`.


* **Vehiculo y Viaje:** Los viajes son ejecutados por vehículos identificados por su `id_Patente`.


* **Viaje y Chofer (Asignación-viaje):** La relación de muchos a muchos entre los viajes y los choferes se administra mediante la tabla intermedia `Asignación-viaje`, utilizando `id_Viaje` e `id_Legajo`.
