# Equipamentos Especiais · protótipo de mapa e fluxo

Protótipo estático para acompanhar **religadores e reguladores indisponíveis**, visualizar a posição no mapa e consolidar o histórico de SS por ativo.

> **Segurança:** este repositório é público. Por isso, a demonstração usa somente ativos e coordenadas fictícios. As planilhas reais são importadas localmente pelo navegador e não são enviadas a um servidor nem gravadas no GitHub.

## O que esta versão de teste entrega

- mapa de equipamentos por latitude/longitude;
- filtros por tipo, local/polo e etapa do fluxo;
- distinção entre a relação oficial de indisponíveis e possíveis equipamentos especiais fora dela;
- histórico de SS pendentes, abertas, repassadas, canceladas e atendidas;
- classificação de etapa: DMSL, COEP, COCM, Proteção e comissionamento;
- fila de material separando **consultar estoque/preparar compra**, **faltam fatos técnicos** e **em fluxo, sem nova compra**;
- exportação da visão filtrada para Excel.

## Como testar

1. Abra `index.html` por GitHub Pages ou em um servidor local simples.
2. A tela inicia em dados fictícios para mostrar a estrutura.
3. Importe:
   - **Relação de Equipamentos Indisponíveis**;
   - **Base COEP de SS Pendentes/Abertas**;
   - opcionalmente, um cadastro geográfico com `Ativo`, `Latitude` e `Longitude`.
4. Clique em **Processar bases**.

Para publicar com GitHub Pages, em **Settings → Pages**, escolha a branch `main` e a pasta `/ (root)`.

## Cabeçalhos reconhecidos

O importador procura variações comuns, ignorando acentos, espaços e pontuação.

| Base | Campos principais |
|---|---|
| Relação de indisponíveis | `Ativo`, `Tipo`, `Município/Polo`, `Alimentador`, `Data Ocorrência`, `Latitude`, `Longitude`, `SS`, `Prioridade` |
| SS COEP | `Ativo`, `SS`, `Status`, `Área/Responsável`, `Data`, `Descrição/Parecer`, `Material`, `Quantidade`, `Modelo`, `Tensão` |
| Cadastro geográfico | `Ativo`, `Latitude`, `Longitude`, `Município/Polo` |

Quando uma coluna não é encontrada, o painel aponta a lacuna em vez de inventar a informação.

## Critérios de análise

As regras de fluxo estão documentadas em [`docs/REGRAS_DE_TRATAMENTO.md`](docs/REGRAS_DE_TRATAMENTO.md).

## Próximas etapas recomendadas

1. validar os cabeçalhos definitivos das duas bases reais;
2. incluir um cadastro de coordenadas confiável para todos os ativos;
3. guardar snapshots diários/mensais das bases em repositório privado, SharePoint ou banco de dados corporativo;
4. somente depois conectar uma automação de atualização e controle de histórico.
