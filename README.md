# Duelo 2026 · Apuração do 2º turno ao vivo

Página web estática que mostra a apuração do 2º turno para presidente (eleição 6258) lendo os dados **direto do servidor público do TSE**. Não tem servidor próprio, banco de dados nem chave de acesso: o navegador de cada visitante consulta o TSE e a tela se atualiza sozinha.

## O que tem na página

**Ao vivo**
* **Duelo animado:** os dois candidatos viram caricaturas (cabeça grande feita com a foto oficial do TSE, corpo de cavaleiro com capa e espada) lutando na frente do Congresso Nacional. Quem lidera usa a coroa, ataca mais, acerta mais golpes e empurra o adversário para trás; quem está perdendo se defende, toma golpes, sua e se abaixa conforme a diferença cresce. A cada atualização do TSE, quem ganhou mais votos naquela rodada faz um combo e aparecem os votos ganhos por cada um. Se a liderança mudar, aparece **VIRADA!**; quando o TSE declarar o eleito, o vencedor comemora e o outro cai de joelhos.
* **Cabo de guerra:** barra com o percentual de votos válidos de cada um e a linha dos 50%.
* **Cartões dos candidatos** com foto, partido, vice, percentual e votos, e o selo de quem está na frente.
* **Apuração:** anel com o percentual de seções totalizadas.
* **Quanto falta para virar?:** estimativa de quanto o segundo colocado precisa dos votos válidos que ainda faltam para passar o primeiro.
* **Narração do duelo:** linha do tempo em texto com cada atualização, viradas e marcos da apuração.
* **Brasil em hexágonos:** mapa em blocos com três modos (Liderança, Apuração e Comparado a 2022).
* **Placar por estado:** lista em formato borboleta, agrupada por região, com ordenação e download em CSV.
* **Duelo na sua cidade:** busca de qualquer município do Brasil e botão para levar o duelo para aquela cidade.
* **Como a noite evoluiu:** gráfico da diferença entre os dois conforme a apuração avança (guardado no navegador enquanto a página estiver aberta).
* Modo telão (tela cheia) e efeitos sonoros opcionais.

**Resumo geral**: eleitorado, seções, comparecimento, abstenção, válidos, brancos e nulos, do Brasil ou de cada estado.

**Boletim de urna**: estado, município, zona e seção, com a situação do boletim publicado pelo TSE e atalho para o app oficial.

## Fontes de dados (todas públicas, do TSE)

| Dado | Endereço |
|---|---|
| Resultado Brasil, estado ou município | `https://resultados.tse.jus.br/oficial/ele2026/6258/dados/{uf}/{uf}{municipio}-c0001-e006258-u.json` |
| Lista de municípios | `https://resultados.tse.jus.br/oficial/ele2026/6258/config/mun-e006258-cm.json` |
| Seções por estado (boletins) | `https://resultados.tse.jus.br/oficial/ele2026/arquivo-urna/3221/config/{uf}/{uf}-p003221-cs.json` |
| Arquivos de uma seção | `https://resultados.tse.jus.br/oficial/ele2026/arquivo-urna/3221/dados/{uf}/{mun}/{zona}/{secao}/p003221-{uf}-m{mun}-z{zona}-s{secao}-aux.json` |

As caricaturas usam recortes das fotos oficiais dos candidatos publicadas pelo TSE (`.../6258/fotos/br/{sqcand}.jpeg`), já embutidos no `index.html`.

Frequência de leitura: Brasil e o local escolhido a cada 20 segundos, os 27 estados mais o exterior a cada 60 segundos. A leitura pausa quando a aba fica em segundo plano e volta ao reabrir.

## Privacidade e segurança

* Nenhuma chave de API, token, senha ou credencial no código. A página só lê arquivos públicos do TSE.
* Nenhum dado de quem visita é coletado: não há formulário, cookie, analytics nem rastreamento.
* A única coisa gravada no navegador é a preferência de som (ligado ou desligado). O gráfico da noite fica só na memória da aba e some quando ela é fechada.
* Todas as chamadas de rede vão apenas para `resultados.tse.jus.br`.

## Publicação no GitHub Pages

O site é um único arquivo `index.html`. Basta colocar os arquivos desta pasta na raiz de um repositório e ligar o GitHub Pages em **Settings > Pages > Deploy from a branch > main / (root)**. O arquivo `.nojekyll` evita processamento extra do GitHub.

## Aviso

Projeto independente, sem vínculo com o TSE nem com candidatos ou partidos. O duelo é uma brincadeira visual que só reflete o placar oficial. Em caso de divergência, vale o site oficial: https://resultados.tse.jus.br/oficial/app/index.html#/eleicao/6258/uf/br/cargo/1/vis/nominal/resultados
