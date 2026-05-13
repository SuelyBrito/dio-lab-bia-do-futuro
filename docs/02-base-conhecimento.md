# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `extrato_opçoes_instituto.pdf`    | PDF | opções previdenciárias realizadas pelo participante após desligamento da patrocinadora ou alteração do vínculo empregatício |
| `alteracao_perfil_invest.pdf`     | PDF | registros de mudança de perfil de investimento do participante |
| `extrato_contribuicão.pdf`        | PDF | histórico de contribuições mensais realizadas pelo participante e patrocinadora |
| `estatuto_social_alpha.pdf`       | PDF | Documento institucional |
| `desempenho_dos_investimentos.pdf`| PDF | Documento contendo:	rentabilidade dos perfis,	composição da carteira,	indicadores financeiros |
| `regulamento_dos_planos.pdf`      | PDF | Documento contendo regras do plano previdenciário |
| `politica_investimento_alpha.pdf` | PDF | Documento contendo as diretrizes de gestão dos recursos garantidores do plano previdenciário  | 
| `participantesPrev.json`          | PDF | arquivo contendo informações dos participantes do Plano Prev  | 

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


Os dados do participante são armazenados em arquivos estruturados no formato JSON e CSV dentro da pasta data do projeto.
No início da execução, o agente realiza a leitura desses arquivos para obter informações necessárias à contextualização das respostas, como:

- perfil do participante
- situação previdenciária
- contribuições
- perfil de investimentos
- opções por institutos

Os documentos institucionais e normativos em PDF também são carregados e processados para consulta contextual durante as interações.


### Como os dados são usados no prompt?

Os dados do participante são usados para contextualizar e personalizar as respostas do agente.

Informações básicas, como perfil de investimento, status no plano e resumo contributivo, são carregadas no início da sessão.

Já documentos maiores, como regulamento, política de investimentos e históricos detalhados, são consultados dinamicamente conforme a pergunta do usuário.

A estratégia utilizada combina contexto inicial e recuperação dinâmica de informações (RAG), tornando as respostas mais objetivas, eficientes e alinhadas às regras da EFPC.


## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
{
  "participantes": [
    {
      "id_participante": "P001",
      "nome": "Participante 01",
      "faixa_etaria": "50-55",
      "status_plano": "Autopatrocinado",
      "patrocinadora": "BETA",
      "plano": "Plano Prev",
      "tempo_plano_anos": 18,
      "perfil_investimento": "Moderado",
      "saldo_previdenciario": 285430.75,

      "instituto_previdenciario": {
        "tipo": "Autopatrocinio",
        "data_opcao": "2025-03-15"
      },

      "historico_perfil_investimento": [
        {
          "data": "2022-01-10",
          "perfil": "Conservador"
        },
        {
          "data": "2024-06-20",
          "perfil": "Moderado"
        }
      ],

      "resumo_contribuicoes": {
        "media_mensal": 1250.00,
        "ultima_contribuicao": "2026-04",
        "contribuicoes_12_meses": 15000.00
      },

      "rentabilidade": {
        "rentabilidade_12m": "11.2%",
        "perfil_referencia": "Moderado"
      }
    },

    {
      "id_participante": "P002",
      "nome": "Participante 02",
      "faixa_etaria": "60-65",
      "status_plano": "BPD",
      "patrocinadora": "BETA",
      "plano": "Plano Prev",
      "tempo_plano_anos": 24,
      "perfil_investimento": "Conservador",
      "saldo_previdenciario": 412890.10,

      "instituto_previdenciario": {
        "tipo": "Beneficio Proporcional Diferido",
        "data_opcao": "2024-09-01"
      },

      "historico_perfil_investimento": [
        {
          "data": "2020-03-11",
          "perfil": "Moderado"
        },
        {
          "data": "2023-08-15",
          "perfil": "Conservador"
        }
      ],

      "resumo_contribuicoes": {
        "media_mensal": 980.00,
        "ultima_contribuicao": "2024-08",
        "contribuicoes_12_meses": 11760.00
      },

      "rentabilidade": {
        "rentabilidade_12m": "9.4%",
        "perfil_referencia": "Conservador"
      }
      ]
}
...
```
