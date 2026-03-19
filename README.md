[README.md](https://github.com/user-attachments/files/26119273/README.md)
# Dashboard de Rentabilidade — Cabana Distribuicao

Analise estrategica de rentabilidade por tabela de preco. Ferramenta de apoio a decisao para precificacao, margem liquida e comparativo entre fornecedores.

## Contexto

Dashboard HTML interativo construido a partir da tabela de precos exportada do ERP Natus. Foco em venda interna ES (B2B, nao consumidor final).

## Regime Tributario Aplicado

| Tributo | Aliquota | Regra |
|---------|----------|-------|
| ICMS | 7,00% | CST 20 — Base reduzida 41,18% x 17% — todos os produtos |
| PIS + COFINS | 0,00% | CST 06 — Isento: Alho, Azeite, Potes Cabana, Nacionalizados (Origem 2) |
| PIS + COFINS | 9,25% | CST 01 — Tributado: Nacionais (Origem 0) — PIS 1,65% + COFINS 7,60% |
| Comissao | 2,30% | Incide sobre todos os produtos |
| **Carga minima** | **9,30%** | Produtos isentos de PIS/COFINS |
| **Carga maxima** | **18,55%** | Produtos nacionais tributados |

## Estrutura do Dashboard

O dashboard possui 7 abas navegaveis:

**Visao Geral** — KPIs consolidados (faturamento potencial, custo em estoque, resultado liquido, margem bruta e liquida), comparativo por grupo com tributacao detalhada, mix de faturamento, e 3 paineis de decisao estrategica: maior resultado potencial, risco (alto estoque + margem baixa) e oportunidade (alta margem + baixo estoque).

**Alho** — Analise completa com comparativo por padrao (calibre x classificacao x tipo) entre fornecedores, ranking por margem liquida, barra visual de margem, diferenca percentual e financeira vs melhor fornecedor, filtros por calibre/classificacao/tipo, graficos por fornecedor e calibre, bubble chart margem x faturamento.

**Alimentos** — 567 SKUs com tributacao mista (nacional 18,55% / nacionalizado 9,30%), ranking por subgrupo, tabela completa com impostos individualizados.

**Azeite** — Grupo critico com margem media negativa. Comparativo preco vs CMV por SKU.

**Conservas** — 33 SKUs, margem media 24,5%, tributacao padrao 18,55%.

**Potes Cabana** — Melhor grupo do portfolio (36,2% margem liquida), PIS/COFINS isento.

**Embalagens** — 13 SKUs com 2 itens criticos abaixo do custo.

## Calculo da Margem

```
Margem Bruta = (Preco/kg - CMV/kg) / Preco/kg x 100
Margem Liquida = Margem Bruta - Carga Total (ICMS + PIS/COF + Comissao)
Resultado Liquido = Faturamento Potencial x Margem Liquida / 100
```

## Como Usar

1. Abra o arquivo `dashboard_rentabilidade.html` em qualquer navegador
2. Navegue pelas abas para cada grupo de produto
3. Use os filtros (dropdowns) para refinar a visualizacao
4. No comparativo de alho, filtre por calibre/classificacao/tipo para comparar fornecedores

## Como Atualizar

1. Exporte a tabela de precos atualizada do ERP Natus (CSV, separador ponto-e-virgula)
2. Envie o arquivo no chat do Claude com a instrucao "atualizar dashboard"
3. A tarefa agendada `atualizar-dashboard-rentabilidade` processa automaticamente

## Dados de Origem

- **Fonte:** ERP Natus — Tabela de Preco Original
- **Formato:** CSV (separador `;`, encoding UTF-8)
- **Colunas-chave:** GrupoProduto, SubGrupoProduto, Produto, SubProduto, PrecoSKUPrimaria, CustoMedioGerencial, Quantidade, IDOrigemMercadoria, CurvaABC

---

Cabana Importacao e Comercio de Alho Ltda — Viana, ES
