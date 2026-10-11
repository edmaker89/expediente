# Expediente v2 — To Be

Data: 11/10/2026. Estado: direção funcional validada pelo usuário no brainstorm. Lente: especificação de produto e processos. Este documento consolida decisões e justificativas; não é plano de implementação nem desenho de infraestrutura.

## 1. Propósito e fronteiras

O Expediente v2 gerencia documentos produzidos pela organização: preparação, aprovação, assinatura, numeração, emissão, envio e publicação conforme o tipo. Evolui do cadastro de números descrito em `as-is.md` para gestão do documento e de suas evidências.

Atende redação na plataforma com templates e produção externa com controle de numeração. Anexo é opcional no uso como controle; uma etapa de assinatura de arquivo exige que a versão a assinar esteja disponível. Documentos externos podem ser anexados como referência e vinculados à resposta. Não há protocolo de entrada, distribuição ou tramitação de recebidos nesta versão. Integrações com sistemas de protocolo são expansão futura.

## 2. Decisões consolidadas

| Decisão | Escolha | Justificativa | Estado |
|---|---|---|---|
| Organização | Uma instância por cliente, com uma organização e suas unidades | Implantação e atualização controladas por cliente | Decidido |
| Infraestrutura | Compartilhável ou dedicada; fora do escopo técnico atual | Provisionamento enxuto conforme demanda | Decidido |
| Produção | Plataforma ou ferramenta externa; anexo opcional | Preservar também o controle de numeração | Decidido |
| Tipo | Vincula fluxo, série, template, acesso e regras | Preparador escolhe um tipo já configurado | Decidido |
| Classificação | Tags múltiplas em catálogo compartilhado | Pesquisa flexível sem hierarquia rígida | Decidido |
| Numeração | Série compartilhável, anual ou contínua | Tipos com fluxos diferentes podem usar um contador | Decidido |
| Identidade | ID permanente, número oficial separado e IDs de versão | Rastrear documento, versões e evidências | Decidido |
| Configuração | Preservada no processo em andamento | Mudanças não alteram silenciosamente processos existentes | Decidido |
| Aprovação | Hierarquia, pessoa fixa ou ponto focal autorizado | Adaptar responsabilidades por etapa | Decidido |
| Autoaprovação | Permitida por padrão; tipo pode exigir outra pessoa | Atender gestores que preparam e aprovam seus documentos | Decidido |
| Assinatura | Modelos organizacionais ativáveis; todas as assinaturas configuradas obrigatórias | Atender requisitos por tipo e organização | Decidido |
| Correção | Reiniciar rito por versão; retificação ou cancelamento após emissão | Preservar original e decisões | Decidido |
| Envio | Plataforma ou declaração externa; múltiplos destinatários | Atender e-mail e entrega física | Decidido |
| Recebimento | Confirmação pelo destinatário fora do escopo | Limitar v2 ao envio | Decidido |
| Publicação | Obrigatória como última etapa quando marcada no tipo | Seguir exigência por tipo | Decidido |
| Delegação | Ausência/vacância discutidas futuramente | Responsável ausente mantém etapa pendente | Adiado pelo usuário |
| Protocolos | Integração futura com sistemas existentes | Evitar duplicar protocolo de entrada | Adiado pelo usuário |

## 3. Tipos, séries e templates

O tipo descreve o que o documento é e como tramita: nome interno, designação oficial, sigla específica quando aplicável, tags, ativo/inativo, modelo de conteúdo, série vinculada, fluxo, acesso padrão, política de correção e obrigatoriedade de envio/publicação.

Inativar um tipo impede novas escolhas, preservando documentos e históricos. Vários tipos podem compartilhar uma série, por exemplo Ofício padrão e Ofício com análise técnica. O fluxo é fortemente vinculado ao tipo; não há escolha livre de outro fluxo pelo preparador.

A funcionalidade se chama **Numeração de documentos**; cada configuração é uma **Série de numeração**. A série controla contador, reinício anual ou contínuo, quantidade mínima de dígitos e formato da identificação numérica. Não define cabeçalho ou diagramação. Três dígitos mínimos produzem 001, mas não limitam a sequência a 999.

O template vinculado ao tipo apresenta a identificação usando campos: designação, identificação numérica e siglas. Exemplo: `{designacao_tipo} nº {identificacao_numerica} {sigla_orgao}` resulta em **Ofício nº 001/2026 SMS-ATB**. Siglas podem vir do tipo ou da organização/unidade; informações institucionais ficam em seus cadastros, evitando duplicação.

Sem template, o Expediente exibe a identificação e seus componentes para aplicação no arquivo externo. A apresentação não substitui o ID permanente. Os valores atribuídos são preservados; mudanças de sigla ou formato não reescrevem documentos numerados.

## 4. Identidade, numeração e versões

