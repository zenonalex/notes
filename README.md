1- 
SOMA = 77

2- 
a) 9
b) 128
C) 49
d) 100
e) 13
f) 20

3-
```python
def calculate_revenue_statistics(daily_revenue):
    valid_revenue = [revenue for revenue in daily_revenue if revenue > 0]

    if not valid_revenue:
        return None, None, 0

    min_revenue = min(valid_revenue)
    max_revenue = max(valid_revenue)

    average_revenue = sum(valid_revenue) / len(valid_revenue)

    days_above_average = sum(1 for revenue in valid_revenue if revenue > average_revenue)

    return min_revenue, max_revenue, days_above_average

daily_revenue = [0, 1500, 2000, 0, 3000, 1000, 0, 4500, 0, 0, 1200, 800, 0, 0, 2500]

min_revenue, max_revenue, days_above_average = calculate_revenue_statistics(daily_revenue)

print(f"Lowest revenue: {min_revenue}")
print(f"Highest revenue: {max_revenue}")
print(f"Days with revenue above average: {days_above_average}")
```
4-
a)
Modelo Lógico do Banco de Dados:
- Tabela clients (Clientes):

  - id (PK): Identificador único do cliente.
  - name (Razão Social): Nome ou razão social do cliente.
  - state_id (FK): Chave estrangeira que referencia a tabela states (Estados).

- Tabela phones (Telefones):

  - id (PK): Identificador único do telefone.
  - client_id (FK): Chave estrangeira que referencia a tabela clients (Clientes).
  - phone_number: Número de telefone.
  - phone_type_id (FK): Chave estrangeira que referencia a tabela phone_types (Tipos de telefone).

- Tabela phone_types (Tipos de Telefone):

  - id (PK): Identificador único do tipo de telefone.
  - description: Descrição do tipo de telefone (comercial, residencial, celular, etc.).

- Tabela states (Estados):

  - id (PK): Identificador único do estado.
  - code: Código do estado (por exemplo, "SP" para São Paulo).
  - name: Nome completo do estado.

b)
| clients             | phones             | phone_types          | states             |
|---------------------|--------------------|----------------------|--------------------|
| id (PK)             | id (PK)            | id (PK)              | id (PK)            |
| name                | client_id (FK)     | description          | code               |
| state_id (FK)       | phone_number       |                      | name               |
|                     | phone_type_id (FK) |                      |                    |

c)
```sql
SELECT c.id AS client_id, 
       c.name AS client_name, 
       p.phone_number, 
       pt.description AS phone_type
FROM clients c
JOIN states s ON c.state_id = s.id
JOIN phones p ON c.id = p.client_id
JOIN phone_types pt ON p.phone_type_id = pt.id
WHERE s.code = 'SP';
```

5-
Como a soma das velocidades é 170 km/h, eles se encontrarão em aproximadamente 44 minutos. Nesse tempo, o carro terá percorrido cerca de 66,15 km e o caminhão, 58,8 km.

Embora o carro perca 15 minutos extras nos pedágios, isso não altera o ponto de encontro, mas apenas o momento. Quando se cruzarem, o caminhão estará mais próximo de Ribeirão Preto, pois percorreu uma distância menor (58,8 km) do que o carro (66,15 km).
