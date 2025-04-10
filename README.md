# supply-chain-analysis

## 📝Descrição do projeto
Simulação de uma empresa do setor de cosméticos com foco na análise de vendas, desempenho logístico e possíveis problemas operacionais ao longo de um ano. Utilizei PostgreSQL para tratamento e consulta de dados e Power BI para criar um dashboard interativo com os principais KPIs.

## 🎯Objetivos
O objetivo deste projeto é simular o funcionamento de uma empresa de cosméticos e analisar seu desempenho em vendas e logística ao longo do ano. A proposta é identificar oportunidades de melhoria e compreender os principais desafios enfrentados durante o período analisado.

## 🛠️Ferramentas utilizadas
- SQL
- PostgreSQL
- Power BI

## 📊KPI's e métricas analisadas
- Faturamento total;
- Lucro;
- Produtos vendidos;
- Sazonalidade do faturamento ao longo do ano;
- Categoria dos produtos mais vendidos;
- Fornecedor com maior volume de vendas;
- Produtos vendidos por cidade;
- Produtos produzidos;
- Produtos em estoque;
- Relação de produtos mais baratos com volume de vendas;
- Top 10 produtos com maior taxa de defeitos;
- Tempo médio de produção por fornecedor (dias);
- Custos de transportes por rota;

## 📂Como visualizar o dashboard
- Baixe o arquivo .pbix presente no repositório e abra com o Power BI Desktop.

## 🧠Principais insights
- Alta lucratividade anual: A empresa fechou o ano com um faturamento de R$ 577.604,86 e um lucro expressivo de 89,92%.
- Influência da sazonalidade: Dezembro foi o mês com maior faturamento, indicando impacto positivo das festas de fim de ano. Outubro teve o pior desempenho, com queda de 32% em relação ao ticket médio.
- Estoque parado em destaque: Foram vendidos 46.099 produtos, mas 10.685 ficaram em estoque. É importante investigar se há excesso de produção ou baixa saída de certos itens.
- Skincare lidera em vendas e defeitos: Foi a categoria mais vendida, mas também com a maior taxa de defeitos (19,45%). Haircare aparece logo atrás com 18,34%.
- Preço não é o único fator de decisão: Produtos mais baratos mantiveram um bom equilíbrio de vendas, sugerindo que os clientes não escolhem apenas pelo menor preço.
- Desempenho regional desigual: Kolkata foi a cidade com maior volume de vendas (27,70%), enquanto Bangalore teve o menor (11,76%). Pode ser interessante investigar ações de marketing local ou barreiras logísticas.
- Alta demanda x tempo de produção: Suppliers 1 e 2 lideraram em vendas, mesmo com tempo de produção mais elevado — o que pode estar relacionado à alta procura e foco na qualidade.
- Supplier 4 é um alerta: Teve o menor número de vendas e o maior tempo de produção, sendo necessário avaliar a qualidade e viabilidade da parceria.
- Oportunidade na logística: A rota C apresentou o menor custo logístico anual (R$ 10.127,50). Vale analisar se é possível aumentar os envios por essa rota para reduzir despesas.

## 📌Conclusão
O projeto demonstrou a importância da análise integrada entre vendas e logística, trazendo pontos de atenção que podem orientar ações estratégicas da empresa. A combinação entre SQL e Power BI permitiu uma visão clara e interativa dos dados.

