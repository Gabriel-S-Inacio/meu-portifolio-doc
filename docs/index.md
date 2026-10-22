# Learn to Learn English — Arquitetura Técnica do Front-end

- **Projeto:** Learn to Learn English
- **Documento:** Arquitetura Técnica do Front-end
- **Classificação:** 02_Arquitetura_SAD
- **Autor:** Gabriel Santos Inácio
- **Versão:** 1.1
- **Documento original:** Atividade 3 — Documentação Viva com Confluence
- **Revisão:** Atividade 4 — Refatoração da Documentação Técnica
- **Última atualização:** 03 de outubro de 2026

---

## 1. Objetivo e escopo

Este documento descreve a arquitetura atual do front-end do Learn to Learn English, incluindo sua organização interna, tecnologias, navegação, componentes, estilos, responsividade e estratégia de acesso a dados.

### Escopo

O documento contempla:

- Tecnologias utilizadas;
- Organização de diretórios;
- Páginas e rotas;
- Componentes reutilizáveis;
- Fundamentos do Design System;
- Responsividade;
- Serviços e dados simulados;
- Fluxo técnico do front-end;
- Estado atual e evolução prevista.

Não fazem parte deste documento:

- Regras detalhadas de agendamento;
- Banco de dados;
- Autenticação;
- Contratos de API;
- Infraestrutura de produção.

Esses elementos devem ser tratados em documentos específicos conforme a evolução do projeto.

---

## 2. Tecnologias utilizadas

| Tecnologia | Responsabilidade |
|---|---|
| React 19 | Construção das páginas e componentes |
| Vite | Ambiente de desenvolvimento e geração do build |
| React Router | Controle da navegação entre rotas |
| JavaScript | Implementação da lógica do front-end |
| CSS | Estilização e responsividade |
| Git | Controle de versão |
| GitHub | Hospedagem e colaboração no código-fonte |

---

## 3. Estrutura do projeto

O código principal da aplicação está organizado no diretório `src`.

```text
src/
├── assets/
│   ├── images/
│   └── icons/
├── components/
│   ├── layout/
│   ├── ui/
│   └── shared/
├── pages/
├── routes/
├── data/
├── services/
├── styles/
├── App.jsx
└── main.jsx
```

### Diretórios e responsabilidades

| Diretório | Responsabilidade |
|---|---|
| `assets` | Imagens e ícones |
| `components` | Componentes reutilizáveis |
| `pages` | Páginas associadas às rotas |
| `routes` | Configuração da navegação |
| `data` | Dados locais e simulados |
| `services` | Abstração do acesso a dados |
| `styles` | Tokens, estilos globais e animações |

Essa separação reduz o acoplamento entre interface, navegação e acesso a dados.

---

## 4. Páginas e rotas

| Página | Rota | Responsabilidade |
|---|---|---|
| Home | `/` | Apresentar o projeto e direcionar o visitante |
| Método | `/metodo` | Explicar o método de aprendizagem |
| Como Funciona | `/como-funciona` | Apresentar a jornada do aluno |
| Conteúdos | `/conteudos` | Exibir os conteúdos disponíveis |
| Sobre | `/sobre` | Apresentar informações institucionais |
| Agendamento | `/agendar` | Exibir os horários disponíveis |
| Minhas Aulas | `/minhas-aulas` | Representar a área de aulas do aluno |
| Administração | `/admin/agenda` | Representar a área administrativa da agenda |
| Página não encontrada | `*` | Tratar rotas inexistentes |

---

## 5. Sistema de rotas

A navegação é controlada pelo React Router.

A configuração principal está localizada em:

`src/routes/AppRoutes.jsx`

O fluxo de navegação é:

```text
URL solicitada
      ↓
React Router
      ↓
Identificação da rota
      ↓
Página correspondente
```

### Exemplo

```text
/agendar
    ↓
React Router
    ↓
Schedule
    ↓
Tela de agendamento
```

Rotas não reconhecidas são direcionadas para a página de erro 404.

---

## 6. Componentes

A aplicação utiliza componentes reutilizáveis para reduzir duplicação e manter consistência visual.

### 6.1 Componentes de layout

| Componente | Responsabilidade |
|---|---|
| `PublicLayout` | Estrutura comum das páginas públicas |
| `Header` | Cabeçalho principal |
| `MobileNav` | Navegação em dispositivos móveis |
| `Footer` | Rodapé da aplicação |

