---
name: pesquisar-leads-b2b-manual
description: Pesquisar e conferir manualmente empresas brasileiras para entregar um lote de leads B2B com CNPJ, responsáveis, contatos e constatações por canal em uma única planilha crua. Usar em pedidos de prospecção por cidade e segmento. Não redigir nem enviar e-mails comerciais.
---

# Pesquisar leads B2B manualmente

Atue como pesquisador que opera as ferramentas fornecidas, examina cada empresa e decide com base em evidências. Entregue a quantidade solicitada de empresas que atendem aos requisitos. O trabalho termina na pesquisa e na entrega das constatações. Outro bot escolhe a personalização e escreve os e-mails.

Leia [ferramentas.md](ferramentas.md) antes de operar os serviços, [criterios.md](criterios.md) antes de admitir candidatos e [entrega-e-historico.md](entrega-e-historico.md) antes de começar o lote e ao exportar.

Quando o pedido incluir e-mails verificados ou reconferência técnica, leia [verificar-emails.md](verificar-emails.md). Esse modo usa a API Emailable autorizada para consultar contatos já pesquisados. Contato publicado e contato tecnicamente entregável são verificações distintas. Em novo lote com verificação obrigatória, complete a quantidade apenas com contatos que passam pelo critério técnico; em reconferência de lote existente, preserve os registros e exponha o resultado real de cada e-mail.

## Modo de execução

- Faça a pesquisa empresa por empresa com navegador/Computer Use, busca e conectores já disponíveis. Leia a documentação das ferramentas realmente expostas no ambiente.
- Não crie crawler, scraper, bot, extensão, integração, script de pesquisa ou coletor em lote. Não use Python, Node, shell, Playwright externo, requisições em scripts ou análise automática de páginas para substituir a conferência manual.
- Chamadas individuais a ferramentas de consulta CNPJ são permitidas. Navegar, clicar, ler DOM visível, examinar imagens e usar locators documentados dentro de Computer Use são formas de operar a ferramenta, não motivo para construir um programa de pesquisa.
- O pacote não exige código. Para salvar arquivos use ferramentas de arquivos; para planilhas prefira o recurso próprio do ambiente. Se o ambiente só gera XLSX por sua skill de planilhas, limite esse uso à serialização local dos fatos já conferidos. Nenhuma coleta pela rede, inferência ou seleção de candidatos deve ficar nesse código. Se o usuário proibir também essa serialização, use exportação pela interface ou CSV, explicitando o formato.
- Nunca execute scripts de pesquisas anteriores. Seus resultados podem ser fontes herdadas, com origem e data identificadas, e precisam de reconferência nos campos obrigatórios do novo lote.
- Feche as abas da empresa anterior antes de pesquisar a seguinte. Reutilize abas para site, redes e Meta da empresa atual. Preserve as abas pessoais do usuário.

## Definir o pedido sem transformar preferências em filtros

Extraia do pedido e do contexto: quantidade, cidade/UF, segmento/CNAE, contatos obrigatórios, preferência de destinatário, restrições de domínio/estrutura e localização do histórico persistente. Pergunte apenas o que não puder ser inferido e impedir a seleção correta.

| Pedido | Regra de admissão |
| --- | --- |
| "Número fixo" | Exigir fixo publicado em fonte empresarial. Celular ou WhatsApp móvel não substitui. |
| "Telefone" | Aceitar fixo ou celular/WhatsApp empresarial publicado, com tipo explícito. |
| "E-mail do dono, ou da empresa se não achar" | Procurar nominal ligado ao responsável primeiro. E-mail empresarial é alternativa aceita. |
| "Somente e-mail do dono" | E-mail empresarial genérico não satisfaz. Não inventar uma associação para completar o lote. |
| Nenhum requisito de e-mail/telefone | Procurar e registrar os contatos úteis. Não tornar um campo obrigatório por iniciativa própria. |
| "30 leads" | Entregar 30 empresas aprovadas pelos critérios, não 30 registros incluindo pendentes. |

CNPJ, identidade empresarial, localização e responsável identificado são o padrão deste fluxo, salvo ajuste explícito do usuário. Empresa ativa e site próprio acessível são o perfil padrão. No perfil original de contabilidades havia exigência de matriz sem qualquer filial no Brasil; mantenha quando esse perfil estiver configurado, não aplique silenciosamente a todos os setores. Restrições a `.com.br`, CNAE principal específico e ausência de filiais precisam vir do pedido ou da configuração do perfil. Não exigir `.com.br` para o endereço de e-mail: responsáveis podem publicar Gmail, Terra, Yahoo e outros provedores.

