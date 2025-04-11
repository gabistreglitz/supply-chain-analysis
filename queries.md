# Métricas realizadas no PostgreSQL

## 1. Sazonalidade do faturamento ao longo do ano:
```sql
select
	to_char(order_date, 'Month') as mes_nome,
	sum(revenue_generated) as total_vendas
from orders
group by mes_nome
order by total_vendas desc;
```
Resultado da query:
```sql
"mes_nome"	"total_vendas"
"December "	78817.60
"March    "	62870.57
"April    "	59980.39
"August   "	53287.40
"May      "	50440.99
"July     "	43432.23
"February "	41774.67
"November "	40692.14
"January  "	39870.20
"June     "	38327.35
"September"	35443.70
"October  "	32667.62
```

## 2. Categoria dos produtos mais vendidos:
```sql
select
	p.product_type,
	sum(o.number_of_products_sold) as total_vendido
from products p
join orders o on p.sku = o.sku
group by p.product_type
order by total_vendido desc;
```
Resultado da query:
```sql
"product_type"	"total_vendido"
"skincare"	        20731
"haircare"	        13611
"cosmetics"	        11757
```
## 3. Fornecedor com maior volume de vendas:
```sql
with pedidos_por_fornecedor as(
select
	l.supplier_name,
	sum(o.number_of_products_sold) as total_pedidos
from logistics l
	join orders o on l.sku = o.sku
group by l.supplier_name
)

select * from pedidos_por_fornecedor
order by total_pedidos desc;
```
Resultado da query:
```sql
"supplier_name"	"total_pedidos"
"Supplier 1"	      11080
"Supplier 2"	      11068
"Supplier 5"	      8662
"Supplier 3"	      8083
"Supplier 4"	      7206
```

## 4. Produtos vendidos por cidade:
```sql
select
	l.location,
	sum(o.number_of_products_sold) as total_vendido
from logistics l
join orders o on l.sku = o.sku
group by l.location
order by total_vendido desc;
```
Resultado da query:
```sql
"location"	"total_vendido"
"Kolkata"	12770
"Delhi"	        9715
"Mumbai"	9426
"Chennai"	8768
"Bangalore"	5420
```

## 5. Relação dos produtos mais baratos com volume de vendas:
```sql
select
	p.sku,
	p.price,
	sum(o.number_of_products_sold) as total_vendido
from products p
	join orders o on p.sku = o.sku
group by p.sku
order by p.price
limit 10;
```
Resultado da query:
```sql
"sku"	"price"	"total_vendido"
"SKU5"	1.70	147
"SKU28"	2.40	394
"SKU94"	3.04	987
"SKU74"	3.17	904
"SKU97"	3.53	62
"SKU6"	4.08	65
"SKU24"	4.16	209
"SKU23"	4.32	391
"SKU4"	4.81	871
"SKU78"	6.31	946
```

## 6. Top 10 produtos com maior taxa de defeitos:
```sql
select
	sku,
	sum(defect_rates) as taxas_defeitos
from logistics
group by sku
order by taxas_defeitos desc
limit 10;
```
Resultado da query:
```sql
"sku"	"taxas_defeitos"
"SKU42"	  4.94
"SKU65"	  4.91
"SKU1"	  4.85
"SKU84"	  4.84
"SKU50"	  4.75
"SKU3"	  4.75
"SKU73"	  4.62
"SKU2"	  4.58
"SKU55"	  4.55
"SKU61"	  4.37
```

## 7. Tempo médio de produção por fornecedor (dias):
```sql
select
	l.supplier_name,
	round(avg(p.lead_times), 2) as tempo_medio
from logistics l
join products p on l.sku = p.sku
group by l.supplier_name
order by tempo_medio desc;
```
Resultado da query:
```sql
"supplier_name"	"tempo_medio"
"Supplier 4"	  17.00
"Supplier 1"	  16.78
"Supplier 2"	  16.23
"Supplier 5"	  14.72
"Supplier 3"	  14.33
```

## 8. Custos de transportes por rota:
```sql
select
	routes,
	sum(costs + shipping_costs) as custos
from logistics
group by routes
order by custos desc;
```
Resultado da query:
```sql
"routes"	"custos"
"Route B"	 22244.83
"Route A"	 21107.06
"Route C"	 10127.50
```
