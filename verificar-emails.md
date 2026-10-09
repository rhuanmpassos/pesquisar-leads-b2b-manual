# Verificação opcional de e-mails pela Emailable

Use este modo quando o usuário pedir verificação técnica ou leads com e-mails verificados. A pesquisa e a associação do contato à empresa continuam manuais. Consultar um endereço já pesquisado na API autorizada é permitido; não construir coletor, aplicação ou integração. A verificação pode consumir créditos. Não comprar créditos nem alterar cobrança.

## Operar a ferramenta disponível

Confira a [documentação oficial](https://emailable.com/docs/api/emails/) antes de operar. Use conector, ferramenta de HTTP autorizada ou interface disponibilizada pelo ambiente, uma consulta por endereço. Sem ferramenta compatível ou credencial, informe o impedimento; não simule resultados. Não instalar serviço ou desenvolver programa por iniciativa própria.

Se nenhuma API Emailable estiver configurada, peça ao usuário que configure uma credencial privada da Emailable no mecanismo seguro do ambiente. Se a credencial estiver inválida ou expirada, peça uma credencial válida. Não exigir que a chave seja colada em arquivo público ou no texto da skill. Mantenha a verificação pendente até receber uma configuração utilizável; continue somente as etapas independentes da pesquisa.

Endpoint: `GET https://api.emailable.com/v1/verify`. Parâmetros: `email` real publicado, `smtp=true`, `accept_all=true`, `timeout=10`. Consulte cada endereço distinto apenas uma vez. Verifique prioritário e alternativas publicadas que serão entregues. Reconfira o contrato se mudar.

Prefira o cabeçalho `Authorization: Bearer <CHAVE_PRIVADA>` conforme a [autenticação oficial](https://emailable.com/docs/api/authentication/). Use o mecanismo privado de credenciais do ambiente. Nunca colocar chave real em skill, GitHub, planilha, histórico, URL de fonte, captura ou relatório. A chave de teste não executa verificação real. O e-mail de um exemplo de URL não entra automaticamente no lote.

Se receber HTTP `249`, consulte novamente o mesmo endereço dentro de cinco minutos, com tentativas limitadas; preserve o início da consulta. Não repetir indefinidamente. Em `429`, respeite o intervalo informado. Em `401`/`403`, interrompa por autenticação; em `402`, por créditos. Erro HTTP não é e-mail inválido. Consulte [status HTTP](https://emailable.com/docs/api/status-codes/) e [limites](https://emailable.com/docs/api/rate-limits/).

Se saldo esgotado ou limite de uso impedir continuar, salve os resultados concluídos e peça ao usuário que renove o saldo/libere o limite ou configure outra API/credencial da **Emailable**. Não trocar de fornecedor, comprar créditos ou fazer rotação de chaves para contornar limites. Uma nova chave da mesma conta pode compartilhar o saldo esgotado. Um limite temporário de velocidade permite aguardar o prazo informado e tentar novamente de forma limitada; se continuar bloqueado, peça a regularização. Depois que o usuário resolver, teste a configuração em um endereço pendente e retome desse ponto, sem repetir consultas já concluídas. Não entregar pendentes como verificados nem preencher a quantidade com eles.

## Decidir e registrar

Preserve literalmente `state`, `reason`, `score`, `accept_all`, `disposable`, `mailbox_full`, `no_reply` e instante UTC. Quando úteis, retenha MX, provedor SMTP e sugestão de correção. Não guardar gênero, idade ou nomes inferidos pelo verificador; ele não comprova o responsável. Não corrigir endereço automaticamente.

Segundo os [estados oficiais](https://emailable.com/docs/email-verification/email-verification-results/all-possible-states-and-reasons/), `deliverable` indica alta confiança técnica de recebimento; `risky` exige cautela; `undeliverable` indica falha; `unknown` é inconclusivo. HTTP 200 ou score alto isolado não aprovam o e-mail. `accept_all=true` não confirma uma caixa individual. Não prometer entrega futura nem identificação do dono por esse resultado.

Para **novo lote com e-mails verificados obrigatórios**, admitir apenas contato publicado e associado à empresa com `state=deliverable`, sem `accept_all=true`, `disposable=true`, `mailbox_full=true` ou `no_reply=true`. Priorize nominal do dono/sócio dentro dos contatos que passam. Se permitido, use alternativa empresarial verificável; se nenhuma passar, procure outro contato publicado ou outra empresa até completar o lote. Não inventar e-mails ou relaxar o requisito para atingir a quantidade.

Para **reverificar lote já entregue**, manter as empresas e contatos originais. Acrescente resultados e `email_verificado_recomendado`; deixe recomendação vazia se nenhum contato passar. Informe quantos atendem ao novo requisito. Essa reconferência não transforma automaticamente os 30 leads anteriores em 30 leads com e-mail verificado.

Entregue a mesma planilha crua de uma aba. Use colunas de status/motivo/score/flags/data para prioritário e alternativo, provedor, fonte sem credencial e contato recomendado. Atualize o lote existente no histórico privado. Nunca enviar e-mail comercial como teste. Instalar a skill em outra máquina requer configurar a credencial separadamente; não transportar chaves no pacote.
