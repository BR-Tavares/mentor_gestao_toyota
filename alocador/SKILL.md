---
name: alocador-recursos
description: Conversa na CLI para listar recursos e objetivos do usuário e gerar uma tela HTML única com sugestões didáticas de alocação (eficiência/eficácia), métricas de risco simuláveis (comprometimento de tempo, insolvência, concentração, dispersão) e os conceitos de gestão associados. Use quando o usuário quiser organizar recursos, decidir onde pôr tempo/caixa, avaliar um contrato/projeto ou atualizar o seu painel de alocação.
---

# Alocador de Recursos por Inversão

## Fluxo
1. **Conversar** (curto, uma pergunta por vez): levante os **recursos** e os **objetivos**. Se já existir `painel.json` no diretório do usuário, leia-o e só pergunte o que mudou.
2. **Inverter**: para cada objetivo, pergunte-se "como esta alocação leva à ruína?" e confira as travas abaixo.
3. **Sugerir**: de 3 a 6 sugestões, priorizando a **restrição dominante** (a pior métrica vermelha). Cada uma deve ter ação, porquê, métrica e conceitos.
4. **Gerar**: copie `modelo.html` para `painel.html` no diretório do usuário, substitua **apenas** o conteúdo do bloco `<script id="dados" type="application/json">` pelo JSON novo e salve o mesmo JSON em `painel.json`.
5. Responda na CLI com: o caminho do arquivo, a restrição dominante em uma frase e uma pergunta, se houver uma decisão pendente.

## Esquema do JSON
```json
{
  "atualizado": "AAAA-MM-DD",
  "recursos": {
    "horas_semana_disponiveis": 50,
    "caixa": 40000,
    "custo_fixo_mensal": 8000,
    "receitas": [ { "fonte": "Cliente A", "mensal": 6000 } ],
    "outros": [ { "nome": "Impressora 3D", "estado": "bom", "nota": "" } ]
  },
  "objetivos": [
    { "id": "O1", "nome": "", "prazo_meses": 6, "prioridade": 1,
      "horas_semana": 20, "gasto_mensal": 1500,
      "deixa_ativo": true, "especificidade": 0, "salvaguarda": 0, "pele_em_risco_contraparte": true }
  ],
  "sugestoes": [
    { "tipo": "eficacia | eficiencia | alerta",
      "titulo": "", "acao": "", "porque": "",
      "metrica": "tempo | folego | concentracao | refem | frentes",
      "ajustes": [ { "objetivo": "O1", "horas_semana": 12, "gasto_mensal": 1000 } ],
      "conceitos": ["inversao", "toc"] }
  ]
}
```
- `ajustes` é opcional. Quando presente, o botão **Simular** da tela recalcula as métricas com a sugestão aplicada (antes × depois).
- `especificidade` e `salvaguarda` vão de 0 a 3.
- Use **valores informados pelo usuário**. Se algo foi estimado por você, diga isso em `porque`.

## Métricas (calculadas pela tela)
| Métrica | Fórmula | Verde / Amarelo / Vermelho |
|---|---|---|
| Comprometimento do tempo | Σ horas_semana ÷ horas disponíveis | ≤80% / ≤100% / >100% |
| Fôlego (risco de insolvência) | caixa ÷ (custo fixo + Σ gastos − Σ receitas) | ≥6 meses / 3–6 / <3 (sem queima = verde) |
| Concentração de receita | maior fonte ÷ total | ≤40% / ≤60% / >60% |
| Projetos sem proteção (`refem`) | nº de objetivos com especificidade > salvaguarda | 0 / — / ≥1 |
| Projetos em paralelo (`frentes`) | nº de objetivos com horas > 0 | ≤3 / 4–5 / >5 |

A tela mostra automaticamente no topo **o gargalo agora** (a pior métrica). Inclua sempre ao menos uma sugestão cuja `metrica` seja esse gargalo.

## Travas (para o raciocínio e para os alertas)
- **T1 Semente** (`semente`): não consumir o que gera o fluxo; preferir objetivos que deixam ativo (`deixa_ativo`).
- **T2 Dependência** (`recusa`): fôlego baixo ou cliente dominante tiram a capacidade de dizer não.
- **T3 Especificidade** (`williamson`): especificidade > salvaguarda é risco de ficar refém → exigir marcos pagos ou retenção de propriedade.
- **T4 Puxado** (`puxado`): não alocar engenharia sem que a contraparte ponha pele em risco.
- **T5 Atenção** (`toc`): uma restrição por vez; não expandir com métrica vermelha aberta.
- **T6 Nome** (`zhengming`): combinados por escrito com critério de aceite.
- **Permissão** (`perda_aceitavel`): uma aposta que cabe em ≤10% do caixa e do tempo e não bate em trava vermelha pode seguir.

## Conceitos disponíveis (ids)
`inversao`, `semente`, `recusa`, `williamson`, `puxado`, `toc`, `zhengming`, `perda_aceitavel`, `alavancagem`, `pareto`, `poka_yoke`, `barbell`. Os textos já estão no modelo. Use só esses ids.

## Estilo das sugestões
- **Calcule as métricas com as fórmulas acima antes de escrever.** Todo número citado em `porque` precisa bater com o que a tela vai mostrar.
- `metrica` deve medir o risco que o texto descreve (ex.: refém → `refem`, não `concentracao`).
- Use o **nome** do objetivo no texto, nunca o id ("O2").
- Linguagem do dia a dia; o nome do autor/conceito fica só nos chips.
- Antes de salvar, valide o JSON (`node -e "JSON.parse(require('fs').readFileSync('painel.json'))"`).
- `acao`: verbo + número ("Reduzir O2 de 20 para 10 h/semana").
- `porque`: 1 a 2 frases, ligando a ação à métrica e ao objetivo, sem jargão (o jargão fica nos conceitos).
- Sempre pelo menos uma sugestão do tipo `alerta` se alguma métrica estiver vermelha.
