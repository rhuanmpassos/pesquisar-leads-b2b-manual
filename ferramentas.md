# Ferramentas e operação manual

Este manual descreve a pesquisa manual refinada em outubro de 2026. O universo inicial veio de consultas anteriores à Receita/CNPJ, QSA, filiais e Overture; a conferência final de sites, redes e anúncios foi feita pelo navegador. Não apresentar essas consultas herdadas como novas nem transformar os scripts anteriores no modo de execução desta skill.

## Escolher as ferramentas disponíveis

| Trabalho | Ferramenta preferida | Como usar |
| --- | --- | --- |
| Universo, cadastro, sócios e estabelecimentos | API CNPJ fornecida, por conector de consulta ou interface documentada | Uma consulta documentada por vez, filtros explícitos e paginação. |
| Enriquecimento geográfico | Overture Places disponibilizado por ferramenta, interface ou arquivo existente | Usar site, contatos e redes como candidatos. Registrar release e confirmar cada identidade. |
| Localizar site/perfil | Busca pelo navegador ou ferramenta de busca | Nome, cidade e dado distintivo. Abrir o melhor candidato e conferir. |
| Conferência de site/redes/Meta | Computer Use e navegador conectado | Operar interface pública e ler o que carregou. |
| Contato público de domínio `.br` | Whois oficial do Registro.br; RDAP quando a ferramenta permitir | Consultar domínio validado, comparar contato nominal com QSA. |
| Persistência | Ferramenta de arquivos ou armazenamento privado configurado | Salvar decisões, fontes, checkpoint e histórico. |
| Entrega | Ferramenta/skill de planilhas ou exportação de interface | Uma aba crua com os registros já conferidos. |

Descubra as ferramentas pelo inventário do ambiente. Não supor que existe um MCP CNPJ, Overture ou Meta só porque este documento o menciona. Não substitua ferramenta ausente por código. Se o cadastro necessário não puder ser consultado pela interface/conector, peça a configuração ou um arquivo apropriado e continue as etapas independentes. Se o usuário determinou Overture em lugar de Maps, preserve essa escolha.

## API de CNPJ

O serviço do fluxo original expunha Swagger em `/docs` e OpenAPI em `/openapi.json`, com autenticação Bearer. A URL base e a credencial pertencem à configuração privada do usuário, fora da skill e do GitHub. Confira o contrato atual antes de consultar. Não inserir tokens em URLs, planilhas, screenshots ou logs.

Operações do contrato consultado no trabalho de referência:

| Operação | Caminho | Uso |
| --- | --- | --- |
| Pesquisar estabelecimentos | `GET /v1/empresas` | Nome, raiz, UF, município, situação, CNAE, matriz/filial e paginação. |
| Consultar empresa | `GET /v1/cnpj/{cnpj}` | Cadastro completo do CNPJ candidato. |
| Consultar sócios | `GET /v1/cnpj/{cnpj}/socios` | Pessoas e cargos do QSA. |
| Verificar serviço | `GET /healthz` | Acessibilidade do serviço. Não valida uma empresa. |

Parâmetros de busca conhecidos: `nome`, `raiz`, `uf`, `municipio`, `situacao`, `cnae`, `matriz_filial`, `limite` e `cursor`. O contrato de referência aceitava limite entre 1 e 100 e padrão 20. Confirme valores e formatos no contrato em uso. Não supor que município aceita nome quando exige código. O CNPJ e a raiz são identificadores textuais; preserve zeros iniciais.

Na interface Swagger, expanda a operação, use Try it out, preencha parâmetros, execute e leia resposta/status. Pelo conector, use seus argumentos documentados. Siga o cursor retornado; uma página não é o universo inteiro. Registro de contagem não prova completude sem paginação. Guarde edição da Receita, filtros e origem das consultas, sem payloads sensíveis completos.

Quando exigido **matriz sem filial nacional**, pesquise a raiz de oito dígitos por filiais, sem filtro de cidade, UF ou situação. Uma filial baixada também exclui, conforme esse perfil. Resposta completa sem filiais sustenta a conclusão na edição consultada. Erro, paginação incompleta ou pesquisa só na cidade não sustenta "sem filiais".

A API CNPJ comprova cadastro, não funcionamento do site ou atualidade operacional do contato. Se o endpoint mudar, adapte pelo contrato real; não insistir em parâmetros antigos.

## Pesquisa e site

Procure nome empresarial/fantasia com município e, se necessário, telefone, endereço ou CNPJ. Overture e resultados de busca são pistas. Abra o domínio e confronte identidade com o cadastro. Examine CNPJ no rodapé, endereço, telefone, razão social, responsáveis e links oficiais. Uma página carregada ou HTTP 200 não comprova identidade.

Leia páginas de serviços e segmentos, quem somos, contato, blog, formulário e entradas públicas de portais. Registre o que a interface oferece. Não enviar formulários, iniciar WhatsApp, fazer agendamentos ou entrar em portais de clientes para descobrir a operação.

## Registro.br e e-mails