O `PublicLayout` organiza a estrutura compartilhada:

```text
Header
   ↓
Conteúdo da página
   ↓
Footer
```

### 6.2 Componentes de interface

| Componente | Responsabilidade |
|---|---|
| `Button` | Padronização de ações |
| `Eyebrow` | Texto auxiliar de destaque |
| `EditorialHeading` | Padronização de títulos |
| `StatePanel` | Apresentação de estados da interface |

### 6.3 Componentes compartilhados

| Componente | Responsabilidade |
|---|---|
| `PageHero` | Cabeçalho visual das páginas |
| `MethodCard` | Apresentação de etapas ou métodos |
| `ContentCard` | Apresentação de conteúdos |
| `QuotePanel` | Exibição de citações ou mensagens |
| `CtaBanner` | Chamada para ação |

A reutilização centraliza alterações: quando um componente é atualizado, todas as páginas que o utilizam recebem a mesma mudança.

---

## 7. Fundamentos do Design System

A aplicação centraliza definições visuais para manter consistência entre páginas e componentes.

### Arquivos principais

- `src/styles/tokens.css`
- `src/styles/globals.css`
- `src/styles/animations.css`

### Paleta principal

| Uso | Cor |
|---|---|
| Fundo | `#F8F4E8` |
| Texto | `#2B2B2B` |
| Verde principal | `#1F4D3A` |
| Verde secundário | `#2E5E4E` |
| Destaque | `#E6D400` |
| Bordas | `#D7DDCF` |

### Tipografia

| Fonte | Aplicação |
|---|---|
| DM Serif Display | Títulos e elementos editoriais |
| Inter | Textos, menus, formulários e botões |

O uso de tokens reduz valores visuais duplicados e facilita alterações globais no tema.

---

## 8. Responsividade

A interface foi projetada para se adaptar a diferentes dimensões de tela.

Os principais pontos de adaptação são:

- `640px`
- `768px`
- `1024px`
- `1280px`
- `1536px`

Em telas maiores, menus e cards utilizam o espaço horizontal disponível.

Em telas menores:

- Navegação desktop → navegação mobile;
- Cards lado a lado → cards empilhados.

Essa estratégia permite o uso da aplicação em computadores, tablets e smartphones.

---

## 9. Dados e serviços

Algumas funcionalidades ainda utilizam dados simulados enquanto a integração com o backend não está disponível.

A agenda utiliza principalmente:

- `src/data/schedule.mock.js`
- `src/services/scheduleService.js`

### Fluxo atual

```text
Página de Agenda
       ↓
scheduleService
       ↓
Dados simulados
```

A página não acessa diretamente os dados. O `scheduleService` funciona como camada de abstração.

### Fluxo previsto

```text
Página de Agenda
       ↓
scheduleService
       ↓
API
       ↓
Backend
       ↓
Banco de Dados
```

Essa separação permite substituir os dados simulados pela API com menor impacto sobre os componentes da interface.

---

## 10. Visão arquitetural do front-end

O fluxo principal da aplicação pode ser representado por:

```text
Usuário
   ↓
Aplicação React
   ↓
React Router
   ↓
Página
   ↓
Componentes
   ↓
Serviços
   ↓
Dados simulados / API
```

### Exemplo do fluxo de agendamento

```text
Usuário acessa /agendar
        ↓
React Router resolve a rota
        ↓
Schedule é carregado
        ↓
Schedule utiliza scheduleService
        ↓
scheduleService obtém os dados
        ↓
A interface apresenta o resultado
```

---

## 11. Diagrama de arquitetura

### Notação utilizada

O diagrama desta documentação utiliza o **C4 Model — Component Diagram**.

A notação representa os elementos da seguinte forma:

| Elemento | Significado |
|---|---|
| Pessoa | Ator externo que utiliza o sistema |
| Container | Aplicação executável ou unidade de implantação |
| Component | Unidade funcional interna da aplicação |
| Software System externo | Sistema externo consumido pela aplicação |
| Seta | Dependência ou fluxo de comunicação |

### Elementos do diagrama

#### Pessoa

**Usuário**

Interage com a aplicação por meio do navegador.

#### Container

**Learn to Learn English — React SPA**

