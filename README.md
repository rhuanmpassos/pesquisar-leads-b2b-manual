# Pesquisar leads B2B manualmente

Skill para uma IA pesquisar empresas brasileiras, conferir CNPJ e responsáveis, procurar contatos empresariais e registrar constatações de site, Instagram, Facebook e Biblioteca de Anúncios da Meta. A entrega é uma única planilha crua com a quantidade de empresas que passou pelos critérios do pedido.

A IA opera as ferramentas disponíveis e toma decisões empresa por empresa. O pacote não contém crawler, scripts, aplicação ou serviço de pesquisa. Também não escreve nem envia e-mails. O bot de e-mails recebe os fatos e decide a personalização.

## Arquivos

- [SKILL.md](SKILL.md): instruções de execução e limites.
- [ferramentas.md](ferramentas.md): ferramentas, contrato CNPJ de referência e operação manual de navegador, Whois, redes e Meta.
- [criterios.md](criterios.md): identidade, responsáveis, contatos e decisões de admissão.
- [entrega-e-historico.md](entrega-e-historico.md): formato cru, fontes, persistência e prevenção de repetição.
- [verificar-emails.md](verificar-emails.md): modo opcional Emailable, resultados técnicos, critérios de aceitação e credencial privada.

## Instalar

No Codex com instalador de skills, peça:

> Use a skill-installer para instalar a skill da raiz de https://github.com/rhuanmpassos/pesquisar-leads-b2b-manual com o nome pesquisar-leads-b2b-manual.

Alternativa manual: baixe o ZIP do repositório e coloque seu conteúdo em uma pasta chamada `pesquisar-leads-b2b-manual` dentro de `$CODEX_HOME/skills`. Sem `CODEX_HOME`, a localização usual é `~/.codex/skills/pesquisar-leads-b2b-manual`, inclusive em Windows. `SKILL.md` deve ficar diretamente nessa pasta, junto dos documentos que ele referencia. A skill pode ser usada no próximo turno após a instalação.

Em outro ambiente de IA, carregue `SKILL.md` e mantenha os documentos relativos disponíveis. As ferramentas de navegador, CNPJ, arquivos e planilhas precisam existir naquele ambiente; a skill não as instala.

## Configurar antes do primeiro lote

Informe ou disponibilize em configuração privada: cidade/segmento padrão, exigências de matriz/filiais e domínio, ferramenta/URL da API CNPJ e pasta persistente do histórico. Autenticação do serviço deve ficar no mecanismo seguro do ambiente. A documentação de referência descreve as operações da API sem publicar a URL particular nem credenciais.

Use um histórico privado comum entre pesquisas. Ao mudar de máquina, transfira esse histórico separadamente ou configure o mesmo armazenamento. Este repositório não contém os leads do teste, e-mails coletados, histórico real ou arquivos de configuração particulares.

## Exemplos de uso

> Use $pesquisar-leads-b2b-manual e procure 30 contabilidades em Itapetininga/SP, com número fixo e e-mail de preferência do titular ou sócio. Se não encontrar nominal confirmado, pode usar o da empresa. Use meu histórico para não repetir empresas e entregue uma única planilha crua com constatações e fontes.

> Use $pesquisar-leads-b2b-manual e procure 20 empresas do segmento informado em Sorocaba/SP que tenham telefone empresarial, podendo ser fixo ou WhatsApp. E-mail é desejável, não obrigatório. Não escreva ganchos nem e-mails.

Na Meta, o padrão é sempre Brasil, todos os anúncios e status todos. Anúncios inativos são examinados. O motivo de inativação só é registrado quando a plataforma o informa.

Para exigir verificação técnica, acrescente ao pedido: "Exija e-mails verificados pela Emailable, usando minha credencial privada configurada. Complete o lote apenas com contatos entregáveis pelo critério da skill." O verificador não confirma titularidade. A credencial precisa ser configurada separadamente e não acompanha este repositório.

## O que a aprovação significa

O lead atende aos critérios verificáveis do pedido e tem fontes. Não existe promessa de 100% de certeza, recebimento de e-mail, atendimento da linha, faturamento ou interesse em comprar. Se um candidato falhar em um requisito obrigatório, a IA procura outro. Não preenche a quantidade com pendentes ou duplicatas.
