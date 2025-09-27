# prct02-AyD-BDD 

## Modelo entidad/relación. Farmacia

### Laboratorio
- **Código_lab** *(PK, entero)* → Identificador único del laboratorio.  
  Ej: `101`, `202`.
- **Nombre** *(texto)* → Nombre comercial del laboratorio.  
  Ej: `A`, `Farmacia Central`.
- **Teléfono** *(texto)* → Número de contacto.  
  Ej: `+34 555555555`.
- **Dirección** *(texto)* → Dirección postal completa.  
  Ej: `Calle Inventada 12, Canarias`.
- **Fax** *(texto)* → Número de fax.  
  Ej: `+34 555555555`.
- **Contacto** *(texto)* → Persona de contacto.  
  Ej: `Dr. Juan Pérez`.

---

### Medicamento
- **Código_med** *(PK, entero)* → Identificador único del medicamento.  
  Ej: `M001`, `M105`.
- **Nombre** *(texto)* → Nombre del medicamento.  
  Ej: `Paracetamol`, `Ibuprofeno`.
- **Tipo** *(texto)* → Forma de presentación.  
  Ej: `Jarabe`, `Comprimido`, `Pomada`.
- **Stock** *(entero)* → Unidades disponibles en almacén.  
  Ej: `120`.
- **Vendidos** *(entero)* → Unidades vendidas.  
  Ej: `300`.
- **Receta** *(bool)* → Indica si requiere receta médica.  
  Ej: `Sí`.

---

### Familia
- **Código_fam** *(PK, entero)* → Identificador de la familia.  
  Ej: `F01`, `F07`.
- **Nombre** *(texto)* → Nombre de la familia de medicamentos.  
  Ej: `Analgésicos`, `Antibióticos`.
- **Descripción** *(texto)* → Breve descripción del tipo de enfermedades que cubre.  
  Ej: `Medicamentos contra el dolor`.

---

### Cliente
- **Código_cli** *(PK, entero)* → Identificador del cliente.  
  Ej: `C001`, `C045`.
- **Nombre** *(texto)* → Nombre completo.  
  Ej: `María López`.
- **Dirección** *(texto)* → Dirección postal.  
  Ej: `Av. Falsa 15, Sevilla`.
- **Teléfono** *(texto)* → Número de contacto.  
  Ej: `+34 678901234`.
- **Crédito** *(booleano)* → Indica si el cliente compra con crédito.  
  Ej: `Sí`.

---

### Crédito (debil)
- **Código_cli** *(PK)* → Hereda del cliente.
- **Datos_bancarios** *(texto)* → IBAN o número de cuenta.  
  Ej: `ES55 5555 5555 5555 5555 5555`.
- **Fecha** *(fecha)* → Fecha de pago mensual de las compras.  
  Ej: `2025-09-27`.

---

### Compra
Entidad asociativa entre Cliente y Medicamento.  
- **Código_cli** *(PK)* → Cliente que realiza la compra.  
- **Cod_med** *(PK)* → Medicamento adquirido.  
- **Fecha_comp** 

## Relaciones definidas
###  Produce (Laboratorio – Medicamento)

- Un laboratorio → puede producir 0..N medicamentos.
- Un medicamento → es producido por 1 laboratorio.

Ejemplo: El laboratorio A produce el medicamento Ibuprofeno y también Paracetamol.

### Pertenece (Medicamento – Familia)

- Un medicamento → pertenece a 1 familia.
- Una familia → puede contener 0..N medicamentos.

Ejemplo: El medicamento Amoxicilina pertenece a la familia de Antibióticos.

### Lo compra (Cliente – Medicamento)

- Un cliente → puede comprar 0..N medicamentos.
- Un medicamento → puede ser comprado por 0..N clientes.

Ejemplo: El cliente Juan Pérez compra 2 Ibuprofenos y 1 Paracetamol el 15/09/2025.

4. Posee (Cliente – Crédito)

- Un cliente → puede tener 0..1 crédito.
- Un crédito → está asociado a 1 cliente.

Ejemplo: La cliente Ana posee un unico crédito, con datos bancarios y fecha de pago el 30 de cada mes.


