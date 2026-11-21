# Método de Inversão da Matriz Produtiva
### Aprendizado por simulação para gestão de recursos próprios — Proposta v1 (opção A)

## 0. Objetivo
Um sistema pessoal (skill de LLM + JSON + HTML) em que o usuário:
1. lista os seus **recursos** (a matriz produtiva) e **objetivos**;
2. conversa com uma IA, que submete cada decisão às **travas**;
3. **prevê** o resultado antes de vê-lo e assiste à **simulação** no HTML;
4. com o tempo, **interioriza** o raciocínio. A medida de sucesso é a calibração, e não a obediência.

Em uma frase: as travas são o currículo, o ciclo I.B.E. é a pedagogia e o HTML é a sala de simulação.

---

## 1. Camada de domínio: o que proteger

### 1.1 Matriz produtiva (7 recursos)
| Recurso | Métrica sugerida | Unidade |
|---|---|---|
| Saúde | autoavaliação + sono médio + sinais objetivos | 0–10 |
| Tempo qualificado | horas/semana disponíveis para trabalho de alto valor | h |
| Atenção | número de frentes abertas simultâneas | n |
| Caixa líquido | saldo disponível sem vender ativos | R$ |
| Ativos físicos | valor de reposição × estado de conservação | R$ × % |
| Ferramental técnico | métodos, código, modelos reutilizáveis | inventário |
| Reputação | contrapartes que voltariam a contratar ou indicar | n |

### 1.2 Pré-condição P0: dados nus (Genchi Genbutsu / Zhengming)
Nenhuma trava é avaliada se a matriz não tiver sido lida nos últimos **N dias** (padrão: 30).
É um ritual curto e impessoal: saldo, custo fixo, desgaste e compromissos assumidos, lidos como instrumentos e não como julgamento moral.
**Falha:** cegueira voluntária. **Barreira:** o sistema se recusa a simular com dados vencidos.

### 1.3 As 6 travas
Cada trava tem uma métrica, as faixas verde, amarela e vermelha (valores padrão editáveis) e o atributo de **reversibilidade**. Uma falha irreversível pesa mais que todas as outras.

| # | Trava | Modo de falha | Métrica | Verde / Amarelo / Vermelho (padrão) | Irreversível? | Fonte |
|---|---|---|---|---|---|---|
| T1 | **Semente** (balanço de ativos) | Consumir o que gera o fluxo; ou trabalho 100% efêmero | (manutenção realizada ÷ desgaste estimado) e % do esforço que deixa ativo | ≥100% e ≥20% / 70–100% ou 10–20% / <70% ou <10% | Parcial (saúde: sim) | Catão; Toyota (TPM); Hesíodo |
| T2 | **Dependência** (recusa + gargalo externo) | Perder a capacidade de dizer não; ponto único de estrangulamento | meses de custo fixo cobertos pelo caixa; maior cliente/canal como % da receita | ≥6 m e ≤40% / 3–6 m ou 40–60% / <3 m ou >60% | Sim | Goldratt; Taleb |
| T3 | **Especificidade** | Investir sob medida sem salvaguarda e virar refém | especificidade do ativo (0–3) × salvaguarda (0–3: marco pago, propriedade retida, contrato escrito) | salvaguarda ≥ especificidade / diferença de 1 / diferença ≥2 | Sim | Williamson |
| T4 | **Puxado** | Resolver problema alheio sem demanda viável (push) | a contraparte já pôs pele em risco verificável? (sinal, prazo, recurso) | sim / promessa escrita / nada | Não | Toyota (pull); Sarasvathy |
| T5 | **Atenção** | Dispersão: otimizar o secundário com a base aberta | frentes abertas; existe uma falha vermelha aberta? | ≤3 e nenhuma / 4–5 / >5 ou expansão com uma vermelha aberta | Não | Goldratt (TOC) |
| T6 | **Reputação/Nome** | Combinados informais que corroem a relação | % de compromissos ativos com registro escrito e critério de aceite | ≥90% / 60–90% / <60% | Parcial | Confúcio (Zhengming) |

