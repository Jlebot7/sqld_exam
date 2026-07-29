classDiagram
  class Vehiculo {
    +varchar(50) VIN {PK, UNIQUE}
    +varchar(30) Brand
    +varchar(40) Model
    +integer Year
    +varchar(30) Color
    +varchar(20) Fuel_type
    +varchar(10) Power
    +varchar(12) Transmission_Type
    +boolean Status
    +decimal Price
  }
