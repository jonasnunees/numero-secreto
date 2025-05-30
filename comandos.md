# GitHub -> Plataforma onde hospedamos o código
# Git -> Ferramenta onde fazemos o controle de versões do código

## As mensagens dos commits devem ser simples e objetivas. A seguir, listamos algumas orientações para isso:

- Mantenha a mensagem curta e concisa: A primeira linha da mensagem deve conter, no máximo, 72 caracteres. Caso seja necessário uma descrição adicional, você deve pular uma linha e adicionar os detalhes, como o contexto, da mudança realizada.
- Uso de verbo no infinitivo: É comum que a mensagem do commit inicie com um verbo no infinitivo que descreva a alteração feita, como “adicionar”, “corrigir” ou “atualizar”. Em sequência, são adicionados detalhes concisos da mudança. Por exemplo: “Atualizar texto do título da página”.
- Evite detalhes técnicos: Não inclua detalhes técnicos complexos na mensagem de commit. Esses detalhes podem ser adicionados nos comentários de código ou na documentação.

### converter o diretório do computador em um repositório Git

```
git init
```

> obs.: caso não tenha certeza que o diretório já tenha sido convertido para um repositório Git, execute o comando git status.
> Se aparecer a mensagem fatal: not a git repository (or any of the parent directories): .git, isso significa que o diretório atual não é um repositório Git e você pode então executar o comando git init.

### adicionar todos os arquivos no repositório Git

```bash
git add .
```

### fazendo um commit

```bash
git commit -m "projeto inicial"
```

### se identificar para o Git local

```bash
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

> O comando abaixo renomeia a branch atual para "main"
> Por padrão, o Git criava a branch principal com o nome "master"
> Porém, hoje em dia, o nome "main" é mais comum e usado por padrão no GitHub
> Esse comando garante que a branch principal tenha o nome correto antes de enviar para o repositório remoto

```bash
git branch -M main
```

> Este comando adiciona um repositório remoto com o nome "origin"
> "origin" é um nome padrão usado para se referir ao repositório remoto principal
> A URL "git@github.com:jonasnunees/numero-secreto.git" usa o protocolo SSH para se conectar ao GitHub
> Isso permite que você envie (push) ou receba (pull) alterações sem digitar login e senha, desde que sua chave SSH esteja configurada
> Em resumo: conecta seu repositório local ao repositório remoto hospedado no GitHub

```bash
git remote add origin git@github.com:jonasnunees/numero-secreto.git
```

> Este comando envia os commits da branch "main" do repositório local para o repositório remoto chamado "origin"
> A opção "-u" cria um vínculo entre a branch local e a remota, tornando "origin main" o destino padrão para futuros "git push" e "git pull"
> Ou seja, nas próximas vezes, você poderá simplesmente usar "git push" sem precisar repetir "origin main"

```bash
git push -u origin main
```

> Este comando gera uma nova chave SSH no seu computador
> O tipo da chave é "ed25519", que é mais seguro e moderno que o antigo "rsa"
> A opção -C adiciona um comentário à chave, geralmente seu e-mail, para identificação
> Substitua "your_email@example.com" pelo e-mail da sua conta do GitHub

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

### Listar repositórios remotos:

```bash
git remote -v

// a saída será algo semelhante a:
origin   https://github.com/seu-usuario/seu-projeto.git (fetch)
origin   https://github.com/seu-usuario/seu-projeto.git (push)
```

### Remover um repositório remoto

```bash
git remote remove origin
```

### Alterar a URL de um repositório remoto

```bash
// exemplo
git remote set-url origin https://github.com/seu-usuario/seu-repositorio.git
```

### Renomear um repositório remoto

```bash
git remote rename origin novo-origin
```

### Mostra o histórico de commits do repositório com detalhes como hash, autor, data e mensagem

```bash
git log
```

### O Git oferece a possibilidade de adicionar mais de um autor a um commit. Para isso, após escrever a mensagem do commit, pulamos duas linhas e usamos a palavra-chave Co-authored-by:, seguido do nome e e-mail associado ao GitHub (entre < >) de cada pessoa colaboradora.
> Cada coautor deve estar em uma linha diferente, como é mostrado no exemplo a seguir:

```bash
$ git commit -m "Adicionar nova funcionalidade.
>
>
Co-authored-by: NOME <nome@email.com>
Co-authored-by: OUTRO-NOME <outro@email.com>"
```

### Comando para baixar os commits do repositório remoto para o repositório local

```bash
git pull origin main
```