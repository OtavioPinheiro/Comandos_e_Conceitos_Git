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


## Gitflow
O Gitflow é um fluxo de trabalho legado do Git que no começo era uma estratégia inovadora e revolucionária para gerenciar ramificações do Git. O Gitflow perdeu popularidade para fluxos de trabalho baseados em troncos, que hoje são considerados práticas recomendadas para o desenvolvimento moderno e contínuo de *softwares* e práticas de DevOps. O Gitflow também pode ser difícil de usar com integração/implementação contínuas.

Fonte: [Bitbucket](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)

### Conceito do Gitflow
Comparado ao desenvolvimento baseado em trocos, o Gitflow tem mais ramificações de vida longa e *commits* maiores. Sob este modelo, os desenvolvedores criam uma ramificação de recurso (desenvolvimento) e retardam o *merge* com a ramificação de tronco principal até que o recurso esteja pronto. Essas ramificações de recursos de longa duração exigem mais colaboração para fazer o *merge* e têm um risco maior de se desviarem do ramificação principal, possuindo, também, o risco de introduzir atualizações conflitantes.

### Funcionamento


# Bibliografia
1. [Git](https://git-scm.com/docs/git#_git_commands)
2. [Training Github](https://training.github.com/downloads/pt_BR/github-git-cheat-sheet/)