# Porsche Sales Intelligence Dashboard

Dashboard executiva desenvolvida como projeto final para o desafio **Aceleração: AI Reports com Excel, GPT Agents e Claude Code**, utilizando uma base de vendas da Porsche originalmente desorganizada, com campos fora de padrão, datas inconsistentes e valores que exigiam tratamento antes da análise.

O resultado final é uma dashboard em **HTML estático**, com visual premium inspirado na identidade da Porsche Brasil, KPIs executivos, filtros interativos, rankings de modelos, análise por estado, análise por cidade e insights de negócio gerados com apoio de IA.

---

## Visão geral do projeto

O objetivo deste projeto foi transformar uma base de dados bruta em uma dashboard executiva, clara e confiável, capaz de responder perguntas de negócio como:

- Quais são os principais modelos Porsche vendidos por cidade?
- Qual combinação de ano e modelo teve maior saída no período analisado?
- Quais estados concentram maior volume de vendas?
- Quais modelos aparecem com maior recorrência na base?
- Como transformar uma base desorganizada em um relatório visual de alto padrão?

A dashboard foi construída com foco em três pilares:

1. **Tratamento e governança dos dados**
2. **Análise executiva e geração de insights**
3. **Design refinado e experiência visual limpa**

---

## Contexto da base de dados

A base original possuía registros de vendas com informações como:

- modelo Porsche;
- ano do modelo;
- cidade;
- estado;
- método de pagamento;
- preço de venda;
- data de venda;
- status de entrega.

Durante a análise inicial, foram encontrados problemas comuns em bases reais, como:

- datas em formatos diferentes;
- datas inválidas;
- registros com datas futuras em relação à data de publicação;
- campos textuais fora de padrão;
- nomes de modelos com variações;
- necessidade de padronização para filtros e gráficos;
- risco de perda de rastreabilidade caso os dados originais fossem sobrescritos.

Por isso, a estratégia adotada foi **não apagar nem substituir as colunas originais**. Em vez disso, foram criadas novas colunas tratadas e sanitizadas, preservando a base original para auditoria.

---

## Estratégia de tratamento dos dados

A limpeza dos dados foi feita progressivamente, partindo da base bruta até chegar à versão final utilizada na dashboard.

### 1. Preservação dos dados originais

As colunas originais foram mantidas intactas. Essa decisão foi importante para garantir:

- rastreabilidade;
- possibilidade de auditoria;
- comparação entre dado bruto e dado tratado;
- transparência sobre as decisões de limpeza;
- preservação da fonte original.

Em um projeto profissional, essa abordagem é mais segura do que simplesmente corrigir valores diretamente na base original.

---

### 2. Criação de colunas sanitizadas

Foram criadas colunas novas para análise, com nomes padronizados, como:

- `PorscheModelSanitized`
- `ModelYearSanitized`
- `SalesPriceSanitized`
- `PayMethodSanitized`
- `CitySanitized`
- `StateSanitized`
- `DeliveryStatusSanitized`
- `SaleDateSanitized`

Essas colunas permitiram que a dashboard trabalhasse com dados mais consistentes, sem perder a referência dos campos originais.

---

### 3. Correção das datas inválidas

Durante a análise, foram identificadas datas inválidas, como dias inexistentes em determinados meses ou formatos ambíguos.

Exemplos de problemas encontrados:

- `2024-02-30`
- `April 31st, 2024`
- `2024/15/07`
- `February 29th, 2025`
- `August 32nd, 2027`

A correção foi feita com regras conservadoras, como:

- ajustar dias inexistentes para o último dia válido do mês;
- interpretar datas ambíguas conforme o padrão mais provável;
- manter registro das correções realizadas;
- preservar a data original em sua coluna de origem.

Essa etapa permitiu transformar datas inconsistentes em datas válidas para análise temporal.

---

### 4. Auditoria das correções

Além da correção em si, foi criada uma aba de auditoria com o histórico das alterações de datas.

A auditoria incluiu informações como:

- identificador da venda;
- linha original na planilha;
- data original;
- data corrigida;
- regra aplicada.

Essa etapa reforça a governança do projeto, pois permite explicar como cada ajuste foi feito.

---

### 5. Exclusão de registros futuros do recorte final

Após a sanitização das datas, foi identificado que parte da base continha registros com datas futuras em relação à data de publicação do projeto.

Como a dashboard representa uma análise de vendas realizadas até a data de entrega, foi tomada a decisão de **excluir do recorte final os registros com data posterior a 26/05/2026**.