Cada documento recebe ID permanente desde o rascunho. Cada versão tem identificação própria; aprovações, assinaturas, envios e publicações apontam para a versão exata.

| Exigências | Atribuição do número |
|---|---|
| Sem aprovação e assinatura | Ao confirmar emissão |
| Aprovações, sem assinaturas | Após última aprovação, ao emitir |
| Aprovações e assinaturas | Após aprovações, antes da primeira assinatura |
| Assinaturas, sem aprovações | Ao fechar conteúdo para assinatura |

Não se reserva número durante a preparação. Para séries anuais, usa-se o ano do momento da atribuição, mesmo que o rascunho tenha começado antes. Número atribuído não é reutilizado, inclusive após cancelamento. Não se exige sequência sem lacunas.

Antes da emissão, retorno para revisão mantém número já atribuído. A versão anterior fica superada e preservada; a nova versão reinicia todas as aprovações e assinaturas. O ano de um número já atribuído não muda por revisão posterior.

## 5. Fluxo e aprovações

Fluxo geral: rascunho → aprovações exigidas → numeração → assinaturas exigidas → emissão → envio exigido → publicação exigida → conclusão. Etapas não exigidas são omitidas; sem assinaturas, numeração ocorre na emissão.

Cada etapa resolve participantes por hierarquia da organização, pessoa fixa no tipo ou ponto focal escolhido entre pessoas autorizadas. Pode combinar formas em etapas sucessivas. Responsável fixo ausente mantém aprovação aguardando; não há substituição automática. Regras e responsáveis usados devem ficar rastreáveis.

| Regra | Resultado favorável | Resultado desfavorável |
|---|---|---|
| Todos aprovam | Todos aprovam | Uma recusa encerra |
| A maioria aprova | Mais da metade dos participantes definidos aprova | Encerra quando a maioria se torna impossível |
| Qualquer um decide | Primeira decisão aprova | Primeira decisão recusa |

Maioria é calculada sobre participantes definidos, não apenas respondentes. Com quatro pessoas, três aprovações são necessárias; empate não aprova. Ausência de resposta mantém pendência. Resultado decidido encerra a rodada e preserva respostas anteriores.

Recusa exige justificativa; aprovação permite comentário. Qualquer aprovador pode devolver para correção com justificativa, interrompendo a rodada. Recusa encerra o fluxo da versão; devolução solicita ajustes. Ambas permitem nova versão com reinício completo.

Conteúdo em aprovação não pode ser editado. Autoaprovação ocorre quando preparador e aprovador resolvido coincidem, com identificação explícita na auditoria e aplicação da regra coletiva. A flag **Exigir aprovação por outra pessoa**, no tipo, impede essa ação; não permite pular a etapa. Autoaprovação nunca substitui assinatura obrigatória.

## 6. Assinaturas

Cada organização configura modelos de assinatura e os ativa/desativa para seleção no tipo. O tipo define modelos permitidos e signatários/etapas; toda assinatura configurada é obrigatória, sem aprovação por votação substituindo signatários.

Direção funcional: assinatura própria do Expediente, assinatura com certificado digital e integração com serviço contratado pela organização. Integração gov.br é possibilidade condicionada à elegibilidade institucional e homologação, não promessa de acesso universal à API.

Separar nível exigido (simples, avançada, qualificada) de mecanismo/provedor. Assinatura própria não é automaticamente avançada nem adequada a qualquer documento; aceitação depende das normas aplicáveis. Assinante deve conferir a versão numerada, manifestar vontade e ficar vinculado ao conteúdo exato e suas evidências.

Após assinatura, não regenerar ou sobrescrever o original assinado. Múltiplas assinaturas precisam preservar anteriores no mesmo artefato ou no conjunto de evidências suportado pelo mecanismo. Ordem sequencial/paralela e combinações entre provedores serão detalhadas na especificação, conforme compatibilidade. Correção de conteúdo reinicia o rito; assinaturas anteriores permanecem associadas à versão superada.

## 7. Emissão, cancelamento e retificação

Emitido significa que concluiu exigências internas, sem implicar envio ou publicação. Após emissão, tipo define retificação vinculada ou cancelamento com nova emissão.

Retificação tem identificação própria e cumpre novamente todo o rito necessário, incluindo assinaturas, envio e publicação exigidos. O original pode apresentar uma nova versão consolidada, marcada como retificada e vinculada à retificação, após concluir as exigências aplicáveis. Essa versão é um arquivo separado: o original emitido/assinado permanece preservado. Não basta aprovação se houver assinaturas obrigatórias.

Cancelamento preserva registro, número, motivo e histórico; nova emissão recebe novo número e vínculo com o documento cancelado.

## 8. Acesso e publicação

