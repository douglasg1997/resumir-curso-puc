---
name: resumir-curso-puc
description: Percorre disciplinas da plataforma PUC/Plataforma A usando a sessão autenticada do navegador, mapeia semanas e unidades, extrai e sintetiza o conteúdo textual, organiza atividades formativas e orientações de avaliações quando solicitado e gera cadernos e resumos profissionais em Word. Use quando o usuário pedir para compilar, estudar, resumir, documentar ou transformar em DOCX o conteúdo de uma matéria ou curso da PUC.
---

# Resumir curso PUC

Executar a leitura sistemática de uma disciplina e entregar documentos Word organizados, completos e visualmente verificados.

## Preparar o trabalho

1. Usar a skill de controle do navegador compatível com a sessão autenticada do usuário e ler integralmente suas instruções.
2. Usar também a skill de documentos e seguir seu fluxo obrigatório de criação, renderização e verificação.
3. Descobrir pela tela o nome da disciplina, sua estrutura e a pasta de saída. Perguntar somente quando isso não puder ser inferido com segurança.
4. Nomear a sessão do navegador e reivindicar apenas a aba do curso indicada pelo usuário.
5. Informar que nenhuma resposta, tentativa ou entrega será enviada sem autorização explícita.

## Mapear antes de extrair

1. Inventariar todas as semanas, unidades, materiais textuais, atividades formativas e áreas de avaliações.
2. Associar cada cartão ao contêiner da semana correspondente; não inferir a semana apenas pela ordem visual.
3. Registrar título, tipo, estado, identificador e destino de cada item.
4. Distinguir conteúdo estático, questionário já respondido, questionário ainda não iniciado, arquivo e link externo.
5. Não iniciar tentativas não realizadas, não marcar itens como concluídos e não clicar em envio.

## Coletar o conteúdo

1. Percorrer as semanas em ordem e abrir cada unidade de conhecimento.
2. Aguardar transições de aplicações de página única antes de capturar o texto; confirmar o título do item aberto.
3. Extrair apenas o conteúdo acadêmico. Remover menus, avisos globais repetidos, navegação e elementos decorativos.
4. Ignorar imagens e vídeos, salvo texto disponível como legenda, transcrição ou descrição acessível.
5. Produzir síntese fiel em vez de reproduzir integralmente material protegido. Preservar conceitos, exemplos, procedimentos, números, requisitos e relações importantes.
6. Manter rastreabilidade por disciplina, semana e unidade. Registrar claramente qualquer item inacessível.
7. Em questionários já concluídos, resumir perguntas, conceitos e feedback. Em questionários não iniciados, parar na tela anterior à criação da tentativa, salvo autorização expressa.

## Tratar atividades e avaliações

Quando o usuário incluir atividades formativas, organizar cada uma por semana com: cenário, objetivo, perguntas centrais, entregável esperado e relação com o projeto acumulado.

Quando o usuário pedir orientação de uma avaliação, localizar a área oficial de atividades somativas e extrair: tarefa, partes obrigatórias, formato, critérios explicitados, recursos permitidos, prazo, pontuação e modo de entrega. Transformar essas informações em checklist sem realizar a atividade nem submetê-la.

## Gerar os documentos

Ler [references/output-spec.md](references/output-spec.md) antes de criar os arquivos.

Por padrão, criar na pasta solicitada:

- `Caderno_de_Estudos_<Disciplina>.docx`: conteúdo detalhado por semana e unidade.
- `Resumo_<Disciplina>.docx`: síntese transversal, conceitos essenciais e checklist de revisão.

Se atividades formativas forem uma etapa separada, criar adicionalmente:

- `Caderno_de_Atividades_Formativas_<Disciplina>.docx`.
- `Resumo_e_Checklist_<Avaliacao>_<Disciplina>.docx`, quando houver orientação avaliativa.

Usar nomes de arquivo seguros, preservar acentos no texto e evitar sobrescrever arquivos existentes sem necessidade.

## Verificar e entregar

1. Renderizar cada DOCX conforme a skill de documentos.
2. Inspecionar visualmente todas as páginas e corrigir cortes, páginas vazias evitáveis, títulos órfãos, tabelas quebradas e margens inconsistentes.
3. Conferir que todas as semanas mapeadas aparecem no caderno ou estão registradas como sem conteúdo textual.
4. Confirmar os arquivos finais na pasta de saída.
5. Resumir ao usuário o que foi encontrado, destacar exigências de avaliações e fornecer citações clicáveis dos documentos.

## Regras de segurança operacional

- Não responder avaliações, não selecionar alternativas, não enviar formulários e não fazer entregas sem pedido explícito.
- Não alterar progresso deliberadamente. Se apenas abrir um item modificar o progresso automaticamente, avisar o usuário.
- Não expor credenciais, tokens, dados pessoais ou informações de outras disciplinas.
- Se a sessão expirar ou uma tentativa precisar ser iniciada para revelar conteúdo, interromper essa parte e solicitar decisão do usuário.
- Confirmar prazos na plataforma no momento da consulta e indicar que podem mudar.

