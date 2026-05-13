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



## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

[Sua descrição aqui]

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

[ex: Os JSON/CSV são carregados no início da sessão e incluídos no contexto do prompt]

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