Alcances internos: participantes do processo, unidades/grupos autorizados ou organização inteira. Tipo define padrão. Participação concede apenas acesso necessário; hierarquia não libera automaticamente documentos restritos.

Direção da matriz de permissões, confiada pelo usuário ao desenho: criação, aprovação, assinatura, envio/declaração, publicação, cancelamento, retificação, compartilhamento e administração são capacidades distintas. Administrar configurações não concede automaticamente leitura irrestrita. Mudanças de acesso e ações ficam auditadas; auditoria tem acesso controlado.

Publicação pública permite consulta sem autenticação apenas ao material explicitamente publicado. A flag **Exige publicação pública** no tipo torna a publicação obrigatória e última etapa. Organização usa portal próprio ou integração externa. Confirmar publicação registra versão, responsável, data e endereço; falha mantém emitido e aguardando publicação, com nova tentativa e histórico.

Usuário exige que ofícios publicados não exponham dados pessoais ou violem LGPD. Prever revisão explícita por responsável autorizado, inclusive anexos, e cópia apropriada para publicação quando necessário, mantendo original. Não presumir garantia automática de conformidade nem confundir restrição operacional com classificação legal de sigilo. Matriz detalhada e procedimentos de revisão serão especificados posteriormente.

## 9. Envio e evidências

Tipo define envio obrigatório ou dispensado. Permitir envio de e-mail na plataforma e declaração de envio externo (físico, correios ou outro sistema), com múltiplos destinatários e situação por destinatário.

Estados distinguem tentativa, entrega técnica confirmada ao servidor destinatário, falha, ausência de confirmação e envio declarado. Entrega técnica não comprova leitura ou recebimento pessoal. Provedor deve oferecer eventos adequados; ausência de erro não é prova de entrega.

Falha alerta responsável e mantém pendência. Ausência de retorno após prazo permite tratamento manual; prazo é configurável, com valor padrão a definir tecnicamente. Declaração manual preserva tentativa falha e informa canal efetivamente utilizado, destinatário, data do envio, versão, justificativa, responsável e eventual comprovante.

Texto de confirmação: “Declaro que realizei o envio desta versão do documento ao destinatário informado, pelo meio e na data registrados. Sou responsável pela veracidade desta informação.”

Interface diferencia envio declarado de entrega técnica automática. Confirmação de recebimento pelo destinatário não integra esta versão.

## 10. Operação por cliente

Uma instância lógica por cliente: aplicação, banco, arquivos, configurações e versão separados. Recursos físicos podem ser compartilhados ou dedicados. Homologação é ambiente separado e opcional. Atualizações seguem versão e janela por cliente, mantendo produto comum e evitando forks de código por contrato.

VPS, clusters, IaC, CI/CD de provisionamento, preços, capacidade e políticas comerciais não são definidos por este To Be. Um segundo cliente não implica cluster automaticamente.

## 11. Detalhamento posterior e itens adiados

Detalhar antes de implementar: escopo de cada contador e associação à hierarquia; unicidade/concorrência; resolução de responsáveis sem cadastro; modelos de assinatura, provedores e elegibilidade gov.br; preservação e validação de múltiplas assinaturas; matriz de acesso; regras de cópia pública; tratamento de falhas parciais com múltiplos destinatários; prazo padrão de e-mail; identificação da retificação e relação com versão consolidada; formato de evidências e retenção.

Esses detalhes não anulam decisões validadas e não devem virar comportamentos implícitos. Delegação por ausência/vacância e integração com protocolos foram adiadas pelo usuário. Não há definição de backlog, stack final, cronograma ou promessa jurídica de conformidade.

## 12. Referências consultadas no brainstorm

Consultadas em 11/10/2026; revalidar condições externas durante implementação:

- Lei 14.063, níveis de assinatura e aceitação por entes públicos: https://www.planalto.gov.br/ccivil_03/_ato2019-2022/2020/lei/l14063.htm
- MP 2.200-2, art. 10, outros meios de autoria/integridade: https://www.planalto.gov.br/ccivil_03/mpv/antigas_2001/2200-2.htm
- Assinatura gov.br para órgãos, contas prata/ouro: https://www.gov.br/governodigital/pt-br/identidade/assinatura-eletronica/assinatura-eletronica-para-orgaos
- Condições institucionais de integração gov.br: https://www.gov.br/governodigital/pt-br/estrategias-e-governanca-digital/transformacao-digital/servico-de-integracao-aos-produtos-de-identidade-digital-gov.br
- Preservação e verificação de assinaturas: https://validar.iti.gov.br/guia.html
- Eventos de entrega de e-mail e falhas posteriores: https://docs.aws.amazon.com/ses/latest/dg/notification-contents.html

Essas fontes suportam distinções externas (estado Verificado na data da consulta); não são decisões automáticas de produto nem parecer jurídico.
