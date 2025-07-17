# 📊 Dashboard de Vendas - Case Simulado LG

Projeto desenvolvido como parte de um **case de BI**, utilizando dados fictícios da LG. O objetivo foi construir um dashboard no **Power BI** para analisar vendas, faturamento e desempenho por produto, loja e período.

---

## 🎯 Objetivos do Dashboard

- Identificar os **modelos mais vendidos**
- Analisar o **faturamento por loja e bandeira**
- Acompanhar o **desempenho dos produtos ao longo do tempo**
- Comparar **vendas trimestrais**
- Avaliar **ticket médio por loja**

---

## 🧭 Navegação e Interatividade

- O **menu está presente em todas as páginas**, permitindo navegação entre as seções.
- Os **gráficos e tabelas são interativos**: ao clicar em um item, os demais visuais se ajustam automaticamente conforme a seleção.

---

## 📈 Como usar os gráficos

### Gráficos principais
- **Filtro "Data Geral"**: ajusta o período analisado e atualiza a tabela de lojas com novos valores de faturamento e ticket médio.
- **Filtro "Modelos mais Vendidos"**: define quantos modelos aparecem no ranking.
- **Filtro "Desempenho dos Produtos"**: permite escolher categorias para acompanhar a evolução de vendas.
- A **tabela de lojas** e o **ranking de modelos** são conectados: ao selecionar um, o outro é filtrado automaticamente.

### Gráficos extras
- **"Data Geral"** também filtra as páginas de vendas por estado e faturamento por bandeira.
- **"Selecione 1 Trimestre"**: compara produtos vendidos entre dois trimestres.
- Gráficos de **produtos** e **faturamento por bandeira** são interativos.
- **KPIs fixos** (vendas e faturamento totais) mostram os valores consolidados dos últimos 5 anos.

---

## 💡 Insights Gerados

### Principais Gráficos
- Entre **dez/2024 e mai/2025**, a LG faturou **R$ 57,2 milhões** com **ticket médio de R$ 16,3 mil**.
- Lojas de **São Paulo** e **Rio de Janeiro** lideram em receita.

  <img width="732" height="195" alt="image" src="https://github.com/user-attachments/assets/e81cfc7c-1319-4677-a916-c266b663d5df" />


- **TVs** foram os produtos mais vendidos e com maior crescimento.
  
  <img width="731" height="179" alt="image" src="https://github.com/user-attachments/assets/5fef511e-189c-408f-881c-705ad2630525" />

- **Maio de 2025** registrou o pico de vendas no período analisado.

  <img width="749" height="211" alt="image" src="https://github.com/user-attachments/assets/f28fbd5e-9b0e-43f0-8332-3e8e73008564" />


### Gráficos Extras

<img width="626" height="142" alt="image" src="https://github.com/user-attachments/assets/ee2958fe-4964-455f-8872-a4b85e42ce99" />


- No **1º trimestre de 2025**, os maiores crescimentos em vendas foram:
  - **Secadora** (+16,03%)
  - **Geladeira** (+10,92%)
  - **Notebook** (+11,45%)
- **TV** teve crescimento de 5,64%; **Máquina de Lavar** teve queda de -2,34%.

---

  <img width="659" height="265" alt="image" src="https://github.com/user-attachments/assets/06face12-cd25-42e9-999e-79323794df94" />

- No faturamento por bandeiras (últimos 6 meses):
  - **Ponto Frio**: R$ 17,1 milhões
  - **Casas Bahia**: R$ 12,1 milhões
  - **Extra**: R$ 12 milhões
 
---
<img width="467" height="259" alt="image" src="https://github.com/user-attachments/assets/a00932c9-9a14-438b-9bef-125655e304e9" />
    
- Regiões com maior volume de vendas: **Sudeste**, **Sul** e parte do **Centro-Oeste**.

## 📐 Algumas medidas DAX Utilizadas


**Ranking de Vendas por Modelo =** 
RANKX(
    ALL(Dim_Produtos[MODELO]);
    [Quantidade Vendida]
)




**Top N de Modelos =** 
IF(
    [Ranking de Vendas por Modelo] <= [Valor Filtro de Top Vendido];
    CALCULATE(
        [Quantidade Vendida];
        TOPN(
            [Valor Filtro de Top Vendido];
            VALUES(Dim_Produtos);
            [Quantidade Vendida]
        )
    )
)


**Variação Trimestral (%) =** 
DIVIDE(
    [Vendas Trimestre Atual] - [Vendas Trimestre Anterior];
    [Vendas Trimestre Anterior]
)


**Numero de Vendas =** 
DISTINCTCOUNT(Fato_Vendas[id_venda])

## 🛠️ Ferramentas Utilizadas

- Power BI  
- Power Query  
- DAX  
- Excel


