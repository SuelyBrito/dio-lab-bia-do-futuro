# Avaliação e Métricas

## Como Avaliar seu Agente

A avaliação pode ser feita de duas formas complementares:

1. **Testes estruturados:** Você define perguntas e respostas esperadas;
2. **Feedback real:** Pessoas testam o agente e dão notas.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
|---------|--------------|------------------|
| **Assertividade** | O agente respondeu o que foi perguntado? | Tenho perfil conservador e estou próximo da aposentadoria. Qual perfil de investimento seria mais adequado? |
| **Segurança** | O agente evitou inventar informações? | Perguntar algo fora do contexto e ele admitir que não sabe |
| **Coerência** | A resposta faz sentido para o perfil do participante? | Sugerir investimento conservador para cliente conservador |

> [!TIP]
> Peça para 3-5 pessoas (amigos, família, colegas) testarem seu agente e avaliarem cada métrica com notas de 1 a 5. Isso torna suas métricas mais confiáveis! Caso use os arquivos da pasta `data`, lembre-se de contextualizar os participantes sobre o **cliente fictício** representado nesses dados.

---

## Exemplos de Cenários de Teste

Crie testes simples para validar seu agente:

### Teste 1. Governança
- **Pergunta:** "Quais são as responsabilidades do Conselho Deliberativo?"
- **Resposta esperada:** "O Conselho Deliberativo é responsável por deliberar sobre alterações no Estatuto do Alpha, inclusive aquelas decorrentes de lei, e sobre alterações nos regulamentos dos planos de benefícios e dos planos de assistência à saúde, bem como sobre a instituição ou extinção desses planos. Além disso, pode exercer outras atribuições previstas no Estatuto, em Regimento Interno próprio e na legislação vigente."

- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 2 — Consulta Básica de Previdência

**Objetivo**
Validar se o agente responde corretamente perguntas simples sobre previdência.
- **Pergunta:** “Qual a diferença entre participante ativo e assistido?”
- **Resposta esperada:** "Com base nos documentos fornecidos:
**Participante ativo** é aquele que ainda está contribuindo para o plano, normalmente enquanto mantém vínculo empregatício com o patrocinador.
**Participante assistido** é aquele que já começou a receber um benefício mensal do plano, como aposentadoria, pensão ou outro benefício de prestação continuada.
Ou seja, o ativo ainda acumula recursos, enquanto o assistido já usufrui dos benefícios do plano."

- **Resultado:** [X] Correto  [ ] Incorreto


**Pergunta:** Tenho 52 anos e 10 anos de contribuição. Posso solicitar aposentadoria?

**Resposta esperada:** "Com base no Regulamento Prev Alpha, para solicitar o benefício de aposentadoria normalmente, é necessário:
-	Ter, no mínimo, 53 anos de idade;
-	Ter, no mínimo, 60 meses (5 anos) de vinculação ao PREV;
-	Ter encerrado o vínculo empregatício com o patrocinador.
Você já possui 10 anos de contribuição (mais do que os 60 meses exigidos), mas ainda não completou 53 anos de idade.
Porém, há uma exceção importante:
O regulamento permite requerer o benefício de aposentadoria antes de completar 53 anos, desde que cumpra as demais condições (ou seja, tempo de vinculação e término do vínculo empregatício).
Faltam informações para concluir:
Você não informou se já encerrou o vínculo empregatício com o patrocinador.
Se já tiver encerrado esse vínculo, você pode solicitar a aposentadoria mesmo antes dos 53 anos, conforme a exceção prevista no regulamento.
**Resumo:**
-	Se já encerrou o vínculo empregatício com o patrocinador, pode solicitar a aposentadoria.
-	Se ainda está trabalhando no patrocinador, precisa primeiro encerrar o vínculo para poder solicitar."
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 3: Recomendação de Perfil de Investimento
**Objetivo**
Verificar se o agente realiza recomendações coerentes com o perfil do participante.

- **Pergunta:** “Tenho perfil conservador e estou próximo da aposentadoria. Qual perfil de investimento seria mais adequado?”
- **Resposta esperada:** "Considerando que você tem perfil conservador e está próximo da aposentadoria, o perfil de investimento mais adequado é o Perfil Conservador.
Segundo a Cartilha Perfis Prev, esse perfil é recomendado para participantes com baixa tolerância a risco e pouco tempo para requerer a aposentadoria, pois prioriza a preservação do valor investido e a liquidez, reduzindo o risco de oscilações que podem impactar negativamente o seu saldo próximo do momento de se aposentar."
- **Resultado:** [X] Correto  [ ] Incorreto


### Teste 4: Pergunta fora do escopo

**Objetivo**
Validar a segurança do agente diante de perguntas não relacionadas ao tema.

- **Pergunta:** "Qual a previsão do tempo?"
- **Resposta esperada:** "Posso responder apenas perguntas relacionadas à previdência complementar e aos documentos carregados."
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 4: Informação inexistente

**Objetivo**
Verificar se o agente evita inventar informações

- **Pergunta:** "Quanto rende exatamente o perfil XYZ no próximo mês?”
- **Resposta esperada:** "Não é possível informar exatamente quanto o perfil XYZ irá render no próximo mês. O extrato fornecido mostra apenas valores históricos de contribuições, pagamentos e movimentações, mas não apresenta informações sobre o perfil XYZ, nem projeções ou regras de rentabilidade futura. Para saber o rendimento exato, seria necessário ter acesso à política de investimentos do perfil XYZ e à rentabilidade projetada ou garantida, caso exista."
- **Resultado:** [X] Correto  [ ] Incorreto

---

## Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**

-	Clareza nas respostas;
-	Boa contextualização sobre previdência complementar;
-	Respostas coerentes com o perfil do participante;
-	Segurança ao admitir limitações de informação.


**O que pode melhorar:**

- O agente de IA apresenta dificuldade em responder perguntas específicas utilizando o conteúdo da cartilha.
-	As respostas estão muito genéricas e pouco aderentes às regras do plano.

**Problemas identificados e melhorias implementadas**

-	O PDF original possuía limitações de OCR, dificultando a leitura correta do texto.
-	Parte do conteúdo da cartilha não era corretamente convertida em embeddings.
-	O sistema de busca vetorial (RAG) não recuperava trechos relevantes em algumas consultas.
-	Possível utilização de embeddings antigos após atualização do documento.

---

## Métricas Avançadas (Opcional)

Para quem quer explorar mais, algumas métricas técnicas de observabilidade também podem fazer parte da sua solução, como:

- Latência e tempo de resposta;
- Consumo de tokens e custos;
- Logs e taxa de erros.

Ferramentas especializadas em LLMs, como [LangWatch](https://langwatch.ai/) e [LangFuse](https://langfuse.com/), são exemplos que podem ajudar nesse monitoramento. Entretanto, fique à vontade para usar qualquer outra que você já conheça!
