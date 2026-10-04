# Mytaste

Site que monta um **perfil personalizado a partir dos jogos escolhidos** pela pessoa. Quanto mais jogos ela cadastra, com nota e status, mais o perfil de gosto toma forma.

> **Etapa atual: 1, interface estática.** Só HTML e CSS, com dados fictícios escritos direto no HTML. Os botões e formulários ainda não executam ações.

## Sumário

- [Tecnologias](#tecnologias)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Páginas](#páginas)
- [Cobertura dos requisitos da etapa](#cobertura-dos-requisitos-da-etapa)
- [Design](#design)
- [Como executar](#como-executar)
- [Próximas etapas](#próximas-etapas)

## Tecnologias

- **HTML5 semântico:** `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`, `figure`, `table`, `form`, `fieldset`, `dl` e outros.
- **CSS3:** Flexbox e Grid, variáveis CSS (`:root`) e layout responsivo, sem frameworks.
- **Fonte:** [Quicksand](https://fonts.google.com/specimen/Quicksand), via Google Fonts, com fallback para a fonte do sistema.
- **JavaScript e API:** ainda não utilizados. A pasta `assets/js/` já está reservada.

## Estrutura do projeto

```
Mytaste/
├── index.html              # Página inicial
├── pages/
│   ├── jogos.html          # Lista de jogos, pesquisa, filtro e ordenação
│   ├── cadastro.html       # Formulário de cadastro (e futura edição)
│   └── detalhes.html       # Detalhes de um jogo
├── assets/
│   ├── css/
│   │   └── style.css       # Folha de estilos única, organizada por seções
│   ├── img/
│   │   ├── Mytaste_Logo.png    # Logo original
│   │   ├── logo-completa.png   # Símbolo + nome (cabeçalho)
│   │   └── logo-mark.png       # Só o símbolo (ícone da aba, hero e capa provisória)
│   └── js/                 # Reservada para a próxima etapa
└── README.md
```

## Páginas

| Página | Arquivo | O que contém |
| --- | --- | --- |
| Início | `index.html` | Hero com chamada para ação, seção "Como funciona" (3 cards) e jogos em destaque |
| Meus jogos | `pages/jogos.html` | Formulário de pesquisa, filtro por gênero e ordenação; tabela com 4 jogos de exemplo; aside com resumo do perfil de gosto |
| Cadastrar jogo | `pages/cadastro.html` | Formulário com título, desenvolvedora, gênero, plataforma, ano, nota, status e opinião; aside com dicas |
| Detalhes | `pages/detalhes.html` | Ficha de um jogo (Celeste) com capa provisória, dados, botões Editar e Excluir e aside de jogos parecidos |

Todas as páginas compartilham o mesmo cabeçalho (logo + navegação) e o mesmo rodapé.

### Dados de exemplo

Os dados são fictícios e estáticos, escritos no HTML: Celeste, Hades, Stardew Valley e The Witcher 3. Eles serão substituídos por dados dinâmicos quando o JavaScript for adicionado.

## Cobertura dos requisitos da etapa

| Requisito | Onde está | Situação |
| --- | --- | --- |
| Identificação do sistema | Logo no cabeçalho de todas as páginas | Pronto |
| Navegação | `nav` no cabeçalho e no rodapé, com `aria-current` na página ativa | Pronto |
| Cadastro da entidade principal | `pages/cadastro.html` | Estrutura pronta, sem ação |
| Visualização dos itens | Tabela em `pages/jogos.html` | Pronto, com dados estáticos |
| Detalhes de um item | `pages/detalhes.html` | Pronto, com dados estáticos |
| Pesquisa | Campo `type="search"` em `pages/jogos.html` | Estrutura pronta, sem ação |
| Filtro | Seleção de gênero em `pages/jogos.html` | Estrutura pronta, sem ação |
| Ordenação | Seleção "Ordenar por" em `pages/jogos.html` | Estrutura pronta, sem ação |
| Edição | Botão **Editar** na tabela e nos detalhes | Botão sem ação |
| Exclusão | Botão **Excluir** na tabela e nos detalhes | Botão sem ação |

### Formulário de cadastro

Os tipos de campo seguem o dado que representam:

| Campo | Elemento |
| --- | --- |
| Título (obrigatório) | `input type="text"` |
| Desenvolvedora | `input type="text"` |
| Gênero (obrigatório) | `select` |
| Plataforma | `select` |
| Ano de lançamento | `input type="number"` (1970 a 2030) |
| Nota | `input type="number"` (0 a 10, passo 0,1) |
| Status | `fieldset` com `input type="radio"` |
| Opinião | `textarea` |

O formulário usa `method="get"` porque ainda não existe backend. Em um servidor estático, `post` causaria erro. Quando houver backend, troque por `post` com uma `action` real.

## Design

Identidade visual baseada na logo: minimalista, escura e com acento roxo.

- **Tema escuro como padrão.** Todas as cores estão em variáveis no `:root` do `style.css`, então o modo claro poderá ser criado sobrescrevendo essas variáveis.
- **Forma:** cantos arredondados desiguais (`--shape`), que lembram as duas metades do símbolo.
- **Acessibilidade:** textos alternativos nas imagens, títulos ocultos visualmente (`.sr-only`) para leitores de tela, foco visível no teclado e `aria-label` nas regiões de navegação.
- **Responsivo:** o layout muda para uma coluna em telas de até 760px.

| Variável | Cor | Uso |
| --- | --- | --- |
| `--bg` | `#07070c` | Fundo da página |
| `--surface` | `#11111a` | Cabeçalho, rodapé e cards |
| `--surface-2` | `#181824` | Botões e destaques |
| `--accent` | `#7c4dff` | Roxo da logo (ações e destaques) |
| `--accent-2` | `#a78bfa` | Links e foco |
| `--text` | `#ededf2` | Texto principal |
| `--gray` | `#7b8494` | Cinza da logo (rótulos) |

## Como executar

Não há instalação nem etapa de build.

1. Baixe ou clone o projeto.
2. Abra o `index.html` no navegador, ou use um servidor estático, como a extensão Live Server do VS Code.

A fonte Quicksand é carregada da internet. Sem conexão, o site usa a fonte padrão do sistema.

## Próximas etapas

Itens planejados, ainda não implementados:

- [ ] Renderizar a lista de jogos com JavaScript a partir de um conjunto de dados.
- [ ] Ativar pesquisa, filtro e ordenação.
- [ ] Ativar cadastro, edição e exclusão, reaproveitando `cadastro.html` para editar.
- [ ] Mostrar o jogo selecionado em `detalhes.html`.
- [ ] Criar a página de perfil, com os gêneros e jogos que definem o gosto da pessoa.
- [ ] Implementar o modo claro.
- [ ] Integrar uma API