Abra [Whois do Registro.br](https://registro.br/tecnologia/ferramentas/whois/) e consulte o domínio `.br` validado. No ambiente de referência o Whois abriu, enquanto a tentativa de RDAP pelo navegador foi bloqueada pelo cliente. Isso é uma limitação observada, não garantia de comportamento em outra instalação.

RDAP oficial segue o formato `https://rdap.registro.br/domain/DOMINIO`, quando permitido pela ferramenta. Use somente domínio confirmado. Leia papéis e contatos públicos. Um titular pode ser empresa e o contato técnico ser agência. Não classificar desenvolvedor, hospedagem ou agência como dono. Confirme o nome com QSA ou titular empresário individual.

Se aparecer CPF ou outro documento pessoal, não o copiar para registros ou entrega. Use apenas nome profissional, cargo e contato público pertinente. Respeite limites e falhas. Não rotacionar IP ou burlar proteções. Consulta em cache continua identificada como cache, com data de origem.

Não gerar padrões como nome@dominio, corrigir e-mail por palpite, completar celular antigo ou usar resposta automática de um verificador como prova de propriedade da caixa.

## Instagram e Facebook

Prefira links no site validado. Confira bio/apresentação, domínio, endereço ou contato que ligue o perfil à empresa. Nome parecido e foto parecida não bastam. Uma página homônima, política ou pessoal não é fonte da empresa sem vínculo demonstrado.

Leia bio, destaques, posts fixados e publicações visíveis. Abra Ver mais ou o post relevante quando o resumo estiver incompleto. Registre tema e fatos da legenda ou da imagem efetivamente examinada. Link da publicação é preferível ao link geral do perfil quando disponível. Registre também o limite da análise: bio, legenda, imagem, vídeo integral ou áudio.

Se só houver alguns posts, não inferir frequência editorial. Datas relativas podem ser guardadas junto da data da consulta, sem fabricar data exata. Perfil indisponível não demonstra exclusão, punição ou encerramento da empresa.

## Biblioteca de Anúncios da Meta

1. Abra a página empresarial confirmada. Use Transparência da Página quando necessário para obter seu Page ID. Não inventar ID a partir de perfil ou domínio.
2. Abra a [Biblioteca de Anúncios](https://www.facebook.com/ads/library/). Selecione Brasil e todos os anúncios.
3. Retire o filtro "anúncios ativos". Configure status todos, incluindo ativos e inativos. Confira a seleção visível ou o parâmetro da URL, salvo contradição na tela.
4. Quando o Page ID estiver comprovado, a consulta pode usar `https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=BR&view_all_page_id=PAGE_ID`.
5. Pesquisar por nome serve para encontrar a página. Abra o anunciante correto e confira identidade. Não atribuir os anúncios de outros resultados à empresa candidata.
6. Abra os detalhes dos cartões distintos. Se um aviso esconder o conteúdo, use Ver anúncio quando disponível. Leia também anúncios desabilitados/inativos.
7. Registre ID, status, início/fim, oferta, segmentos citados, tema, CTA, destino e motivo de remoção/encerramento explicitamente informado. Diferencie cada criativo quando houver temas diferentes.
8. Uma contagem aproximada não é quantidade de IDs analisados. Se a tela disser aproximadamente três mas expuser um, registre um analisado e a limitação.

Sem resultados na página, no país e no filtro consultados não significa "nunca anunciou". Página não confirmada, login, erro ou bloqueio significa inconclusivo. Vídeo com player vazio não foi assistido. Legenda não comprova conteúdo do áudio.

Inativo não significa campanha ruim ou falta de orçamento. Um aviso de remoção por ausência de rótulo pode ser registrado como aviso de plataforma. Aviso de conta/página desabilitada posteriormente não demonstra por que um anúncio específico parou em uma data anterior. Se não houver explicação, escreva "motivo não informado pela plataforma".

Não validar promessas tributárias, datas legais ou resultados financeiros do anúncio como fatos atuais do negócio. Registre como alegação do criativo, com período. Não extrair orçamento total, vendas, ROI ou desempenho a partir de poucas horas de veiculação.

## Computer Use no Codex

No ambiente de referência, a operação ocorreu por `mcp__cua_repl.js`, navegador Chrome conectado, DOM snapshots, leitura de texto visível, locators e navegação documentados. Em outra instalação, use a ferramenta equivalente realmente disponível, após ler suas instruções. Não fixar IDs de navegador, aba ou janela desta sessão.

Quando a sessão for retomada, recupere a documentação e o estado antes de interagir. Reuse o navegador selecionado e obtenha aba nova quando a anterior tiver sido fechada. No fluxo de referência isso evitou relançar o navegador e abrir muitas abas.

Uma página pode devolver apenas cabeçalho enquanto carrega. Leia o estado atualizado antes de declarar ausência. Para conteúdo não encontrado, tente a alternativa relevante documentada; não repetir buscas ou cliques sem entender a falha. Respeite login, CAPTCHA, avisos de segurança e políticas do ambiente. Nunca contornar controles para preencher o lote.
