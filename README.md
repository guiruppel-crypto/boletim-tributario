# Boletim do Dia — Direito Tributário

Boletim diário com as novidades de direito **tributário**: atos oficiais, estados e municípios, legislativo, decisões judiciais e administrativas (STF, STJ, TRFs, TJs e CARF) e artigos. Cada edição traz destaques, tabelas por categoria (status, resumo, impacto prático, relevância, fontes datadas) e a lista de fontes pesquisadas.

Este repositório é uma cópia do painel publicado no Claude, gerada a partir do artifact e das edições gravadas no banco de dados dele.

## Estrutura

| Caminho | Conteúdo |
|---|---|
| `index.html` | A página do boletim. Dentro do Claude, lê as edições do banco do artifact; fora dele, lê os arquivos de `edicoes/`. |
| `edicoes/AAAA-MM-DD.json` | Uma edição por dia útil. |
| `edicoes/index.json` | Lista das edições, da mais recente para a mais antiga. A página usa esta lista para montar o seletor. |
| `tarefa-diaria.md` | Horário e instruções da tarefa agendada que gera cada edição. |

## Como abrir

A página precisa ser servida por HTTP para ler os JSON (abrir o arquivo direto do disco não funciona):

```bash
python3 -m http.server 8000
# depois abra http://localhost:8000
```

Também funciona no GitHub Pages: ative em *Settings → Pages*, com a branch `main` e a pasta raiz.

## Formato de uma edição

```json
{
  "data": "2026-11-06",
  "geradoEm": "2026-11-06T09:50:00Z",
  "periodo": "06/11/2026 a 06/11/2026",
  "nota": "Itens já reportados em edições anteriores não foram repetidos.",
  "destaques": ["..."],
  "itens": [{
    "categoria": "atos | estados | legislativo | tribunais | artigos",
    "materia": "Tributário",
    "item": "STJ — CSLL e amortização de deságio",
    "status": "Julgado",
    "resumo": "...",
    "impacto": "...",
    "relevancia": "ALTA | MÉDIA | BAIXA",
    "fontes": [{ "nome": "ConJur", "data": "02/11/2026", "url": "https://..." }]
  }],
  "fontesPesquisadas": [{ "grupo": "Tribunais", "nome": "STF — Portal de notícias", "url": "https://...", "obs": "..." }]
}
```

## Atualização

As edições novas são gravadas todos os dias úteis no banco do artifact pela tarefa agendada (veja `tarefa-diaria.md`). Este repositório **não** se atualiza sozinho: para trazer edições novas, exporte-as do artifact para `edicoes/` e acrescente a data em `edicoes/index.json`.

Os resumos são produzidos por IA a partir das fontes indicadas. Confira o texto oficial antes de citar.
