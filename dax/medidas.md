# Medidas DAX

Principais medidas utilizadas no projeto.

```DAX
Volume Antecipado =
SUM(TabelaMovimentacoes[Valor antecipado (R$)])
```

```DAX
Volume Solicitado =
SUM(TabelaMovimentacoes[Valor solicitado (R$)])
```

```DAX
Receita =
SUM(TabelaMovimentacoes[Receita estimada (R$)])
```

```DAX
Margem =
SUM(TabelaMovimentacoes[Margem estimada (R$)])
```

```DAX
Total Operações =
COUNTROWS(TabelaMovimentacoes)
```

```DAX
Operações Concluídas =
CALCULATE(
    COUNTROWS(TabelaMovimentacoes),
    TabelaMovimentacoes[Situação] = "Concluída"
)
```

```DAX
Taxa de Conversão =
DIVIDE([Operações Concluídas], [Total Operações], 0)
```

```DAX
Margem Percentual =
DIVIDE(
    [Margem],
    [Volume Antecipado],
    0
)
```

```DAX
Spread Médio =
AVERAGE(TabelaMovimentacoes[Spread anual])
```

```DAX
Taxa Média Cliente =
AVERAGE(TabelaMovimentacoes[Taxa anual ao cliente])
```

```DAX
Taxa Básica Média =
AVERAGE(TabelaMovimentacoes[Taxa básica anual])
```

```DAX
Total Empresas =
DISTINCTCOUNT(TabelaEmpresas[ID Empresa])
```

```DAX
Empresas Manuais =
CALCULATE(
    DISTINCTCOUNT(TabelaEmpresas[ID Empresa]),
    TabelaEmpresas[Tipo de antecipação] = "Manual"
)
```

```DAX
Percentual Empresas Manuais =
DIVIDE([Empresas Manuais], [Total Empresas], 0)
```

```DAX
Recebíveis Mensais =
SUM(TabelaEmpresas[Recebíveis mensais (R$)])
```

```DAX
Potencial Adicional =
SUM(TabelaEmpresas[Potencial adicional (R$)])
```

```DAX
Potencial Capturável =
SUM(TabelaEmpresas[Potencial capturável (R$)])
```

```DAX
Potencial Capturável Manual =
CALCULATE(
    [Potencial Capturável],
    TabelaEmpresas[Tipo de antecipação] = "Manual"
)
```

```DAX
Volume Atual Carteira =
SUM(TabelaEmpresas[Volume antecipado atual (R$)])
```

```DAX
Volume Potencial =
[Volume Atual Carteira] + [Potencial Capturável]
```

```DAX
Potencial de Crescimento % =
DIVIDE([Potencial Capturável], [Volume Atual Carteira], 0)
```

```DAX
Empresas Alta Prioridade =
CALCULATE(
    DISTINCTCOUNT(TabelaEmpresas[ID Empresa]),
    TabelaEmpresas[Prioridade] = "Alta"
)
```

```DAX
Potencial Alta Prioridade =
CALCULATE(
    [Potencial Capturável],
    TabelaEmpresas[Prioridade] = "Alta"
)
```

```DAX
Empresas com Potencial =
CALCULATE(
    DISTINCTCOUNT(TabelaEmpresas[ID Empresa]),
    TabelaEmpresas[Potencial capturável (R$)] > 0
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

```DAX
% Antecipado Atual Médio =
AVERAGE(TabelaEmpresas[% antecipado atual])
```

```DAX
Volume Ano Anterior =
CALCULATE(
    [Volume Antecipado],
    SAMEPERIODLASTYEAR(TabelaCalendario[Date])
)
```

```DAX
Crescimento Anual % =
DIVIDE(
    [Volume Antecipado] - [Volume Ano Anterior],
    [Volume Ano Anterior]
)
```

```DAX
Volume Mês Anterior =
CALCULATE(
    [Volume Antecipado],
    DATEADD(TabelaCalendario[Date], -1, MONTH)
)
```

```DAX
Crescimento Mensal % =
DIVIDE(
    [Volume Antecipado] - [Volume Mês Anterior],
    [Volume Mês Anterior]
)
```
