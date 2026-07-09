# MakeValue IA

**MakeValue IA** é o framework de produto e os agentes de IA que apoiam o ciclo **refinamento → desenvolvimento → review → finalização**. Esta área é a **fonte de verdade** que os agentes consultam para trabalhar já com o contexto de cada produto.

## O que é

Em vez de espalhar regras de negócio em vários lugares, centralizamos aqui: cada produto tem seu framework (em **Skills**) e cada agente de IA tem sua diretriz (em **Agentes**). O time conversa com a Claude, que lê estas páginas e age como o agente certo — sem ninguém precisar colar instruções longas.

| Pasta | Conteúdo |
| --- | --- |
| **Agentes** | Diretrizes dos agentes de IA (hoje: **planning-agent**; em breve finalization / dev / review) |
| **Skills** | Base de conhecimento por produto — visão de negócio, arquitetura, histórico. É o que os agentes leem antes de refinar. |
| **Design System (kit de protótipo)** | Kit HTML/CSS com a cara da plataforma. O planning-agent parte dele para os protótipos ficarem parecidos com o produto real. |

## Para o time de Produto — passo a passo

**Pré-requisito (uma vez só):** no **app da Claude** (desktop), conecte o conector da **Atlassian** em Configurações → Conectores e autorize o acesso (Confluence + Jira). É isso que permite a Claude ler este framework e criar a story no final.

1. **Abra o app da Claude** e comece uma nova conversa.
2. **Dê o init do planning-agent** — cole a frase abaixo trocando o produto (banking | ft | backoffice | produto novo):

   ```
   Siga a diretriz do planning-agent do MakeValue IA:
   https://make-value.atlassian.net/wiki/spaces/Cloud/pages/48496641 — refine comigo uma story de banking.
   ```

   A Claude abre essa página, lê a diretriz e o framework do produto, e começa a entrevista — você não cola mais nada.

3. **Descreva sua ideia** livremente. Como a Claude já tem o contexto do produto, ela pergunta só o que falta.
4. **Refine pelo protótipo** — a Claude gera um protótipo navegável com a cara da plataforma. Clique nos estados (vazio, erro, borda); cada ajuste que você pedir atualiza o escopo junto.
5. **Feche e publique** — quando estiver bom, confirme. A Claude cria a **story no Jira** (projeto CLOUD) com o escopo completo e o protótipo num comentário. _Pronto — a story é o entregável; a doc de produto será atualizada na finalização._

**Sempre comece pelo init.** O app da Claude não guarda a diretriz — ele lê a página do Confluence na hora, então você sempre trabalha com a versão mais recente. Não é preciso copiar markdown nem manter instruções salvas.

## Para o time de Dev

**Em breve** — o passo a passo de desenvolvimento e finalização (finalization-agent) será adicionado aqui quando esses agentes forem criados.

Produtos cobertos hoje: **Banking** (documentado), **FT** e **Backoffice** (a preencher). Produtos novos (POC / validação de mercado) entram sem framework histórico.
