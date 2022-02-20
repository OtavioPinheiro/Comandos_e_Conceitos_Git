# Comandos e conceitos do Git
O objetivo desse projeto é simplesmente abordar os comandos mais usados do Git e explicar alguns conceitos.

# Sumário
- [O que é Git?](#o-que-é-git)
- [Comandos do Git](#comandos-do-git)
  - [Git flow](#gitflow)
    - [Conceito](#conceito-do-gitflow)
    - [Funcionamento](#funcionamento-do-git-flow)
    - [Branch develop e main](#ramificações-de-desenvolvimentodevelop-e-principalmain)
    - [Branch feature](#ramificações-de-recursofeature)
    - [Branch release](#ramificações-de-lançamentorelease)
    - [Branch hotfix](#ramificação-de-correçãohotfix)
- [Assinando commits](#assinando-commits)
- [Bibliografia](#bibliografia)

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

### Conceito do Gitflow
Comparado ao desenvolvimento baseado em trocos, o Gitflow tem mais ramificações de vida longa e *commits* maiores. Sob este modelo, os desenvolvedores criam uma ramificação de recurso (desenvolvimento) e retardam o *merge* com a ramificação de tronco principal até que o recurso esteja pronto. Essas ramificações de recursos de longa duração exigem mais colaboração para fazer o *merge* e têm um risco maior de se desviarem do ramificação principal, possuindo, também, o risco de introduzir atualizações conflitantes.

O Gitflow pode ser usado para projetos que têm um ciclo de lançamento agendado e para a prática recomendada de DevOps de entrega contínua. Este fluxo de trabalho não adiciona novos conceitos ou comandos além do necessário para o fluxo de trabalho com ramificação. O que ele faz é atribuir funções bem específicas para diferentes ramificações e definir quando elas devem interagir. Além das ramificações de recurso (desenvolvimento), também se faz uso das ramificações individuais para preparar, manter e registrar lançamentos.

### Instalação
Para usar o Gitflow é necessário ter instalado o Git na máquina. O Gitflow funciona em MacOs, Linux e Windows e para instala-lo podemos executar no terminal (*shell*) o comando:

| Comando | OS |
|---------|----|
|`brew install git-flow-avh`| MacOs[^MacOs] |
| `apt-get install git-flow`| Linux |
| `wget -q -O - --no-check-certificate https://raw.github.com/petervanderdoes/gitflow-avh/develop/contrib/gitflow-installer.sh install stable \| bash` | Windows[^Windows] |


**FONTE:** [Cheatsheet do git-flow](https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html)

[^MacOs]: é necessário ter o Homebrew instalado.
[^Windows]: em algumas versões do Git for Windows, o git-flow já vem instalado por padrão.

### Comandos
| Comando | Funcionamento |
|---------|---------------|
| `git flow init` | Inicia o git flow dentro de um repositório existente. Assim que executar o comando, irá aparecer algumas perguntas que precisam ser respondidas para que o git flow saiba qual a nomeclatura que você usará para as suas *branches*, o recomendável é usar o padrão já definido pelo git flow. |
| `git flow feature start minhaFuncionalidade` | Cria uma nova *branch* de funcionalidade (*feat*), denominada, neste exemplo, de "minhaFuncionalidade", a partir da *branch develop* e faz o *checkout* para a nova *branch* |
| `git flow feature publish minhaFuncionalidade` | Faz um *push* para o servidor remoto, ou seja, publica a *branch*, especificada no comando, para um servidor remoto. |
| `git flow feature pull minhaFuncionalidade` | Faz um *pull* do servidor remoto, ou seja, baixa o código da *branch*, especificada no comando, de um servidor remoto. |
| `git flow release start RELEASE [BASE]` | Criar um *release*, uma *branch* que irá para produção, baseado na *branch develop*. |
| `git flow release finish RELEASE` | Finaliza uma versão. Por de baixo dos panos, executa a mescla (*merge*) da *branch* da versão na *branch master*, coloca uma etiqueta (*tag*) na versão, realiza o *merge* da *branch* da versão de volta na *branch develop* e por fim remove a *branch* da versão. |

**FONTE:** [CheatSheet do git flow](https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html)

### Funcionamento do Git flow
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

### Finalizando uma ramificação de recurso(*feature*)
Quando concluído o desenvolvimento da ramificação (*branch*) de recurso (*feature*), o próximo passo é realizar o *merge* (mesclar) da *branch feature* com a *branch develop*. Para realizar esse processo utilizando o Git flow, executamos o seguinte comando `git flow feature finish feature_branch`. Em comparação com o Git tradicional temos:

| Git | Git flow |
|-----|----------|
| `git checkout develop` <br> `git merge feature_branch` | `git flow feature finish feature_branch` |

**FONTE:** [Bitbucket](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)

### Ramificações de lançamento(*release*)
Quando a *branch develop* possuir os recursos necessários estipulados para um lançamento (*release*), devemos criar uma nova *branch* de *release* a partir da *develop*. Como via de regra, após a criação da *branch release*, nenhum recurso (*feature*) pode ser adicionado, apenas atualizações de segurança, geração de documentos e outras tarefas relacionadas ao lançamento devem ir nesta ramificação. Quando estiver pronta para ser lançada, a ramificação *release* passa por *merge* para a ramificação *main* e é marcada com o número da versão. Ela também deve passar por *merge* de volta para a ramificação *develop*, que pode ter progredido desde que o lançamento foi iniciado. O uso da ramificação dedicada ao preparo de lançamentos permite o trabalho paralelo, ou seja, enquanto uma equipe aperfeiçoa o lançamento atual, a outra equipe continua a trabalhar nos recursos para o próximo lançamento. Os comandos utilizados para realizar as tarefas, com e sem gitflow:

| Git | Git flow | Função |
|-----|----------|--------|
| `git checkout develop`<br>`git checkout -b release/0.1.0` | `git flow release start 0.1.0` | Criar *branch release* e atribuir a versão. |
| `git checkout main`<br>`git merge release/0.1.0` | `git flow release finish '0.1.0'` | Finalizar *branch release*. |

![Branch Release](https://wac-cdn.atlassian.com/dam/jcr:8f00f1a4-ef2d-498a-a2c6-8020bb97902f/03%20Release%20branches.svg?cdnVersion=212)

**FONTE:** [Bitbucket](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)

### Ramificação de correção(*hotfix*)
As ramificações de manutenção ou correção (*hotfix*) são usadas para corrigir com rapidez lançamentos de produção. As ramificações de *hotfix* se parecem muito com ramificações de *release* e de *feature*, a diferença é que a *branch hotfix* é criada a partir da *main* ao invés da *develop*. Esta é a única ramificação que deve ser bifurcada direto da ramificação *main*. Assim que a correção for concluída a *branch hotfix* deve ser mergeada na *main* e na *develop* ou, ao invés da *develop*, realizar o *merge* na *branch release* atual. Ainda, a *branch main* deve ser marcada com o número da versão atualizada. A vantagem de se usar a *branch hotfix* é que o time de desenvolvimento poderá resolver problemas sem ter que interromper o fluxo de trabalho ou esperar o próximo ciclo de lançamento. Os comandos Git e Git flow para realizar a tarefa de criação das *hotfix* e, posteriormente, finaliza-las, são:

| Git | Git flow | Função |
|-----|----------|--------|
| `git checkout main`<br>`git checkout -b hotfix_branch`  | `git flow hotfix start hotfix_branch` | Mudar para a *branch main* e criar a *branch hotfix* |
| `git checkout main`<br>`git merge hotfix_branch`<br>`git checkout develop`<br>`git merge hotfix_branch`<br>`git branch -D hotfix_branch` | `git flow hotfix finish hotfix_branch` | Mudar para a *branch main*, realizar o *merge*, mudar para a *develop*, realizar o *merge* e deletar a *branch hotfix*. |

![Branch Hotfix](https://wac-cdn.atlassian.com/dam/jcr:cc0b526e-adb7-4d45-874e-9bcea9898b4a/04%20Hotfix%20branches.svg?cdnVersion=212)

**FONTE:** [Bitbucket](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)

# Assinando *commits*
Antes de falar sobre como assinar os *commits*, irei explicar do que se trata assinar um *commit*. Assinar um *commit* nada mais é do que realizar uma assinatura eletrônica criptografada, para que o autor do *commit* possa ser identificado, ou seja, permite que outras pessoas tenham a certeza sobre quem realizou o *commit*. Para realizar essa tarefa normalmente usa-se o GPG ou o S/MIME.

 ## GPG
GPG é uma acrônimo para [*GNU Privacy Guard*](https://gnupg.org/), trata-se de um software livre de criptografia e é uma alternativa ao PGP da empresa Symantec [Wikipedia](https://pt.wikipedia.org/wiki/GNU_Privacy_Guard). O GnuPG (GPG) é uma implementação completa e gratuita do padrão OpenPGP, definido pela [RFC4880](https://www.ietf.org/rfc/rfc4880.txt). O GPG permite a criptografia e a assinatura de dados e comunicações, possuindo um sistema de gerenciamento de chaves versátil, juntamente com módulos de acesso para todos os tipos de diretórios de chaves públicas. É uma ferramenta de linha de comando com recursos para fácil integração com outros aplicativos. O GnuPG também oferece suporte para S/MIME e Secure Shell (ssh). [GnuPG org](https://gnupg.org/).

Também vale citar o Gpg4win, que é uma versão do GnuPG para Windows com uma ferramenta de menu de contexto, um gerenciador de criptografia e um plug-in do Outlook para enviar e receber e-mails PGP/MIME padrão. [GnuPG org](https://gnupg.org/).

O GPG usa criptografia assimétrica, logo faz uso de uma chave pública e outra privada, sendo que a pública tem o objetivo de cifrar (criptografar) a informação que é endereçada a um receptor, portanto é a chave que o receptor (dono das chaves) e emissor da mensagem compartilham de modo seguro. Já a chave privada não deve ser compartilhada com ninguém, apenas o receptor da mensagem deve possui-la para conseguir descriptografar (decifrar) a mensagem recebida. A criptografia assimétrica oferece suporte à assinatura digital, que autentica a identidade do destinatário e garante que a mensagem não seja violada em trânsito.

Para saber mais sobre criptografia:
- [Criptografia simétrica x assimétrica: qual é a diferença? Por Valter de Souza](https://blog.mailfence.com/pt/criptografia-simetrica-x-assimetrica-qual-e-a-diferenca/)
- [PKI – Public key infrastructure](https://www.gta.ufrj.br/grad/07_2/delio/Criptografiaassimtrica.html)
- [Criptografia Assimétrica - Segurança da Informação - Dicionário de Informática](https://www.youtube.com/watch?v=GeSnN8Tt04U)
- [Entendendo Conceitos Básicos de CRIPTOGRAFIA | Parte 1/2](https://www.youtube.com/watch?v=CcU5Kc_FN_4)
- [Entendendo Conceitos Básicos de CRIPTOGRAFIA | Parte 2/2](https://www.youtube.com/watch?v=HCHqtpipwu4)

 ## S/MIME
S/MIME, ou Secure/Multipurpose Internet Mail Extensions, é uma tecnologia que permite criptografar e-mails. O S/MIME é baseado em criptografia assimétrica para proteger seus e-mails contra acessos indesejados. Além disso, ele permite assinar digitalmente seus e-mails para atestar que você é o remetente legítimo da mensagem, tornando-se uma arma eficiente contra ataques de phishing. [Fonte: GlobalSign - O que é o S/MIME e como ele funciona?](https://www.globalsign.com/pt-br/blog/what-is-s-mime)

## Mãos na massa
Nos passos descritos a seguir, utilizaremos o GPG para realizar a criptografia, mas é possível utilizar o S/MIME caso queira.

### Instalando o GPG
Para instalar o GPG no Linux basta executar os comandos:
```
sudo apt-get update
sudo apt-get install gnupg
```

No Windows será necessário fazer o download do Gpg4win, disponível em: [gpg4win](https://www.gpg4win.org/)

Caso queira, poderá deixar todas as opções marcadas quando estiver instalando o gpg4win (e.g. Kleopatra, GPA, etc).

### Realizando a criptografia
Após ter instalado o GPG no Sistema Operacional (SO), siga os passos, sempre precionando a tecla enter após cada passo:

1. Execute o comando `gpg --gen-key`;
2. Em seguida, escolha o tipo de chave que deseja gerar, sendo que a opção 1 é a opação padrão, chave usada para assinar e cifrar arquivos com algoritmo RSA;
3. Escolha o tamanho da chave, em bits, sendo que o ideal é 4096 bits;
4. Defina por quanto tempo a chave ficará válida;
5. Por fim, defina uma senha forte (alfanumérica, caractéres especiais, com mais de 12 caractéres, etc)

Enquanto a chave está sendo gerada, faça movimentos aleatórios com o mouse e pressionar teclas aleatórias do teclado para ajudar o computador na geração de números randômicos.

**Obs.1:** Caso esteja utilizando Windows, é possível realizar esse mesmo processo pelo terminal do windows ou pelo git bash. Caso não queira realizar esse processo pelo bash ou terminal, use o software Kleopatra, baixado junto com o gpg4win, e gere as chaves por lá, em Arquivo > Novo par de chaves > Criar um par de chaves OpenPGP pessoal, depois siga as mesmas recomandações citadas acima.

**Obs.2:** Dependendo da versão do GPG que esteja utilizando, o comando para gerar uma chave GPG é `gpg --default-new-key-algo rsa4096 --gen-key`

**Obs.3:** Para listar as chaves criadas use o comando `gpg --list-secret-keys --keyid-format=long`

# Bibliografia
1. [Git](https://git-scm.com/docs/git#_git_commands)
2. [Training Github](https://training.github.com/downloads/pt_BR/github-git-cheat-sheet/)
3. [Bitbucket](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)
4. [CheatSheet do git flow](https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html)
5. [GPG](https://gnupg.org/)