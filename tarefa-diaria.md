# Tarefa agendada — geração da edição diária

- **Nome:** Boletim do Dia — Tributário
- **Horário:** dias úteis (segunda a sexta), 6h43, horário de Brasília (`CRON_TZ=America/Sao_Paulo 43 6 * * 1-5`)
- **Destino:** banco de dados do artifact do boletim (coleção `edicoes`, um documento por dia `AAAA-MM-DD`) e este repositório (`edicoes/AAAA-MM-DD.json` e `edicoes/index.json`)
- **Aprovação:** roda sem pedir aprovação; avisa por notificação quando termina

## Instruções da tarefa

Gere a edição de hoje do "Boletim do Dia — Tributário", grave-a no banco de dados do artifact do boletim e envie a mesma edição a este repositório. Não altere nem republique a página; apenas grave o documento.

**ESCOPO:** somente direito TRIBUTÁRIO (tributos federais, estaduais e municipais, contribuições, obrigações acessórias, processo administrativo e judicial tributário, execução fiscal, transação, crimes tributários, reforma tributária IBS/CBS/IS). Ignore direito empresarial/societário, recuperação judicial e falência (salvo quando a decisão tratar de crédito tributário), e matérias penais (exceto crimes tributários), previdenciárias, trabalhistas, consumeristas, administrativas etc.

1. Descubra a data de hoje (fuso America/Sao_Paulo), formato AAAA-MM-DD.
2. Leia as duas edições mais recentes (coleção `edicoes`, ordenadas por `data` decrescente, limite 2). O período coberto vai do dia seguinte à edição anterior até hoje (em segundas-feiras inclui o fim de semana). Não repita itens já reportados.
3. Pesquise na web, dentro do período:
   - **Atos oficiais federais:** DOU, Planalto (leis, MPs, decretos), RFB (INs, soluções de consulta Cosit relevantes, ADEs), PGFN (portarias, editais de transação), Ministério da Fazenda, Comitê Gestor do IBS (CGIBS), CGSN.
   - **Estados e municípios:** Confaz (convênios, ajustes), Sefaz estaduais, assembleias legislativas e prefeituras (ISS, IPTU, ITBI) quando relevantes.
   - **Legislativo:** Câmara e Senado (PLPs, PLs, PECs, resoluções, reforma tributária IBS/CBS, alíquotas, audiências).
   - **Tribunais — SOMENTE DECISÕES:** julgamentos (acórdãos, teses fixadas, repetitivos e repercussão geral julgados), liminares, tutelas, sentenças, decisões monocráticas, julgamentos iniciados ou suspensos por pedido de vista e afetações de temas repetitivos. NÃO inclua notícias institucionais dos tribunais ou do CARF (balanços, metas, estatísticas, estoque, calendários, eventos, consultas públicas, audiências públicas, iniciativas administrativas), em nenhuma categoria.
     - STF: portal de notícias https://noticias.stf.jus.br/ (percorra as notícias do período) e pautas do Plenário/Plenário Virtual, aproveitando apenas decisões.
     - STJ: portal de notícias, Informativo de Jurisprudência, repetitivos/temas afetados.
     - TRFs 1 a 6, Justiça Federal de 1º grau quando noticiada, TJs (câmaras e varas de direito público/tributário e execuções fiscais) e CARF (acórdãos e decisões de turmas e da CSRF).
   - **Artigos e análises (tributário):**
     - Seções de opinião/tributário do ConJur (https://conjur.com.br/areas/tributario/), "Migalhas de peso" e colunas do JOTA.
     - Pesquisa geral na web por artigos e análises de direito tributário publicados no período (ex.: "artigo tributário" + tema do dia, "reforma tributária IBS CBS análise", "LC 236/2026 artigo", "transação tributária análise", "ITCMD", "ganho de capital", "PIS Cofins tese"), incluindo blogs e informativos de escritórios, Valor Econômico, Estadão/Fausto Macedo, Contábeis, Fenacon e revistas especializadas. Descarte guias genéricos e textos antigos ou sem data: só entram artigos publicados no período, com tese ou análise concreta e de interesse prático.
   - **Agenda de obrigações** e prazos próximos (nos destaques, quando houver vencimentos na semana).

   Anote cada site efetivamente consultado, inclusive os que não trouxeram novidade ou bloquearam o acesso.
4. Monte os itens (normalmente 6 a 20), no formato descrito no README. Só inclua o que estiver nas fontes; nunca invente processos, números, datas ou decisões. Abra a página antes de resumir; não resuma só pelo título. Categoria sem novidades fica sem itens.
5. **destaques:** 3 a 5 frases (até ~300 caracteres cada) com os pontos mais importantes do período, incluindo prazos da semana. Sem notícias institucionais.
6. **fontesPesquisadas:** todos os sites consultados, como `{ grupo, nome, url, obs? }`, nos grupos "Tribunais", "Órgãos e atos oficiais", "Legislativo", "Portais jurídicos", "Imprensa e especializados" e "Pesquisa geral".
7. Grave o documento do dia com `data`, `geradoEm`, `periodo`, `nota`, `destaques`, `itens` e `fontesPesquisadas`.
8. Envie a edição a este repositório: salve `edicoes/AAAA-MM-DD.json`, atualize `edicoes/index.json` e faça commit "Edição de DD/MM/AAAA" na `main`.
9. Responda com uma linha: quantos itens foram gravados, quantas fontes foram consultadas, se a edição foi enviada ao GitHub e o primeiro destaque.
