Plano de Gerência de Configuração
=================================

<small>Sumário</small>
======================

<!-- MDTOC maxdepth:2 firsth1:0 numbering:0 flatten:0 bullets:1 updateOnSave:1 -->

- [1. Introdução](#1-introdução)   
   - [1.1. Definições, Acrônimos e Abreviações](#11-definições-acrônimos-e-abreviações)   
   - [1.2. Referências](#12-referências)   
- [2. Organização, Responsabilidades, e Interfaces](#2-organização-responsabilidades-e-interfaces)   
   - [2.1. Responsabilidades do GCO](#21-responsabilidades-do-gco)   
   - [2.2. Responsabilidades da equipe de desenvolvimento em relação à GCO](#22-responsabilidades-da-equipe-de-desenvolvimento-em-relação-à-gco)   
- [3. A Gerência de Configuração](#3-a-gerência-de-configuração)   
   - [3.1. Artefatos da Gerência de Configuração](#31-artefatos-da-gerência-de-configuração)   
   - [3.2. Ferramentas e Tecnologias](#32-ferramentas-e-tecnologias)   
   - [3.3. Branches](#33-branches)   
   - [3.4. Estrutura do Repositório](#34-estrutura-do-repositório)   
   - [3.5. Identificação da Configuração](#35-identificação-da-configuração)   
   - [3.6. Commits](#36-commits)   
   - [3.7. Controle de mudanças](#37-controle-de-mudanças)   
   - [3.8. Baselines](#38-baselines)   

<!-- /MDTOC -->

## 1. Introdução
Este **Plano de Gerência de Configuração** apresenta todas as tarefas do
Gerenciamento de Configuração e Mudanças neste projeto. Nesse documento detalha-se toda a infraestrutura
utilizada neste projeto e como contribuir no mesmo.

### 1.1. Definições, Acrônimos e Abreviações

| Termo | Significado |
|------:|-------------|
| [**Baseline/Tag**](https://en.wikipedia.org/wiki/Baseline_%28configuration_management%29) | **Linha de referência** / "etiqueta" marcando ponto no desenvolvimento de software em que seus artefatos estão supostamente estáveis. |
| [**CamelCase**](https://pt.wikipedia.org/wiki/CamelCase) | forma de representação **escrita** de palavras compostas ou frases iniciadas por maiúsculas e unidas sem espaços. |
| [**Commit**](https://en.wikipedia.org/wiki/Commit_%28version_control%29) | **Revisão**, de (todo ou parte de) um código-fonte num VCS. |
| [**GCO / GCS**](https://pt.wikipedia.org/wiki/Ger%C3%AAncia_de_configura%C3%A7%C3%A3o_de_software) | **Gerência de Configuração de Software**, área da Engenharia de Software que fornece apoio para o desenvolvimento de software. |
| [**IDE**](https://pt.wikipedia.org/wiki/Ambiente_de_desenvolvimento_integrado) | **Ambiente de Desenvolvimento Integrado** (do inglês *Integrated Development Environment*), software que reúne ferramentas para auxiliar e agilizar o desenvolvimento de software. |
| [**Issue**](https://en.wikipedia.org/wiki/Project_management_software) | **Incidente** / *card* / atividade ou pacote de trabalho dentro de um Sistema de Gerenciamento de Projetos. |
| [**Markdown**](https://en.wikipedia.org/wiki/Markdown) | Linguagem de Marcação Leve ([LML](https://en.wikipedia.org/wiki/Lightweight_markup_language)) para **documentos**. |
| [**Milestone**](https://en.wikipedia.org/wiki/Milestone_%28project_management%29) | **Marco do projeto**, reúne *Issues* / *PR*s para futura entrega de um software (ou parte dele) para um cliente. |
| [**Push**](https://en.wikipedia.org/wiki/Version_control#Common_vocabulary) | Comando em alguns VCS para **enviar mudanças** (*commits*) para um repositório remoto. |
| [**VCS**](https://pt.wikipedia.org/wiki/Sistema_de_controle_de_vers%C3%B5es) | **Sistema de Controle de Versões** (do inglês *Version Control System*), software usado para fazer Gerência de Configuração. |

### 1.2. Referências

<h6 id="cite-ref-1"/>
###### 1. SANTOS, Gustavo Moraes dos et al. Template de Plano de Gerenciamento de Configuração. Disponível em: http://github.com/gabrielaimeeg/DroidMetronome/wiki/TEMPLATE-Plano-de-Gerenciamento-de-Configuração. Acesso em: 28 mar. 2015.

<h6 id="cite-ref-2"/>
###### 2. WERNER, Tom Preston. Semantic versioning 2.0.0. Disponível em: http://semver.org. Acesso em: 28 mar. 2015.

## 2. Organização, Responsabilidades, e Interfaces
A gerência de configuração faz um papel fundamental para que o
desenvolvimento não seja prejudicado por informações inconsistentes.
Dessa forma, o gerente de configuração é responsável por controlar todas
as mudanças e disponibilizar a todos os envolvidos as versões e os itens
de configuração corretos e íntegros (artefatos de software) para que
inconsistências não atrapalhem a evolução do desenvolvimento (auditoria
das configurações) e permita uma melhor comunicação entre os membros da
equipe.

#### Gerente de Configuração (GCO)

A lista do(s) Gerente(s) de Configuração (GCO) encontra-se nesta página:

[**@VanBoraTeam/gerencia-de-configuracao**](https://github.com/orgs/VanBoraTeam/teams/gerencia-de-configuracao)

### 2.1. Responsabilidades do GCO

* Manter padronizada a estrutura de diretórios do repositório (organização ― seções [3.4](#34-estrutura-do-repositório) e [3.5](#35-identificação-da-configuração));
* Supervisionar as *Issues* no nível de rastreabilidade (pacotes de trabalho ― seção [3.7](#37-controle-de-mudanças));
* Supervisionar a possível presença de "commits quebrados" – commits com não conformidades à GCO / código-fonte com erros de compilação / nos testes (seção [3.7](#37-controle-de-mudanças));
* Entregar pacotes relativamente estáveis de código-fonte para o *Gerente de Projeto* regularmente (seção [3.8](#38-baselines)).

### 2.2. Responsabilidades da equipe de desenvolvimento em relação à GCO

* Usar as ferramentas sugeridas (seção [3.2](#32-ferramentas-e-tecnologias));
* Seguir os padrões de criação e uso de branches (seção [3.3](#33-branches)), da estrutura de diretórios do repositório (seção [3.4](#34-estrutura-do-repositório)), da identificação da configuração / nome dos arquivos (seção [3.5](#35-identificação-da-configuração)) e de mensagem de *commit* e *Pull Request* (seção [3.6](#36-commits));
* Usar as *Issues* / *cards* para gerência de atividades, devendo usá-las para comunicação (tal como no processo definido no **Plano de Projeto** do VanBora);
* Fazer rastreabilidade entre os *commits* / *baselines* e as *Issues* / *cards* (anexando o(s) a ele(s) (seção [3.7](#37-controle-de-mudanças)).

## 3. A Gerência de Configuração

### 3.1. Artefatos da Gerência de Configuração

A Gerência de Configuração trabalhará em alto nível sob os seguintes conjuntos de artefatos:

* [Documentação](../)
* [Quadro de atividades do projeto](https://trello.com/b/EhTpl06z)
* [Baselines](../../../../releases)

### 3.2. Ferramentas e Tecnologias

#### Ferramentas

| Tipo | Ferramenta | Versão* |
|-----:|:-----------|:-------:|
| VCS | [Git](http://git-scm.com) | 2.4.2 ou superior |
| Cliente em GUI para VCS | [SmartGit](http://www.syntevo.com/smartgit) | 7.1.4 ou superior |
| Sistema de Repositório | [GitHub](https://github.com/ES-INF-UFG-2016-2/Sempre-UFG) | – |
| Linguagem de Programação | [Java](https://java.com/pt_BR) | 8 Update 91 ou superior |
| IDE | [Android Studio](https://developer.android.com/sdk/index.html) | 2.0 ou superior |
| Editor de texto *Markdown* | [Atom](http://atom.io) | 1.8.0 ou superior |
| Editor de diagramas | [Draw.io](http://draw.io) | – |
| Editor de Imagens |[GIMP](http://www.gimp.org) | 2.8.0 ou superior |
| Editor de Desenho Vetorial |[Inkscape](https://inkscape.org) | 0.48.0 ou superior |
| Gerência de projeto | [Trello](https://trello.com) | – |
| Controle de mudanças | [GitHub Issues](../../../../issues) | – |

\* "**–**" – *sistema Web, sempre será última versão.*

#### Tecnologias

| Tipo | Tecnologia | Versão |
|-----:|:-----------|:------:|
| Plataforma de desenvolvimento | [Android SDK](https://developer.android.com/studio/releases/sdk-tools.html) | 25 ou superior |
| Banco de Dados | [Firebase](https://firebase.google.com) | – |

### 3.3. Branches

O uso de branches no repositório é livre para os integrantes fazerem a partir da branch `master`.

### 3.4. Estrutura do Repositório

+ **`anexos`**
	* ***`arq`***
		- *Arquivos de anexo relacionados à Arquitetura do software (diagramas, processos, etc.)*
	* ***`gco`***
		- *Arquivos de anexo para o Plano de Gerência de Configuração*
	* ***`req`***
		- *Arquivos de anexo para apoio da Engenharia de Requisitos (protótipos, etc.)*
	* ***`v&v`***
		- *Arquivos de apoio para o processo de Verificação e Validação*
- **`extras`**
	+ *Arquivos de terceiros ou que não tem relação direta com apenas uma área de conhecimento dentro do projeto (identidade visual, material de apoio, etc.)*

### 3.5. Identificação da Configuração

#### Documentos em Markdown

Todos os documentos de texto em *Markdown* na pasta `docs/wiki/` terão o seguinte método de identificação:

**`<Título-do-documento>.md`**

| Identificador | Descrição |
|---------------|-----------|
| `<Título-do-documento>` | Um nome único e completo para o documento, com primeira letra *maiúscula*, com acentos e espaçamento com *hífen* ("-"). O mesmo nome deve ser o nome do título do documento dentro deste, mas com espaçamento com *espaços* (" "). Ex.: *"Plano-de-Gerência-de-Configuração", "Documento-de-Especificação-de-Interface"*, etc. |

**Obs.:** Todo novo documento de texto incluído no repositório deve ser referenciado no [**`README.md`**](../README.md) na seção (área da Engenharia de Software) a qual ele pertence.

#### Outros artefatos

Todos os outros artefatos gerados no projeto – como diagramas e protótipos de interface – terão o seguinte método de identificação:

**`<tipo-do-artefato>_<identificador>.<ext>`**

| Identificador | Descrição |
|---------------|-----------|
| `<tipo-do-artefato>` | Tipo do artefato. Um nome completo com letras *minúsculas*, sem acentos e espaçamento com *hífen* ("-"). Ex.: *"diagrama-de-classes", "politica-de-branches"*, etc. |
| `_` | Separador. Um *underline* ("\_"). |
| `<identificador>` | Identificador único, mas opcional, dependendo do tipo do artefato (número, data ou frase), também com letras *minúsculas*, sem acentos e espaçamento com *hífen* ("-"). Ex.: *"121", "18-02-2016", "avaliacao-de-provas"*, etc. |
| `<ext>` | A extensão do arquivo. Ex.: *"png", "ep", "asta", "bpm"*, etc. |

Exemplos:
 * `diagrama-de-sequencia_rf-atualegres.png`
 * `politica-de-gco.png`

**Obs.:** O nome desses artefatos deve ser obrigatoriamente em *minúsculas*, sem acentos e espaçamento com *hífen* ("-") porque existem servidores Web e frameworks de aplicação que rodam em *Linux* e podem causar problemas de não encontrarem arquivos e/ou emitir erros ao executar o software com arquivos com esse tipo de nome.

### 3.6. Commits

#### Padrão de mensagem de commit

* Mensagem **sucinta** e **objetiva** sobre o conteúdo do commit
* Tamanho: de 15 a 50 caracteres
* **Verbo** ***na 3º pessoa do presente simples*** **+ complemento** (o que mudou no projeto)
	* Exemplos:
		* `Adiciona diagrama de classes`
		* `Refatora função X`
		* `Otimiza funcionalidade "Enviar email"`
		* `Conserta bug #13`

#### Frequência de commit

* Pelo menos **1x no dia** que um integrante da equipe trabalhar numa tarefa delegada a ele, ou assim que uma parte signficativa da tarefa foi realizada e será continuada posteriormente (*commit* como um "[***checkpoint***](https://en.wikipedia.org/wiki/Application_checkpointing)", ponto "estável" que pode ser retornado – [*respawning*](https://en.wikipedia.org/wiki/Spawning_(video_gaming) –  em caso de falhas posteriores / erro humano / perda de dados).
* Os commits feitos localmente devem ser enviados ("*push*") ao repositório principal pelo menos assim que o integrante terminar de trabalhar no projeto no dia. **Não devem ser deixados commits apenas localmente** ***ou*** **artefatos fora do controle de versão** na máquina do integrante do grupo, mesmo que eles tenham sido feitos na frequência estipulada acima.

### 3.7. Controle de mudanças

O **processo de Controle de Mudanças** do *Sempre UFG* gira em torno dos ***Pull Requests***, recurso do [GitHub](https://github.com) para solicitar mudanças no repositório de projeto. Eles podem ter origem em⁽[**²**](#cite-ref-2)⁾:
* *Cards* do [quadro de atividades do projeto no **Trello**](https://trello.com/b/CH0jPQVT), questões de natureza *administrativa*;
* *Issues* no [**GitHub** do projeto](https://github.com/ES-INF-UFG-2016-2/Sempre-UFG/issues), questões de natureza *técnica*.

### 3.8. Baselines

Para que se dê a criação de uma baseline, é necessário que os GCOs tenham feito todas as auditorias de configuração nas atividades feitas pela equipe de desenvolvimento do *Sempre UFG* na iteração do projeto (definida pelo *Gerente de Projeto* e estarem na branch `master`.

#### Tag

As baselines serão "etiquetadas" com o seguinte formato, começando a partir de **`v0.1.0`**⁽[**⁴**](#cite-ref-4)⁾:

`<major>.<minor>.<patch>`

E serão construídas com as seguintes orientações:

* Quebra de compatibilidade com versões anteriores, avança o `<major>`.
* Adição de novas funcionalidades sem quebrar compatibilidade com versões anteriores, avança o `<minor>`.
* Correção de bugs e outras alterações, avança `<patch>`.

#### Notas de release

Ao criar uma nova baseline no projeto no [GitHub](https://github.com/ES-INF-UFG-2016-2/Sempre-UFG/releases/new), há opção de colocar notas de release e anexar um arquivo executável do projeto em questão. As notas de release deverão ser feitas em texto na linguagem *Markdown* no seguinte *template*:

```markdown
### Histórico de mudanças
* Novo: (...)
* Correção: (...)
* Melhoria: (...)
* Menor: (...)
```

O repositório será versionado com tag **`v1.0.0`** quando o software for lançado.
