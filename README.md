# Análise Logística e Satisfação do Cliente — E-commerce Brasileiro (Olist)

## Objetivo do Projeto
Investigar como a eficiência logística — especificamente os prazos de entrega, atrasos e custos de frete — impacta a satisfação do cliente (nota de avaliação) no e-commerce brasileiro, além de mapear o desempenho operacional por estado e por categoria de produto.

## Ferramentas Utilizadas
* **Python (Google Colab):** Pandas, NumPy, Matplotlib e Seaborn para limpeza, validação de integridade, modelagem relacional e análise exploratória.
* **Data Studio:** Criação de dashboard interativo com KPIs logísticos, satisfação do cliente e faturamento.

## Arquitetura e Premissas dos Dados
Para evitar distorções nas métricas causadas pela relação *1:N* entre pedidos e itens, a análise foi estruturada em duas granularidades distintas:
* **Nível de Pedido (`orders` + `reviews` + `customers`):** Utilizado para calcular tempos de entrega, taxas de atraso e notas médias de avaliação, garantindo que pedidos com múltiplos itens não tivessem seu peso inflado.
* **Nível de Item (`items` + `products`):** Utilizado para análises de receita, frete e desempenho por categoria.

**Regras de negócio adotadas:**
* **Cálculo de atraso:** Baseado na diferença exata de *timestamp* entre a data de entrega ao cliente e a data estimada (entregas ocorridas após a data/hora prevista são contabilizadas como atraso).
* **Faturamento por categoria:** Considera a soma do preço dos itens (`price`) de todos os pedidos registrados na base consolidada.

## Dashboard Interativo (Data Studio)
🔗 **[Clique aqui para acessar o dashboard interativo no Data Studio](https://datastudio.google.com/reporting/4ea52bb6-66fc-40fa-982d-4ec9d418b2e4)**

### Visão Geral — Logística e Satisfação
(<img width="448" height="337" alt="dashboard olist pagina 1" src="https://github.com/user-attachments/assets/a9cadb0a-a3af-4e68-b873-95ea1896c348" />
)

### Visão Comercial — Categorias e Frete
(<img width="449" height="335" alt="dashboard olist pagina 2" src="https://github.com/user-attachments/assets/e7de813b-a74e-4f49-bd39-7bb96201bdde" />
)

## Principais Resultados e Insights
* **Impacto severo do atraso na nota:** Pedidos entregues dentro do prazo mantêm uma média de avaliação elevada (acima de 4,2), enquanto pedidos atrasados derrubam a média para menos de 2,6, concentrando a maioria das avaliações de 1 estrela.
* **Disparidade regional:** Estados mais afastados dos grandes centros logísticos (especialmente nas regiões Norte e Nordeste) apresentam maior tempo médio de trânsito e maior incidência de atrasos, refletindo diretamente em médias de avaliação inferiores.
* **Peso do frete por categoria:** Categorias de menor ticket médio e maior volume/peso apresentam maior proporção do frete em relação ao valor do produto, atuando como ponto crítico de atenção na jornada de compra.

## Arquivos do Projeto
* `notebook_olist.ipynb` — Código completo com tratamento, checagens de consistência, análises estatísticas e gráficos.
* `relatorio_olist.docx` — Documentação executiva com a contextualização, metodologia, principais achados e recomendações de negócio.
