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
- **Resposta esperada:**
**O agente:**

- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 2 — Consulta Básica de Previdência

**Objetivo**
Validar se o agente responde corretamente perguntas simples sobre previdência.
- **Pergunta:** “Qual a diferença entre participante ativo e assistido?”
- **Resposta esperada:**

**O agente:**

A diferença fundamental entre um Participante Ativo e um Participante Assistido reside no estágio em que se encontram em relação ao plano de previdência: o primeiro está na fase de acumulação de recursos, enquanto o segundo já está na fase de recebimento de benefícios.
Com base no Regulamento do Plano Prev e nos documentos de suporte, aqui estão as principais distinções:

## 1. Definição e Vínculo Empregatício

**Participante Ativo:** É o empregado da patrocinadora que requereu sua inscrição no plano e mantém o vínculo empregatício ativo.
**Participante Assistido:** É todo participante (ou seu beneficiário) que já está em gozo de um benefício mensal pago pelo plano.
Geralmente, para se tornar assistido, o participante precisa ter concretizado o término do vínculo empregatício com a patrocinadora (exceto em casos de invalidez ou pensão)

- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 3: Recomendação de Perfil de Investimento
**Objetivo**

Verificar se o agente realiza recomendações coerentes com o perfil do participante.

- **Pergunta:** “Tenho perfil conservador e estou próximo da aposentadoria. Qual perfil de investimento seria mais adequado?”
- **Resposta esperada:** 

- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 4: Contribuições
- **Pergunta:** "Como funciona a contribuição do participante?"
- **Resposta esperada:** Produto compatível com o perfil do cliente
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 5: Pergunta fora do escopo

**Objetivo**
Validar a segurança do agente diante de perguntas não relacionadas ao tema.

- **Pergunta:** "Qual a previsão do tempo?"
- **Resposta esperada:** Agente informa que só trata de finanças
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 4: Informação inexistente

**Objetivo**
Verificar se o agente evita inventar informações

- **Pergunta:** "Quanto rende exatamente o perfil XYZ no próximo mês?”
- **Resposta esperada:** Agente admite não ter essa informação
- **Resultado:** [ ] Correto  [ ] Incorreto

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
