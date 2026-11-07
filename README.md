# resumir-curso-puc

Skill para o Codex que percorre disciplinas da PUC/Plataforma A usando uma sessão autenticada do navegador, organiza o conteúdo por semana e gera documentos profissionais em Word.

## O que a skill faz

- identifica a disciplina aberta no navegador;
- mapeia todas as semanas, unidades e materiais textuais;
- sintetiza o conteúdo acadêmico sem reproduzir imagens ou vídeos;
- organiza atividades formativas por semana;
- extrai orientações oficiais de atividades somativas quando solicitado;
- gera caderno de estudos, resumo e documentos de atividades em `.docx`;
- renderiza e inspeciona visualmente os documentos antes da entrega;
- informa quando a simples abertura de materiais altera automaticamente o progresso do curso.

Arquivos gerados por padrão:

```text
Caderno_de_Estudos_<Disciplina>.docx
Resumo_<Disciplina>.docx
Caderno_de_Atividades_Formativas_<Disciplina>.docx
Resumo_e_Checklist_<Avaliacao>_<Disciplina>.docx
```

O último arquivo é criado quando o usuário solicita a orientação de uma avaliação.

## Proteções incorporadas

A skill não deve:

- responder avaliações em nome do estudante;
- selecionar alternativas;
- iniciar tentativas ainda não realizadas;
- marcar itens como concluídos;
- enviar atividades ou formulários;
- copiar integralmente material acadêmico protegido.

Ela produz sínteses autorais e preserva conceitos, exemplos, procedimentos, números, prazos e requisitos importantes.

## Requisitos

1. Codex ou ChatGPT Work com suporte a skills.
2. Plugin de controle do navegador compatível com Chrome ou Edge.
3. Extensão do navegador instalada e conectada.
4. Sessão autenticada na Plataforma A da PUC.
5. Ferramenta de criação de documentos Word disponível no ambiente.
6. Permissão de leitura da disciplina e de gravação na pasta de saída.

A skill contém o fluxo de trabalho, mas não inclui credenciais, acesso à PUC, navegador ou Microsoft Word.

## Instalação

### Opção 1 — instalação global recomendada

Clone o repositório e copie a pasta completa para o diretório global de skills:

```powershell
git clone https://github.com/douglasg1997/resumir-curso-puc.git
New-Item -ItemType Directory -Force "$env:USERPROFILE\.agents\skills" | Out-Null
Copy-Item -Recurse -Force ".\resumir-curso-puc" "$env:USERPROFILE\.agents\skills\resumir-curso-puc"
```

Reinicie o Codex depois da instalação.

### Opção 2 — compatibilidade com instalações do Codex Desktop

Algumas instalações pessoais do Codex Desktop usam `CODEX_HOME/skills`:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills" | Out-Null
Copy-Item -Recurse -Force ".\resumir-curso-puc" "$env:USERPROFILE\.codex\skills\resumir-curso-puc"
```

Se a skill já aparecer na lista de skills do Codex, não é necessário instalar nas duas pastas.

### Opção 3 — somente para um projeto

Dentro do projeto em que a skill será usada:

```powershell
New-Item -ItemType Directory -Force ".agents\skills" | Out-Null
Copy-Item -Recurse -Force ".\resumir-curso-puc" ".agents\skills\resumir-curso-puc"
```

As skills são diretórios com um arquivo `SKILL.md`; o nome e a descrição do front matter determinam quando o Codex considera ativá-las. Consulte a [documentação oficial sobre skills](https://developers.openai.com/plugins/concepts/skills) e o guia [Build skills](https://developers.openai.com/plugins/build/skills).

## Configuração do navegador

1. Instale o plugin de navegador/Chrome no aplicativo desktop.
2. Instale e autorize a extensão correspondente no Chrome ou Edge.
3. Entre normalmente na Plataforma A da PUC.
4. Abra a disciplina desejada e deixe a página principal do curso visível.
5. No Codex, selecione o navegador externo conectado quando solicitado.

A documentação oficial explica que o plugin de Chrome usa a sessão já autenticada do navegador: [Using your computer and browser](https://developers.openai.com/training/walkthroughs/using-your-computer-and-browser).

Não compartilhe senha, código de autenticação ou token com a skill.

## Configuração no Codex

Depois de copiar a pasta e reiniciar o Codex:

1. confirme que `resumir-curso-puc` aparece entre as skills disponíveis;
2. mantenha disponíveis as skills/ferramentas de navegador e documentos;
3. abra um projeto ou pasta onde os arquivos Word possam ser salvos;
4. abra a disciplina da PUC no navegador conectado;
5. invoque a skill explicitamente com `$resumir-curso-puc`.

Exemplo:

```text
Use $resumir-curso-puc na disciplina aberta no Edge.
Gere o caderno de estudos, o resumo e o caderno de atividades formativas.
Salve os documentos na pasta deste projeto.
```

Para incluir uma avaliação:

```text
Use $resumir-curso-puc nesta disciplina e também consulte
"ATIVIDADES SOMATIVAS DA DISCIPLINA". Crie um checklist da AS2,
sem responder ou enviar a atividade.
```

## Modelo recomendado

Para esse fluxo, prefira um modelo com boa capacidade de navegação, contexto longo e revisão de documentos.

- **Recomendado:** **Astra, raciocínio médio**, quando disponível. É a melhor opção para disciplinas extensas, interação confiável com o navegador e entregáveis completos.
- **Alternativa mais rápida:** **GPT-6.1 Terra**, com raciocínio médio, para tarefas de computador bem delimitadas e cursos menores.
- Se esses nomes não aparecerem na sua conta, escolha o modelo mais forte disponível no Codex que ofereça controle de navegador/computador e use raciocínio **médio ou alto**.

A disponibilidade varia por produto e plano. Consulte o guia oficial de [seleção de modelos](https://developers.openai.com/api/docs/guides/model-selection).

## Fluxo esperado

```text
Disciplina aberta
    ↓
Mapa de semanas e cartões
    ↓
Leitura das unidades textuais
    ↓
Síntese por semana
    ↓
Atividades e orientações solicitadas
    ↓
Geração dos arquivos Word
    ↓
Renderização e inspeção visual
    ↓
Entrega dos documentos
```

## Estrutura do repositório

```text
resumir-curso-puc/
├── SKILL.md
├── README.md
├── LICENSE
├── agents/
│   └── openai.yaml
└── references/
    └── output-spec.md
```

## Limitações conhecidas

- A estrutura visual da Plataforma A pode mudar.
- Alguns conteúdos abrem em uma segunda aba ou aplicação externa.
- Questionários podem ocultar perguntas até o início de uma tentativa; a skill deve parar nesse ponto.
- Vídeos sem transcrição e imagens sem descrição acessível não são convertidos em texto.
- Abertura de unidades pode atualizar automaticamente o percentual de progresso.
- Prazos e pontuações devem ser conferidos novamente antes de qualquer entrega.

## Uso responsável

Esta skill foi criada para organização de estudos. O estudante continua responsável por conferir o material, elaborar suas próprias respostas e respeitar as regras acadêmicas da instituição.

## Licença

Distribuído sob a licença MIT. Consulte [LICENSE](LICENSE).

