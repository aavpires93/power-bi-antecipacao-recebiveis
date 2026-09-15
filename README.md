# Estratégia e Antecipação de Recebíveis — Power BI

Projeto de portfólio em Power BI voltado à análise estratégica de antecipação de recebíveis para grandes contas.

> **Aviso:** este projeto utiliza dados 100% fictícios/sintéticos e tem finalidade exclusivamente educacional e de portfólio. A identidade visual é inspirada em uma adquirente de pagamentos e não representa material oficial da empresa.

## Objetivo

Responder principalmente à pergunta:

**Quais clientes ainda fazem antecipações de forma manual e quanto de volume e receita podemos capturar aumentando a recorrência desses clientes?**

A análise foi estruturada em três páginas:

1. **Visão Executiva** — acompanhamento dos principais indicadores da carteira.
2. **Potencial da Carteira** — identificação e priorização das maiores oportunidades comerciais.
3. **Precificação** — análise da relação entre taxa básica, spread, preço ao cliente e rentabilidade.

## Base de dados

A base sintética possui aproximadamente **30 mil movimentações** e **200 empresas fictícias**, cobrindo o período de **jan/2025 a ago/2026**.

Principais entidades do modelo:

- Empresas
- Movimentações
- Consultores
- Metas
- Taxa Básica
- Calendário
- Medidas

Entre os campos analisados estão volume solicitado, volume antecipado, tipo de antecipação, segmento, taxa básica, spread, taxa ao cliente, receita, custo de captação, margem, potencial adicional, probabilidade de captura e prioridade.

## Principais indicadores

- Volume Antecipado
- Receita
- Margem
- Margem %
- Taxa de Conversão
- Taxa Básica Média
- Spread Médio
- Taxa Média Cliente
- Potencial Capturável
- Potencial de Crescimento %
- Empresas de Alta Prioridade
- Receita Potencial Estimada

## Lógica de oportunidade

O potencial comercial foi construído a partir da diferença entre o nível atual de antecipação da empresa e uma referência do segmento.

**Potencial adicional = % de referência × recebíveis mensais − volume antecipado atual**

Em seguida, foi aplicada uma probabilidade de captura:

**Potencial capturável = potencial adicional × probabilidade de captura**

A receita potencial é uma estimativa baseada na relação atual entre receita e volume antecipado.

## Páginas do painel

### 1. Visão Executiva

A página apresenta uma leitura geral da operação, com filtros por período, segmento, UF e tipo de antecipação.

Principais análises:

- Evolução mensal do volume antecipado
- Volume por segmento
- Manual x recorrente
- Principais empresas da carteira
- Indicadores executivos de volume, receita, margem e conversão

### 2. Potencial da Carteira

Foco na identificação das oportunidades com maior potencial de captura.

Principais análises:

- Potencial capturável
- Potencial de crescimento
- Empresas de alta prioridade
- Receita potencial estimada
- Atual x potencial por segmento
- Manual x recorrente por potencial capturável
- Top empresas com maior potencial
- Dispersão entre percentual antecipado atual e potencial capturável
- Tabela de oportunidades

### 3. Precificação

Foco em entender como custo de captação e preço ao cliente influenciam a rentabilidade.

Principais análises:

- Taxa Básica Média
- Spread Médio
- Taxa Média Cliente
- Receita
- Margem %
- Evolução das taxas
- Margem por segmento
- Spread x Margem
- Análise de Precificação por empresa

## Exemplos de medidas DAX

```DAX
Volume Antecipado =
SUM(TabelaMovimentacoes[Valor antecipado (R$)])
```

```DAX
Margem Percentual =
DIVIDE(
    [Margem],
    [Volume Antecipado]
)
```

```DAX
Potencial Capturável =
SUM(TabelaEmpresas[Potencial capturável (R$)])
```

```DAX
Empresas Alta Prioridade =
CALCULATE(
    DISTINCTCOUNT(TabelaEmpresas[ID Empresa]),
    TabelaEmpresas[Prioridade] = "Alta"
)
```

```DAX
Receita Potencial Estimada =
[Potencial Capturável] *
DIVIDE(
    [Receita],
    [Volume Antecipado],
    0
)
```

## Ferramentas utilizadas

- Power BI
- DAX
- Excel
- Modelagem relacional
- Análise de indicadores financeiros e comerciais

## Autor

**Anderson Pires**

Projeto desenvolvido para portfólio com foco em análise de dados, estratégia comercial, antecipação de recebíveis e Power BI.
