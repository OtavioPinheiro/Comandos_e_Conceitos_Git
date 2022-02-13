# Comandos e conceitos do Git
O objetivo desse projeto é simplesmente abordar os comandos mais usados do Git e explicar alguns conceitos.

# Sumário
- [O que é Git?](#o-que-é-git)
- [Comandos do Git](#comandos-do-git)

# O que é Git?
Git é o sistema de controle de versão distribuído moderno mais usado no mundo. Git é um projeto de código aberto e com uma manutenção ativa. Foi desenvolvido em 2005 por Linus Trovalds, o famoso criador do kernel do Sistema Operacional Linux. Um número impressionante de projetos de software depende do Git para o controle de versão, incluindo projetos de código aberto e projetos comerciais. O Git funciona e se integra muito bem com diversos SOs (Sistemas Operacionais) e com diversas IDEs (Ambiente de Desenvolvimento Integrado). As vantagens do Git sobre os demais controladores de versões são:
1. **DVCS**. O Git, por ser um sistema de controle de versão distribuído (DVCS - *Distributed Version Control Systems*), não armazena o histórico completo da versão do software em um único local.
2. **Desempenho**. As operações como, *commit*, *merge*, criar novas *branches*, etc, todas elas são otimizadas para ter o melhor desempenho. O Git utiliza *Deep Learning* para obter esse desempenho e também verifica o contéudo dos arquivos que estão sendo mapeados, não apenas os nomes dos arquivos.
3. **Segurança**. O Git utiliza criptografia hash chamada SHA1, isso protege o código e o histórico contra alterações acidentais e maliciosas e garante que o histórico tenha rastreabilidade total.
4. **Flexibilidade**. O Git é flexível em vários aspectos, como por exemplo: apresenta suporte a vários tipos de fluxos de trabalho de desenvolvimento não lineares, matém a eficiência em projetos pequenos e grandes e é compatível com muitos sistemas e protocolos existentes.

**FONTE**: [Atlassian](https://www.atlassian.com/br/git/tutorials/what-is-git)

# Comandos do Git
Os comandos do Git servem para ...

## Comandos mais usados do Git
### Comandos usados para a configuração
| Comando | Para que serve? |
|---------|-----------------|
| `git config --global user.name <nome>` | Configura o nome que você quer que esteja ligado às suas transações de *commit* |
| `git config --global user.email <e-mail>` | Configura e-mail que você quer que esteja ligado às suas transações de *commit* |

### Criando repositórios
| Comando | Para que serve? |
|---------|-----------------|
| `git init <nome-do-projeto>`[^git-init] | Cria um novo repositório local com o nome especificado |
| `git clone <url-do-projeto>` | Baixa um projeto e seu histórico de versão inteiro |

[^git-init]: O comando `git init` também pode ser usado quando o repositório já está criado. Neste caso basta abrir o terminal dentro da pasta (repositório) e executar o comando. Uma pasta (repositório) .git será criada.

## Lista completa de comandos do Git

| Comando | Funcionamento |
|---------|---------------|

## Gitflow
O Gitflow é um fluxo de trabalho legado do Git que no começo era uma estratégia inovadora e revolucionária para gerenciar ramificações do Git. O Gitflow perdeu popularidade para fluxos de trabalho baseados em troncos, que hoje são considerados práticas recomendadas para o desenvolvimento moderno e contínuo de *softwares* e práticas de DevOps. O Gitflow também pode ser difícil de usar com integração/implementação contínuas.

Em suma, Gitflow é uma ideia abstrata do fluxo de trabalho do Git, ou seja, ele dita que tipos de ramificações configurar e como fazer o merge.

Fonte: [Bitbucket](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)

## Conceito do Gitflow
Comparado ao desenvolvimento baseado em trocos, o Gitflow tem mais ramificações de vida longa e *commits* maiores. Sob este modelo, os desenvolvedores criam uma ramificação de recurso (desenvolvimento) e retardam o *merge* com a ramificação de tronco principal até que o recurso esteja pronto. Essas ramificações de recursos de longa duração exigem mais colaboração para fazer o *merge* e têm um risco maior de se desviarem do ramificação principal, possuindo, também, o risco de introduzir atualizações conflitantes.

O Gitflow pode ser usado para projetos que têm um ciclo de lançamento agendado e para a prática recomendada de DevOps de entrega contínua. Este fluxo de trabalho não adiciona novos conceitos ou comandos além do necessário para o fluxo de trabalho com ramificação. O que ele faz é atribuir funções bem específicas para diferentes ramificações e definir quando elas devem interagir. Além das ramificações de recurso (desenvolvimento), também se faz uso das ramificações individuais para preparar, manter e registrar lançamentos.

## Instalação
Para usar o Gitflow é necessário ter instalado o Git na máquina. O Gitflow funciona em MacOs, Linux e Windows e para instala-lo podemos executar no terminal (*shell*) o comando:

| Comando | OS |
|---------|----|
|`brew install git-flow-avh`| MacOs[^MacOs] |
| `apt-get install git-flow`| Linux |
| `wget -q -O - --no-check-certificate https://raw.github.com/petervanderdoes/gitflow-avh/develop/contrib/gitflow-installer.sh install stable \| bash` | Windows[^Windows] |


**FONTE:** [Cheatsheet do git-flow](https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html)

[^MacOs]: é necessário ter o Homebrew instalado.
[^Windows]: em algumas versões do Git for Windows, o git-flow já vem instalado por padrão.

## Comandos
| Comando | Funcionamento |
|---------|---------------|
| `git flow init` | Inicia o git flow dentro de um repositório existente. Assim que executar o comando, irá aparecer algumas perguntas que precisam ser respondidas para que o git flow saiba qual a nomeclatura que você usará para as suas *branches*, o recomendável é usar o padrão já definido pelo git flow. |
| `git flow feature start minhaFuncionalidade` | Cria uma nova *branch* de funcionalidade (*feat*), denominada, neste exemplo, de "minhaFuncionalidade", a partir da *branch develop* e faz o *checkout* para a nova *branch* |
| `git flow feature publish minhaFuncionalidade` | Faz um *push* para o servidor remoto, ou seja, publica a *branch*, especificada no comando, para um servidor remoto. |
| `git flow feature pull minhaFuncionalidade` | Faz um *pull* do servidor remoto, ou seja, baixa o código da *branch*, especificada no comando, de um servidor remoto. |
| `git flow release start RELEASE [BASE]` | Criar um *release*, uma *branch* que irá para produção, baseado na *branch develop*. |
| `git flow release finish RELEASE` | Finaliza uma versão. Por de baixo dos panos, executa a mescla (*merge*) da *branch* da versão na *branch master*, coloca uma etiqueta (*tag*) na versão, realiza o *merge* da *branch* da versão de volta na *branch develop* e por fim remove a *branch* da versão. |

**FONTE:** [CheatSheet do git flow](https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html)

## Funcionamento
### Ramificações de desenvolvimento(*develop*) e principal(*main*)
Para começar a explicar como funciona o fluxo de trabalho do Gitflow é necessário explicar as duas *branches* (ramificações) mais importantes, a *develop* e a *main* (ou *master*, ou *origin*, etc). Basicamente, a *branch main* é a ramificação principal e é aonde todo o código principal da aplicação se encontra. Já a *branch develop*, inicialmente, é uma cópia da *branch main* que é designada para receber atualizações da aplicação, ou seja, é a partir da *branch develop* é que os desenvolvedores irão criar novas *branches*, realizar o desenvolvimento da aplicação, e, quando concluído o desenvolvimento, realizar o *merge*, em palavras, unir as novas *branches* que foram criadas à *branch develop*. A estratégia de possuir essas duas ramificações, *main* e *develop*, é para evitar que conflitos prejudiquem o código na *branch main*, que pode estar se comunicando com uma esteira ou sendo homologada e distribuída para produção. Estando a *branch develop* sempre a frente da *branch main*, os conflitos sempre irão acontecer na *branch develop* e, assim que forem resolvidos, é que a *develop* será mergeada com a *branch main* e, por sua vez, irá estar disponível para a homologação e produção. O Gitflow utiliza essa estratégia de desenvolvimento.

![Fluxo de trabalho Gitflow](https://wac-cdn.atlassian.com/dam/jcr:a13c18d6-94f3-4fc4-84fb-2b8f1b2fd339/01%20How%20it%20works.svg?cdnVersion=199)

**FONTE:** [Bitbucket](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)

### Ramificações de recurso(*feature*)
Cada novo recurso(*feature*) deve ter a sua própria *branch*, que posteriormente será enviada (mergeada) para a *branch develop*, que no caso é a *branch* pai. As novas *features* não devem nunca interagir diretamente com a *branch main*, ou seja, não se deve realizar um *merge* das novas *features* diretamente para a *branch main*.

![Fluxo de criação de branches features](https://wac-cdn.atlassian.com/dam/jcr:34c86360-8dea-4be4-92f7-6597d4d5bfae/02%20Feature%20branches.svg?cdnVersion=199)

Comparando o Git tradicional com o Git flow, em termos de comandos a serem usados, temos:

| Git | Git flow |
|-----|----------|
| `git checkout develop` <br> `git checkout -b feature_branch` | `git flow feature start feature_branch` |

Logo podemos concluir que, em termos de comandos utilizados, o Git Flow possui a vantagem de resolver a criação de uma nova *branch* de funcionalidade em apenas um comando, porém com o Git tradicional, pelo fato de realizar a mesma tarefa em mais passos, o torna mais versátil.

**FONTE:** [Bitbucket](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)

### 

# Bibliografia
1. [Git](https://git-scm.com/docs/git#_git_commands)
2. [Training Github](https://training.github.com/downloads/pt_BR/github-git-cheat-sheet/)