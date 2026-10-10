# Planejador de Viagens 2027

Página única (HTML, CSS e JavaScript puro) para planejar uma viagem a dois em 2027 saindo de São Paulo. Compara 28 destinos no Brasil e no mundo em qualquer mês do ano, com custo item por item, clima do mês, emendas de feriado, roteiro dia a dia e um planejador de economia.

Não precisa de instalação, servidor nem build: é só abrir o `index.html` no navegador.

## O que a página faz

- **Mês a mês:** escolha qualquer mês de 2027. Clima, preço de temporada, datas, roteiros e planejador se ajustam ao mês.
- **Melhor época de cada destino:** mapa de calor com os 28 destinos × 12 meses (ótimo, com ressalvas, fraco). A estrela marca o mês de clima ótimo mais barato de cada destino.
- **Datas e feriados:** semanas de sábado a sábado (7 noites) ou de quarta a domingo (5 dias), além das emendas de feriado de 2027 (Ano-Novo, Páscoa, Tiradentes, Corpus Christi, 7 de Setembro, 12 de Outubro, Finados, 15 de Novembro, Natal e Réveillon).
- **Regras da CLT:** as datas de férias respeitam o mínimo de 5 dias por período e a proibição de começar as férias nos 2 dias antes de um feriado ou do domingo. A página mostra dias de férias, dias de trabalho usados e a folga contínua.
- **Comparativo:** custo de cada viagem dividido em passagem, hospedagem, alimentação, passeios, transporte local e seguro/taxas; custo × clima; para onde vai o dinheiro; custo por dia aproveitado.
- **Filtros:** duração, perfil (econômico, intermediário, confortável), valores para o casal ou por pessoa, teto por pessoa e região.
- **Destinos e roteiros:** para cada destino, tabela de custos nos três perfis, roteiro com as datas reais da viagem, onde ficar, o que reservar antes e a observação de clima do mês.
- **Planejador:** destino, mês, datas, perfil, número de pessoas, itens incluídos e reserva para imprevistos. Calcula o total, quanto guardar por mês até a viagem, o custo do mesmo destino ao longo do ano e um calendário de compras (passagem, hospedagem, visto, pedido de férias).
- **Plano de férias do ano:** como fica a divisão dos 30 dias de férias com o bloco de Carnaval já marcado.

As escolhas ficam salvas no navegador (`localStorage`) e voltam na próxima visita. Funciona no celular e em modo claro ou escuro.

## Como usar

1. Baixe ou clone o repositório.
2. Abra `index.html` no navegador.

Para publicar online, ative o **GitHub Pages** em *Settings → Pages*, com a branch `main` e a pasta raiz. A página fica em `https://andreplannerer.github.io/Planejador-de-Viagens/`.

## Estrutura do código

Tudo está em `index.html`:

| Parte | Onde | O que guarda |
|---|---|---|
| Custos e roteiros | `const D = [...]` | Para cada destino: custos por pessoa de 7 noites em agosto nos perfis econômico (`e`) e intermediário (`i`), na ordem passagem, hospedagem, alimentação, passeios, transporte local e seguro/taxas; horas de viagem; documentos; onde ficar; roteiro de 8 dias (`plan`). |
| Clima e temporada | `const META = {...}` | Para cada destino: faixas de meses com nota de clima (3 ótimo, 2 com ressalvas, 1 fraco), rótulo e explicação (`seas`); meses de alta (`hi`) e baixa (`lo`) temporada. |
| Feriados | `const HOL` | Feriados nacionais e pontos facultativos de 2027. |
| Emendas | `const WIN` | Janelas de viagem montadas à mão para os meses com feriado. |
| Cálculo | `items()` | Ajusta o custo pela temporada do mês, pelo número de noites e pelo perfil. |

Para atualizar um preço, edite os vetores `e` e `i` do destino em `D`. Para mudar a época boa de um destino, edite `seas`, `hi` e `lo` em `META`.

## Premissas dos números

- Os custos partem de preços pesquisados em 2026 para uma semana em agosto, saindo de São Paulo, e servem como projeção, não como cotação.
- Para os outros meses, passagem e hospedagem sobem cerca de 25% na alta temporada do destino e caem cerca de 15% na baixa.
- Passagem custa o mesmo para qualquer duração; hospedagem acompanha as noites; alimentação, passeios e transporte local acompanham os dias.
- O perfil confortável é uma projeção a partir do intermediário.
- Paraty e Capitólio não têm passagem aérea: a ida de carro entra como combustível em transporte local.
- Os valores em reais usam o câmbio de 2026.
- Carnaval e Corpus Christi são pontos facultativos, e as emendas de segunda-feira dependem da empresa.

## Fontes

As fontes de cada custo estão listadas no fim da página, na seção **Fontes**.