Essa decisão foi importante porque registros futuros poderiam distorcer os indicadores, especialmente:

- total de vendas;
- receita estimada;
- ranking por período;
- modelo líder;
- análise por estado;
- evolução temporal;
- leitura executiva da performance comercial.

Os dados futuros não foram tratados como erro apagado da base original. Eles apenas foram removidos do **recorte analítico final**, por não fazerem sentido para uma dashboard publicada em maio de 2026.

---

## Decisões analíticas

Além da limpeza dos dados, foram tomadas decisões para evitar que a dashboard ficasse carregada ou visualmente confusa.

### Rankings com Top N + Outros

Como a base continha muitos modelos, cidades e estados, os gráficos foram organizados com rankings curtos.

Exemplos:

- Top modelos vendidos;
- Top estados por volume;
- Top combinações de ano + modelo;
- agrupamento dos demais registros como “Outros”.

Essa decisão melhora a leitura visual e evita excesso de informação na tela.

---

### Agrupamento executivo de status

Os status de entrega foram agrupados em categorias executivas, facilitando a leitura gerencial.

Em vez de exibir muitos status operacionais separados, a dashboard trabalha com uma visão consolidada, como:

- concluídas;
- em andamento;
- em análise;
- canceladas.

Esse tipo de agrupamento ajuda a transformar dados operacionais em informação executiva.

---

### Foco em KPIs de alto valor

A dashboard final prioriza indicadores de leitura rápida, como:

- vendas totais;
- receita estimada;
- ticket médio;
- modelo líder;
- estado líder;
- período analisado.

A ideia foi criar um painel com aparência de relatório executivo, e não apenas uma tela cheia de gráficos.

---

## Dashboard final

A versão final da dashboard recebeu o nome:

**Porsche Sales Intelligence Dashboard**

Ela inclui:

- filtros interativos;
- KPIs executivos;
- gráficos de modelos mais vendidos;
- ranking por estado;
- análise de ano + modelo;
- tabela de cidades com modelo líder;
- bloco de insights executivos gerados com apoio de IA;
- seção de metodologia explicando o tratamento dos dados;
- design premium, escuro, elegante e refinado.

---

## Tecnologias e recursos utilizados

- **Excel** para análise inicial e estruturação da base;
- **ChatGPT** para apoio na análise, limpeza, decisões de negócio, estrutura da dashboard e geração do HTML;
- **HTML, CSS e JavaScript** para construção da dashboard estática;
- **GitHub** para versionamento e documentação;
- **GitHub Pages** para publicação gratuita da dashboard.

---

## Estrutura sugerida do repositório

```text
porsche-sales-intelligence-dashboard/
│
├── index.html
├── README.md
│
└── data/
    └── porsche_sales_cleaned.xlsx
```

---

## Como visualizar a dashboard

Caso esteja rodando localmente, basta abrir o arquivo:

```text
index.html
```

em qualquer navegador moderno.

## Repositório

Este projeto está disponível em:

[GitHub - Porsche Sales Intelligence Dashboard](https://brunogiacomelli1979-cyber.github.io/porsche-sales-intelligence-dashboard/
)
---

## Aprendizados do projeto

Este projeto mostrou que uma boa dashboard não depende apenas de visual bonito. Antes da etapa de design, foi necessário:

- entender a estrutura da base;
- identificar inconsistências;
- preservar os dados originais;
- criar campos sanitizados;
- corrigir datas inválidas;
- auditar as correções;
- remover registros futuros do recorte analítico;
- definir KPIs relevantes;
- reduzir ruído visual;
- transformar dados em uma narrativa executiva.

A versão final representa não apenas uma dashboard, mas um fluxo completo de trabalho com dados: da base bruta ao relatório executivo.

---

## Observação sobre os dados

Os dados utilizados neste projeto possuem finalidade educacional e foram tratados para fins de construção de dashboard, análise exploratória e apresentação de portfólio.

A decisão de remover registros futuros do recorte final foi feita para manter coerência temporal com a data de publicação do projeto: **26/05/2026**.

---

## Resultado final

O projeto final entrega uma dashboard executiva, elegante e interativa, construída a partir de uma base inicialmente desorganizada e progressivamente tratada com apoio de IA.

A proposta demonstra habilidades em:

- análise de dados;
- limpeza e sanitização;
- pensamento crítico sobre qualidade da informação;
- design de dashboards;
- storytelling com dados;
- uso prático de IA aplicada a relatórios executivos.
