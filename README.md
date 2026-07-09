Diretrizes dos agentes de IA do framework MakeValue IA. Espelha a pasta .agentes/ do projeto. Cada página filha é o prompt de um agente — a Claude lê a página via MCP e age como aquele agente.

Agentes

Agente

Papel

Status

planning-agent

Refinamento de negócio com o PM — gera escopo + protótipo



finalization-agent

Promove o escopo para o framework (Skills) e adiciona doc técnica, após o desenvolvimento



dev-agent

Apoio ao desenvolvimento



review-agent

Revisão



Fluxo do planning-agent

A diretriz completa está na página filha planning-agent. O PM dá o init no app da Claude e o agente percorre estes passos:

Init: Siga a diretriz do planning-agent do MakeValue IA: https://make-value.atlassian.net/wiki/spaces/Cloud/pages/48496641 — refine comigo uma story de banking.

Identificar produto e task — produto existente (banking | ft | backoffice) ou produto novo (POC / validação de mercado, sem histórico). Define um ID no padrão TASK-XXX-nome-curto-produto.

Absorver contexto — a Claude lê via MCP o framework do produto em Skills antes de qualquer pergunta. Produto novo pula este passo.

Entender a ideia — o PM descreve livremente; o agente reformula em 3-5 linhas para confirmar.

Entrevista cirúrgica — pergunta SÓ o que o framework/histórico não responde, e levanta conflitos com regras existentes.

Gerar o escopo — regras numeradas e testáveis (viram critério de aceite).

Gerar o protótipo — entregue como artifact navegável, mostrando os estados (vazio, sucesso, erro, borda) para revelar regras que faltavam.

Loop de refinamento — a cada ajuste do PM, atualiza protótipo e escopo juntos.

Handoff — com a confirmação do PM: cria a story no projeto CLOUD (board 308, tipo História, sem responsável) com o escopo completo na descrição, e adiciona o protótipo num comentário com seção "Expandir" (HTML em code block recolhível — o conector não anexa arquivo). Não cria página de escopo no Confluence — a story do Jira já é a fonte completa; a doc de produto (Skills) é atualizada depois pelo finalization-agent.

O protótipo é uma ferramenta de descoberta, não enfeite: ao clicar nos estados, o PM percebe regras que faltavam. Toda regra revelada volta para o escopo.
