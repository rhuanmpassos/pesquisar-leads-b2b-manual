# Planilha crua e histórico privado

## Uma única entrega

Entregue um arquivo de planilha com uma aba, cabeçalhos na primeira linha e uma linha por empresa aprovada. XLSX é o padrão; CSV quando solicitado ou quando a exportação disponível exigir, com formato explicitado. Não entregar os dois por iniciativa própria.

Sem cores, negrito decorativo, título/capa, células mescladas, tabelas estilizadas, gráficos, fórmulas, linhas de resumo ou abas de pendentes/reprovados. Não inserir ganchos, perguntas de abordagem, assunto de e-mail ou texto comercial. As fontes ficam em colunas da própria linha.

Preserve CNPJ, raiz e telefone como texto, inclusive zeros iniciais. Use datas ISO `AAAA-MM-DD`. Preserve e-mail e URL reais sem corrigir por palpite. Campo de contato opcional ausente pode ficar vazio. Em campos de análise use estados específicos de indisponibilidade/inconclusão quando necessário; não transformar ausência em uma conclusão negativa.

## Cabeçalhos recomendados

Adapte os campos adicionais ao pedido, mantendo nomes estáveis para o bot de e-mails. Não trocar campos de fatos por uma coluna única de redação persuasiva.

| Grupo | Colunas |
| --- | --- |
| Identidade | `empresa`, `cnpj`, `razao_social`, `cnae`, `municipio_uf`, `site` |
| Responsável | `responsavel`, `vinculo`, `fonte_responsavel` |
| Contato | `email_prioritario`, `tipo_email`, `email_alternativo`, `observacao_email_alternativo`, `telefone`, `tipo_telefone` |
| Fontes do contato | `fonte_email_prioritario`, `fonte_email_alternativo`, `fonte_telefone` |
| Canais | `instagram`, `facebook` |
| Fatos por canal | `constatacoes_site`, `constatacoes_instagram`, `constatacoes_facebook`, `constatacoes_anuncios` |
| Fontes por canal | `fontes_constatacoes_site`, `fontes_constatacoes_instagram`, `fontes_constatacoes_facebook` |
| Meta | `status_anuncios_meta`, `ids_periodos_anuncios`, `motivo_inativacao_informado`, `biblioteca_meta_status_todos` |
| Recência e alcance | `data_conferencia_web`, `base_cadastral_qsa_filiais`, `verificacao_contatos`, `alcance_analise_redes` |
| Estrutura, se exigida | `matriz_sem_filiais`, `fonte_consulta_filiais` |

Para preservar uma integração existente, mantenha nomes como `telefone_fixo` e `fonte_telefone_fixo` em lotes que exigem fixo. Vários fatos na mesma célula podem ser separados por quebras de linha. Quando houver vários anúncios, vincule cada descrição a seu ID/período para que outro bot não associe o tema ao criativo errado.

Estados Meta: ativos encontrados, inativos encontrados, ativos e inativos encontrados, sem resultados visíveis no recorte, inconclusivo ou não verificado. Acrescente quantidade efetivamente analisada, sem usar o contador aproximado como total confirmado. "Motivo não informado pela plataforma" é uma constatação válida. Não preencher "campanha fracassou" ou "faltou verba" por inferência.

## Registro privado durante a pesquisa

Use a ferramenta de arquivos/armazenamento privado. Salve fatos estruturados e um checkpoint após pequenas sequências de empresas, para retomar sem depender da memória da conversa. Registre o candidato atual, aprovados, faltantes até a meta, candidatos já examinados e consultas cuja validação faltou. Não repetir pesquisa já concluída por perda de contexto.

Arquivos privados sugeridos:

- `config-pesquisa.md`: URL do serviço CNPJ, ferramentas disponíveis, perfil do usuário e caminho persistente do histórico. Credenciais ficam no mecanismo seguro do ambiente, não nesse arquivo.
- `historico-leads-entregues.json`: lotes entregues e chaves de comparação.
- `candidatos-consultados.json`: controle interno de aprovados, excluídos, duplicatas e pendências, com motivos e data.
- `checkpoint-pesquisa.md`: estado do lote em execução.

Esses são registros de dados, não scripts. Não criar banco/serviço de automação para implementar o histórico. Use um local persistente informado/configurado pelo usuário, fora do repositório público e fora de uma pasta temporária de chat. Não atualizar a memória global do Codex por iniciativa própria.

## Evitar repetição entre semanas, cidades e máquinas

Leia todos os lotes entregues antes de escolher candidatos. Compare CNPJ completo, raiz de oito dígitos, domínio principal normalizado, marca, e-mail e telefone. Remover `www.` do domínio ajuda a comparação, sem confundir domínios distintos. CNPJ igual é repetição. Mesma raiz ou marca/domínio/contato compartilhado exige verificar se é a mesma operação; não duplicar uma marca com outro CNPJ.

Contatos de prestadores compartilhados podem produzir falso positivo de duplicata. Examine a identidade antes de excluir automaticamente por um único e-mail/telefone. Não inventar pontuação ou deduplicador em código.

Cada lote deve guardar identificador, data, cidade/UF, segmento, critérios, arquivo entregue e lista das empresas com CNPJ, raiz, domínio, marca e contatos escolhidos. Atualize o lote existente ao corrigir uma entrega; não transformar uma correção em novo envio de empresas.

Candidatos só examinados não são automaticamente "já entregues". Mantenha sua decisão para poupar trabalho, mas a exclusão de repetição usa o histórico de entregas. Um pedido de reconferência pode revisitar o mesmo lote sem contaminar a contagem de novos leads.

Instalar a skill em outra máquina **não transporta o histórico**. Configure o mesmo armazenamento privado ou transfira o histórico separadamente com autorização do usuário. Se estiver ausente, não afirmar que a seleção é inédita em relação a outras máquinas/chats. Informe essa limitação e solicite o histórico quando evitar repetição depender dele.

## Conferência final

Confirme quantidade exata, identidade de cada empresa, contatos exigidos preenchidos, fontes, tipo de telefone, vínculo do e-mail, zeros de CNPJ preservados, ausência de duplicatas e ausência de redação de abordagem. Confirme que Meta foi consultada em status todos nas páginas verificadas e que as limitações de vídeo/áudio estão descritas quando relevantes.

Se o ambiente tiver validação de planilha, use-a para verificar integridade local do arquivo, sem transformar a validação em nova coleta ou classificador. Reabra ou inspecione o arquivo salvo. Não declarar exportação concluída só por ter tentado salvar.

O histórico só recebe os aprovados realmente incluídos na entrega. Pendentes e excluídos ficam no controle privado. A resposta final deve apontar a única planilha, informar o tamanho do lote e resumir os limites materiais de verificação, sem anexar controles internos ou repetir todos os dados no chat.
