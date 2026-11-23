# PDCA: onde funcionou, onde falhou e como implantar num sistema que já existe

Estudo de apoio às premissas 29 e 30. Termos Toyota (STP, andon, nemawashi, kata) estão explicados em `references/toyota.md`.

**Pergunta de trabalho:** em que ambiente o PDCA se desenvolve, em que ambiente ele morre, e como um líder o faz girar num sistema que já tem medo de julgamento e cultura de "entregar tudo pronto"?

## 1. O que o PDCA é (e o que costuma virar)

- **Origem:** Shewhart (1939) descreveu uma sequência linear: especificar, produzir, inspecionar. Deming a apresentou como ciclo no Japão em 1950, e os japoneses a reformularam como PDCA (Moen e Norman, 2009).
- **Correção de Deming:** mais tarde ele preferiu **PDSA** (*Study*, estudar), porque "Check" virou "inspecionar". No sentido original, o terceiro passo é comparar o resultado com a previsão e aprender. Não é conferir se a pessoa acertou (Moen e Norman, 2009).
- **Ideia central:** cada ciclo é um experimento. Se a previsão falha, isso é informação, não fracasso. Por isso o PDCA depende de que o erro possa ser dito sem risco.

## 2. Onde funcionou

| Caso | O que aconteceu | Condição que fez funcionar |
|---|---|---|
| **Toyota (STP, Sistema Toyota de Produção)** | Milhares de pequenos experimentos diários, conduzidos por quem faz o trabalho | Padrão como linha de base; o líder ensina a resolver em vez de resolver; problema visível é valorizado (Spear e Bowen, 1999; Rother, *Toyota Kata*, 2009) |
| **NUMMI (GM e Toyota, Califórnia, 1984)** | Uma das piores fábricas da GM, com a maioria dos operários recontratados e o mesmo sindicato (UAW), chegou em poucos anos à qualidade das fábricas japonesas | O sistema mudou, não as pessoas: andon (cordão que qualquer operador puxa para parar a linha), ajuda imediata em vez de bronca, treino no Japão. Muda-se a cultura mudando o que as pessoas fazem, não o que pensam (paráfrase de John Shook, *MIT Sloan Management Review*, 2010) |
| **Virginia Mason (hospital, Seattle, desde 2002)** | Aplicação do STP à saúde; sistema de "alerta de segurança do paciente" que qualquer funcionário pode acionar | Direção comprometida por mais de uma década; o alerta de erro passou a ser elogiado; houve crises no caminho (Kenney, *Transforming Health Care*) |
| **Aviação comercial** | Relato voluntário de erros (ASRS, sistema de relatos da NASA) e cultura justa (distingue erro honesto de imprudência) | Quem relata o próprio erro tem proteção; a punição fica reservada à imprudência deliberada (Reason; Dekker, *Just Culture*) |
| **Alcoa (Paul O'Neill, 1987)** | A segurança virou prioridade número um; acidentes chegavam ao presidente em 24 horas, com plano de prevenção (relato jornalístico de Duhigg, *O Poder do Hábito*; tratar como ilustrativo) | Um critério claro e compartilhado; o problema subia rápido sem caça a culpados |

**Padrão comum:** o critério estava combinado antes, o ciclo era pequeno e frequente, quem expunha o problema era protegido, o líder ia ao lugar real e havia tempo reservado para verificar.

## 3. Onde falhou

| Caso | O que aconteceu | Por que o PDCA morreu |
|---|---|---|
| **GM depois da NUMMI** | A GM não conseguiu levar o modelo para as outras fábricas por anos | Gerentes médios viam o andon como perda de controle; copiaram as ferramentas, não a relação com o erro |
| **Lean importado como programa** | Quadros, formulários e eventos kaizen sem mudança de conduta da liderança | O PDCA virou ritual: relatório preenchido para cima, não aprendizado. (A cifra "70% das implantações falham" circula muito, mas tem base fraca: trate como anedótica) |
| **Mid Staffordshire (hospital, Reino Unido, 2005 a 2009)** | Mortes evitáveis num ambiente de metas e medo (Relatório Francis, 2013) | Metas de custo e a busca do status de *foundation trust* acima de tudo; quem levantava problemas era ignorado ou punido; o C virou cobrança |
| **Wells Fargo (2016)** | Milhões de contas falsas para bater metas | O que é medido vira alvo (premissa 14); a verificação media o número, não a realidade |
| **Boeing 737 MAX (acidentes de 2018 e 2019)** | Falhas de projeto e certificação do sistema MCAS (relatório do Congresso dos EUA, 2020) | O sinal de erro existia, mas a pressão de prazo e custo e a certificação delegada impediram que ele parasse o projeto |
| **Toyota (recalls de 2009 e 2010)** | Falhas reais (tapete e pedal) e resposta lenta; parte da crise foi de percepção, sem falha eletrônica confirmada (NHTSA e NASA) | Akio Toyoda admitiu ao Congresso (2010) que o crescimento superou a capacidade de formar pessoas; Liker e Ogden (*Toyota Under Fire*) relativizam a causa |

**Padrão comum:** a verificação servia para julgar pessoas, as metas vinham de cima sem método, os problemas eram punidos ou ignorados e não havia folga.

## 4. Síntese: as condições do ambiente

| Dimensão | Ambiente onde o PDCA gira | Ambiente onde o PDCA morre |
|---|---|---|
| Critério | Combinado no P, explícito | Implícito; decidido por quem julga depois |
| Tamanho do ciclo | Pequeno e frequente | Grande; só se mostra o pronto |
| Erro exposto | Agradecido | Punido ou constrangido |
| Papel do líder | Treinador, que pergunta | Juiz, que cobra |
| Verificação | Estudo: previsto contra real | Inspeção: certo contra errado |
| Meta | Direção, com método | Número, sem método |
| Folga | Tempo reservado para verificar | Tudo é urgência (premissas 16 e 22) |

## 5. O mecanismo do medo (ligação com a premissa 29)

1. Sem critério explícito, quem julga decide na hora, e o julgamento parece pessoal.
2. A pessoa se antecipa e se autoavalia antes dos outros, em excesso, mas com critérios superficiais: o que parece acabado e o que o chefe vai achar.
3. Para reduzir o risco, ela entrega tudo de uma vez e o mais tarde possível.
4. Cada entrega fica grande, então cada julgamento fica grande e o medo aumenta.
5. O ciclo se reforça, e o PDCA vira só "PD": planeja, faz e torce, sem verificar nem ajustar.

**Ponto de alavanca:** combinar o critério antes transforma o julgamento sobre a pessoa num teste do produto. Isso também corrige a superficialidade da análise, porque dá à pessoa algo concreto para verificar.

## 6. Como implantar num sistema que já existe

O sistema não começa do zero. O medo, a cultura de entregar pronto e a falta de correção já estão lá. Não se anuncia "agora temos PDCA". Planta-se um ciclo que prova a si mesmo.

1. **Comece por você.** Mostre um rascunho seu, peça crítica e mude algo visivelmente por causa dela. É o sinal mais forte de que expor é seguro (Edmondson).
2. **Escolha um ciclo pequeno e de baixo risco.** Uma entrega recorrente, com uma ou duas pessoas dispostas. Não comece pelo que é crítico nem por quem tem mais medo.
3. **Dê nome ao rascunho.** "Versão 0" ou "peça para ajuste" muda a regra do jogo: nessa etapa, a falta de acabamento é esperada.
4. **Combine o critério no P.** "Vamos verificar X e Y no dia Z." A revisão fala do critério, nunca da pessoa.
5. **Na verificação, pergunte "o que você aprendeu?" antes de "o que deu errado?".** As perguntas de treinador do *Toyota Kata* servem de roteiro: qual é a meta, como está agora, qual obstáculo, qual o próximo passo, quando vemos o resultado.
6. **Agradeça em público quem expõe o erro cedo.** Corrija em particular, e sempre o processo.
7. **Proteja o tempo da verificação.** Sem folga, o C é o primeiro a ser cortado.
8. **Torne a prova visível.** Mostre o antes e depois do ciclo-piloto. O resultado convence mais que o discurso, sobretudo onde há desconfiança histórica (premissa 28).
9. **Espere resistência dos níveis do meio.** No caso GM, quem mais perdia controle era quem mais travava. Inclua essas pessoas cedo (nemawashi).

## 7. Questões em aberto para refinar

- Como medir se o medo está diminuindo? Candidatos: número de rascunhos mostrados antes do prazo e de erros relatados pela própria pessoa. Esses números devem **subir** no começo.
- Como o líder lida com o próprio medo de ser julgado pelos superiores enquanto protege a equipe?
- Qual é a versão do PDCA para trabalho criativo e de conhecimento, em que o critério não está totalmente claro antes?
- Fontes a aprofundar: Edmondson, *The Fearless Organization* (2018); Rother, *Toyota Kata*; Deming, *Out of the Crisis*; Dekker, *Just Culture*; Kegan e Lahey, *An Everyone Culture*.