Representa a aplicação front-end executada no navegador.

#### Componentes internos

- `AppRoutes`
- Pages
- Shared Components
- Services
- Local / Mock Data

#### Sistema externo futuro

**Backend API**

### Fluxo representado

```text
Usuário
   ↓
React SPA
   ↓
AppRoutes
   ↓
Pages
   ↓
Shared Components

Pages
   ↓
Services
   ↓
Local / Mock Data

Services
   ↓
Backend API
   (integração futura)
```

O diagrama deve ser inserido nesta seção utilizando [Draw.io](https://app.diagrams.net/), Lucidchart, Excalidraw ou ferramenta equivalente, preservando explicitamente a notação C4 descrita acima.

---

## 12. Estado atual

### Funcionalidades implementadas

| Área | Estado |
|---|---|
| Home | Implementado |
| Método | Implementado |
| Como Funciona | Implementado |
| Conteúdos | Implementado |
| Sobre | Implementado |
| Estrutura da Agenda | Implementado |
| Minhas Aulas sem autenticação | Implementado |
| Área administrativa sem autenticação | Implementado |
| Header e Footer | Implementado |
| Navegação mobile | Implementado |
| Rotas | Implementado |
| Componentes reutilizáveis | Implementado |
| Estilos globais | Implementado |
| Responsividade | Implementado |
| Animações | Implementado |

### Funcionalidades pendentes

| Área | Estado |
|---|---|
| Backend | Pendente |
| Banco de dados | Pendente |
| API | Pendente |
| Autenticação real | Pendente |
| Cadastro de usuários | Pendente |
| Reserva real de horário | Pendente |
| Painel completo do aluno | Pendente |
| Painel administrativo completo | Pendente |

---

## 13. Evolução prevista

A evolução técnica prevista segue esta integração:

```text
Front-end
    ↓
API
    ↓
Backend
    ↓
Banco de Dados
```

Essa evolução permitirá incorporar:

- Autenticação;
- Cadastro de usuários;
- Agendamento persistente;
- Área completa do aluno;
- Funções administrativas;
- Persistência de dados.

A estrutura atual de serviços reduz o impacto da futura substituição dos dados simulados por integrações reais.

---

## 14. Controle de versão

O projeto utiliza Git e GitHub para controle de alterações e colaboração.

### Repositório

[Gabriel-S-Inacio/Projeto-Learn-to-Learn](https://github.com/Gabriel-S-Inacio/Projeto-Learn-to-Learn)

### Fluxo de branches utilizado como referência

```text
main
│
├── feature/home
├── feature/como-funciona
├── feature/agenda
└── feature/area-aluno
```

Cada alteração pode ser desenvolvida em uma branch específica e posteriormente integrada à `main` por meio de Pull Request.

---

## 15. Rastreabilidade documental

### Categoria

```text
PROJETO_SISTEMA/
└── 02_Arquitetura_SAD/
    └── Arquitetura Técnica do Front-end
```

A classificação em `02_Arquitetura_SAD` ocorre porque este documento descreve a estrutura da solução, componentes, responsabilidades, navegação e dependências técnicas do front-end.

### Documentos relacionados

- Documento de requisitos do sistema;
- Documentação das regras de agendamento;
- Documentação futura da API;
- Documentação futura do backend;
- Documentação futura do banco de dados.

---

## 16. Referências

- Protótipo do Learn to Learn English;
- Repositório GitHub do projeto;
- Código-fonte atual;
- Documento de requisitos do sistema;
- Documentação oficial do [React](https://react.dev/);
- Documentação oficial do [Vite](https://vite.dev/);
- Documentação oficial do [React Router](https://reactrouter.com/);
- Documentação do [C4 Model](https://c4model.com/).

---

## 17. Labels

Aplicar os seguintes rótulos à página no Confluence:

- `arquitetura`
- `frontend`
- `react`
- `vite`
- `react-router`
- `componentes`
- `design-system`
- `responsividade`
- `servicos`
- `learn-to-learn`

---

## 18. Histórico do documento

| Versão | Data | Alteração |
|---|---|---|
| 1.0 | 18/09/2026 | Criação inicial da documentação técnica |
| 1.1 | 03/10/2026 | Refatoração pelos 3 Cs, classificação documental, rastreabilidade, labels e definição do diagrama arquitetural |
