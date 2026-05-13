# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `extrato_opçoes_instituto.pdf` | PDF | opções previdenciárias realizadas pelo participante após desligamento da patrocinadora ou alteração do vínculo empregatício |
| `alteracao_perfil_investimento.pdf` | PDF |registros de mudança de perfil de investimento do participante |
| `extrato_contribuicão.pdf` | PDF | histórico de contribuições mensais realizadas pelo participante e patrocinadora |
| `estatuto_social_alpha.pdf` | PDF | Documento institucional |
| `desempenho_dos_investimentos.pdf` | PDF | Documento contendo:	rentabilidade dos perfis,	composição da carteira,	indicadores financeiros |
| `regulamento_dos_planos.pdf` | PDF | Documento contendo regras do plano previdenciário |
| `politica_investimento_alpha.pdf` | PDF |Documento contendo as diretrizes de gestão dos recursos garantidores do plano previdenciário  |                                       

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Arquivos Utilizados

### 1. Extrato de Operações
Arquivo contendo movimentações financeiras do participante, incluindo:
-	contribuições
-	portabilidades
-	resgates
-	rentabilidade
-	saldos
-	empréstimos (quando aplicável)

Objetivo no agente:

Permitir análise da evolução financeira do participante e contextualizar respostas sobre histórico previdenciário

### 2. Alteração de Perfil de Investimentos
Documento com registros de mudança de perfil de investimento do participante.
Exemplos:
-	conservador
-	moderado
-	agressivo

Objetivo no agente:

Auxiliar em recomendações educativas e explicar impactos de risco, volatilidade e horizonte de investimento.

### 3. Extrato de Contribuição
Arquivo com histórico de contribuições mensais realizadas pelo participante e patrocinadora.

Objetivo no agente:

Permitir consultas sobre:
-	frequência de contribuição
-	percentual contributivo
-	contrapartida da patrocinadora
-	projeções previdenciárias

### 4. Estatuto Social da EFPC ALPHA
Documento institucional contendo:

-	estrutura administrativa
-	regras de governança
-	competências dos conselhos
-	diretrizes da entidade

Objetivo no agente:

Responder dúvidas institucionais e fornecer informações sobre governança e funcionamento da EFPC.

### 5. Relatório de Desempenho dos Investimentos
Documento contendo:
-	rentabilidade dos perfis
-	composição da carteira
-	indicadores financeiros
-	comparativos de desempenho

Objetivo no agente:

Permitir explicações sobre performance dos investimentos e educação financeira/previdenciária.

### 6. Regulamento do Plano Prev
Documento contendo regras do plano previdenciário:
-	elegibilidade
-	carência
-	resgate
-	benefício
-	portabilidade
-	institutos previdenciários

Objetivo no agente:

Servir como principal fonte normativa para respostas relacionadas aos direitos e deveres dos participantes

### 7. Política de Investimentos da ALPHA
Documento contendo as diretrizes de gestão dos recursos garantidores do plano previdenciário.
Inclui informações como:
-	objetivos de investimento
-	alocação estratégica dos ativos
-	limites de risco
-	segmentos de aplicação
-	metas de rentabilidade
-	governança e controles

Objetivo no agente:

Permitir respostas educativas e explicativas sobre:
•	funcionamento dos investimentos da EFPC
•	perfis de risco
•	estratégia de longo prazo
•	diversificação
•	aderência à legislação previdenciária


## Adaptações nos Dados

Os documentos utilizados na base de conhecimento foram adaptados e anonimizados para preservar informações institucionais e pessoais.

Embora parte dos documentos utilizados seja de acesso público na EFPC, foram realizadas adequações para utilização segura no projeto acadêmico e educacional.

As seguintes modificações foram aplicadas:

- remoção de nomes reais de participantes
- substituição do nome da entidade previdenciária por “ALPHA”
- substituição dos nomes das patrocinadoras por “BETA” e “GAMA”
- retirada de logotipos e elementos de identificação visual
- anonimização de dados cadastrais e financeiros
- adequação dos documentos para fins exclusivamente educacionais e acadêmicos[Sua descrição aqui]

---

## Estratégia de Integração

### Como os dados são carregados?

Os documentos da base de conhecimento são armazenados na pasta data do projeto e carregados no início da execução do agente.

Os arquivos estruturados (CSV e JSON) são lidos diretamente pela aplicação para acesso às informações de participantes, contribuições e perfis de investimento.

Já os documentos institucionais em PDF, como regulamento do plano, estatuto social e política de investimentos, passam por extração de texto para que seu conteúdo possa ser utilizado pelo agente durante as respostas.

Os documentos utilizados incluem:

- extrato de opções de instituto
- alteração de perfil de investimentos
- extrato de contribuição
- estatuto social da ALPHA
- relatório de desempenho dos investimentos
- regulamento do Plano Prev
- política de investimentos


### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

[Sua descrição aqui]

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
