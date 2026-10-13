# HOF Hub — gestão para clínicas de harmonização orofacial

Experiência como desenvolvedor full-stack no **HOF Hub**, SaaS da Arco para clínicas de harmonização orofacial (outubro de 2026).

> O código do HOF Hub é proprietário da Arco e não está neste repositório. Aqui fica a descrição do que construí. Posso mostrar o trabalho numa conversa, mediante autorização da empresa.

## O produto

Sistema web (PWA) que a clínica usa no dia a dia: agenda, prontuário da paciente, financeiro, estoque de insumos, CRM com WhatsApp, contratos com assinatura, metas e KPIs, e uma assistente de IA (a sócIA) que conversa com os dados da clínica.

## Minha contribuição

De 01 a 13 de outubro de 2026, na branch principal:

| | |
|---|---|
| Commits | 169 |
| Tarefas do quadro entregues | 112 |
| Funcionalidades (`feat`) | 73 |
| Correções (`fix`) | 76 |
| Testes, manutenção e docs | 19 |

Cada tarefa seguiu o mesmo caminho: card no quadro → branch → merge request com pipeline verde → revisão → merge. Mudanças de banco entravam com migration, o back antes do front.

### Destaques por área

**Financeiro**
- Limite de crédito do cartão da clínica, descontado a cada lançamento, e despesa paga em duas formas quando o limite não cobre.
- Antecipação da fatura do cartão (valor parcial ou total), com o limite voltando na hora.
- Limite de gastos por conta no mês, com confirmação ao passar do teto.
- Visão geral dividida em "Neste período" e "Em aberto", com filtro Hoje / Semana / Mês / Ano / Personalizado.
- Aba de cobranças: quem deve, quanto, e a cobrança enviada pelo WhatsApp.
- Taxa da maquininha por parcela e ticket médio por paciente nas metas.

**Estoque**
- Produto fracionado: um frasco ou caixa atende várias pacientes, com custo por unidade e lucro de cada serviço.
- Lote e validade escolhidos na entrada e na saída; lotes visíveis na lista do estoque.
- Tipo do produto (unidade, caixa, frasco em ml ou em U).

**Prontuário**
- Aba Evolução: ml aplicado por sessão, com o estoque ajustado pela diferença e uma prévia do que vai mudar.
- Carimbo digital do profissional na evolução, contratos da paciente em cards e fotos/vídeos com categorias da clínica.

**CRM e conversas (WhatsApp)**
- Confirmação de leitura (✓, ✓✓, ✓✓ azul) recebida por webhook e entregue à tela em tempo real (SSE).
- Encaminhar mensagens, baixar mídia, foto nas mensagens automáticas e procedimentos de interesse do lead.
- Aviso sonoro e notificação do sistema quando chega mensagem com o app em outra aba.

**Agenda**
- Horário de funcionamento com intervalo de almoço, bloqueado na grade, e compromisso pessoal com cara de bloqueio.

**Internacionalização**
- Botão PT/EN. Para traduzir áreas inteiras sem reescrever cada componente, um tradutor da tela (MutationObserver + dicionário) troca os textos à medida que a página muda.

**Segurança e confiabilidade**
- Permissões por papel (administrador, doutora, recepção) e isolamento de dados entre clínicas.
- Escape de HTML nos e-mails, limite de tamanho de corpo nas rotas públicas e dados sensíveis fora dos logs de erro.
- Datas e lembretes no fuso de Brasília, consultas sem limite escondido de 1.000 registros, exclusões que não deixam dados órfãos.

**Qualidade**
- Testes de serviço no back com Vitest.
- Régua de avaliação da IA: 113 frases com nota por ferramenta e um portão que reprova regressão contra o baseline.
- QA de ponta a ponta com Playwright e um mapa do código por partes para orientar as mudanças.

## Stack

- **Front:** React 19, TypeScript, Vite, Tailwind CSS, TanStack Query, React Router, Recharts, PWA
- **Back:** Node.js, Express, TypeScript, Prisma, PostgreSQL, Redis, Zod, JWT
- **Integrações:** WhatsApp (Evolution API), Google Agenda, Stripe, e-mail (Resend), S3, Sentry, LLMs (Groq, OpenAI, Gemini)
- **Testes e entrega:** Vitest, Playwright, GitLab CI
- **Ferramentas:** Git, Claude Code como par de programação