Anúncios não aprovam nem reprovam um lead por si só. Inclua quem anuncia e quem não apresenta resultados, salvo filtro explícito diferente.

## Executar o lote

1. Localize a configuração privada das fontes e do histórico. Leia `config-pesquisa.md` na pasta desta skill, se existir, ou a configuração disponibilizada pelo usuário/contexto. Leia os lotes já entregues antes de pesquisar. Conte somente empresas novas e distintas. Históricos de diferentes cidades e chats também contam.
2. Descubra candidatos pela API CNPJ fornecida. Use Overture como enriquecimento quando disponível. Busca na web pode localizar site e canais, mas o snippet não aprova o lead.
3. Confira situação, município, atividade e matriz/filiais conforme o perfil. Consulte QSA ou nome empresarial do titular. Registre a edição dos dados.
4. Abra o site oficial e confirme sua identidade. Leia quem somos, serviços, contato, páginas de segmentos, formulários e áreas públicas do cliente. Não entre em áreas privadas de clientes.
5. Procure o e-mail nominal do responsável no site e no contato público de domínio. Cruze com QSA/nome empresarial. Depois procure contato empresarial. Confira o telefone solicitado e sua fonte.
6. Abra os perfis oficiais de Instagram e Facebook. Leia bio, destaques e uma amostra de publicações disponíveis. Abra publicações relevantes quando o texto resumido esconder a informação. Registre fatos específicos, canal, fonte e limitações.
7. Na Biblioteca de Anúncios da Meta identifique a página correta, selecione Brasil, todos os anúncios e **status todos**. Retire "anúncios ativos" toda vez que aparecer. Examine também inativos e anúncios sob avisos.
8. Registre conteúdo e operação observados. Não escreva ganchos, perguntas de abordagem, assuntos, textos de e-mail, recomendações de venda ou diagnósticos de dor.
9. Aplique a decisão de admissão. Se falta um requisito obrigatório, resolva a falta ou substitua o candidato. Registre excluídos e pendentes apenas no controle privado, não na planilha entregue.
10. Continue buscando até atingir a quantidade. Ao terminar, revise duplicatas e fontes, exporte uma única planilha crua e atualize o histórico privado com o lote realmente entregue.

## Constatações que outro bot pode usar

Separe site, Instagram, Facebook e anúncios. Prefira frases independentes que identifiquem o fato e sua origem. Registre, por exemplo: segmentos citados, especialidades, sócios apresentados, equipes por departamento, portais e aplicativos divulgados, campos do formulário, condições de abertura, eventos, vagas, temas dos posts, oferta do anúncio e chamada para ação.

Correto: "O site separa contatos de comercial, fiscal e departamento pessoal." "A bio menciona supermercados e hortifruti." "O anúncio oferece ingresso para evento tributário e tem botão Saiba mais."

Não escrever: "Como vocês organizam os contatos?" "Vocês precisam de um bot." "A empresa deve estar sobrecarregada." Um portal divulgado não comprova uso ou funcionamento; uma vaga publicada não prova crescimento; um criativo inativo não comprova falta de verba.

Para afirmar tema predominante, examine amostra suficiente e identifique seu alcance. Com apenas alguns posts, escreva "publicações observadas tratam de...", não "falam mais sobre...". Números de clientes e anos de atuação são declarações da empresa, salvo confirmação independente.

## Encerrar com precisão

Não declare "100% de certeza" nem invente pontuação de qualidade. A aprovação significa que os critérios verificáveis foram atendidos com fontes. Contato publicado não comprova recebimento de e-mail ou atendimento da linha. Não faça envio comercial ou ligação de teste como parte desta skill.

Uma fonte inacessível não autoriza inventar fatos. Se faltar dado obrigatório de um candidato, não o entregue. Se houver impedimento real para completar todo o lote, preserve o trabalho, descreva o impedimento e a quantidade validada; não relaxe critérios nem anuncie que entregou a quantidade solicitada. Falta de informação opcional nas redes/Meta pode ser registrada sem invalidar contatos e identidade já comprovados.