> As fusões em relação às 7 travas originais: a margem de recusa e o gargalo externo viraram T2 (Dependência); comer a semente e a alavancagem composta viraram T1 (balanço de ativos); a cegueira voluntária virou a pré-condição P0. A T5 e a T6 surgiram por desdobramento: a atenção como recurso e o registro de combinados.

### 1.4 Permissão PX: perda aceitável (barbell)
Uma decisão que **não passa em nenhuma trava vermelha** e cuja **perda máxima cabe no orçamento de apostas** (padrão: ≤10% do caixa e ≤10% do tempo do trimestre) é **liberada**, mesmo com incerteza alta.
Isso evita que o método vire paralisia, porque permite apostas pequenas com ganho assimétrico. Fontes: Sarasvathy (*affordable loss*) e Taleb (*barbell*).

### 1.5 Regra do gargalo dominante
A cada ciclo, só **uma** trava é a restrição ativa: a vermelha irreversível de maior impacto. Enquanto ela estiver aberta, decisões de expansão ficam bloqueadas, e só são permitidas decisões que a reduzam.

---

## 2. Camada de aprendizado: ciclo I.B.E.

| Passo | O que acontece | Quem age |
|---|---|---|
| 1. **Inverter** | Diante de uma decisão ("aceitar o contrato X"), o usuário **prevê** quais travas disparam e por quê | usuário |
| 2. **Blindar** | O usuário escolhe a barreira, seguindo a hierarquia: eliminar > impossibilitar > tornar visível > lembrar > instruir | usuário |
| 3. **Ensaiar** | O HTML simula a matriz em 3, 12 e 24 meses, com e sem a decisão, e com a barreira escolhida | sistema |
| 4. **Andon** | A IA interrompe quando uma trava é violada, sem julgamento, como leitura de instrumento | IA |
| 5. **Colher** | Previsão × resultado entram no **mapa de cegueiras**, que mostra quais travas o usuário costuma não ver | sistema |

**Métrica de aprendizado:** calibração por trava, ou seja, a % de acertos de previsão ao longo do tempo. Quando todas passam de 80%, o usuário "graduou" naquela trava, e a IA passa a perguntar menos e a confrontar mais (cenários mais ambíguos).

---

## 3. Arquitetura técnica

### 3.1 JSON (estado único)
```json
{
  "versao": "1.0",
  "leitura_matriz": { "data": "2026-11-21", "recursos": { "caixa": 0, "custo_fixo_mensal": 0, "...": "..." } },
  "objetivos": [ { "id": "O1", "descricao": "", "horizonte_meses": 12 } ],
  "travas": [ { "id": "T2", "metricas": [], "limiares": { "verde": "", "amarelo": "", "vermelho": "" }, "irreversivel": true } ],
  "permissao": { "caixa_pct": 10, "tempo_pct": 10 },
  "decisoes": [ {
      "id": "D1", "descricao": "", "previsao_usuario": { "travas": ["T3"], "justificativa": "" },
      "avaliacao": { "T3": "vermelho" }, "barreira": "", "resultado": "bloqueada|redesenhada|liberada"
  } ],
  "calibracao": { "T1": { "acertos": 0, "total": 0 } }
}
```

### 3.2 Skill (LLM)
- Faz a entrevista de inventário, verifica a P0 e aponta o gargalo dominante.
- Para cada decisão: **pede primeiro a previsão do usuário**, depois avalia, explica com o conceito-fonte e atualiza o JSON.
- Usa exemplos históricos (Catão, Toyota, produtores isolados) como casos de simulação, e não como autoridade.
- Trata as travas como **hipóteses revisáveis**: o usuário pode alterar limiares, e a mudança fica registrada com o motivo.

### 3.3 HTML
- **Painel da matriz:** 7 medidores e 6 travas com semáforo.
- **Simulador:** decisão → projeção comparada (com / sem / com barreira).
- **Mapa de cegueiras:** calibração por trava.
- **Biblioteca de cenários:** casos-treino prontos para quando não houver decisão real.

---

## 4. Limites declarados
- Não substitui a contabilidade, o planejamento tributário nem o aconselhamento financeiro.
- Os limiares padrão são pontos de partida, e não verdades.
- O método protege contra a ruína. Ele não garante crescimento, só o torna estruturalmente possível.
