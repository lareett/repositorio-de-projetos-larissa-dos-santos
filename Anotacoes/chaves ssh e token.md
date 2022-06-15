# Chaves SSH e Token (Autenticação)

### Chave SSH

- Forma de estabelecer uma conexão segura e encriptada entre duas máquinas (local e remoto).

---

> **Gerando par de chaves pública e privada**
> 
1. No CLI **git Bash** digite:
    
    ```powershell
    ssh-keygen -t ed25519 -C larihsantos2017@gmail.com
    ```
    
    1. Assim, podemos gerar as chaves em uma **pasta oculta** na máquina e associá-las ao email (de preferencia o email da conta do github)
    2. Após o enter será exigida **uma senha.** Repita a senhas **duas vezes** e aperte enter em seguida.
    3. Logo após, a chave será gerada.

> **Colocando a chave pública no Github**
> 
1. Entrar na pasta oculta através do terminal: **cd /c/users/larih/.ssh** (usar **dir -a** lista pastas ocultas)
2. Listar as chaves com o **dir** 
3. Verificar o conteúdo da **chave pública id_ed25519.pub:** $ cat id_ed25519.pub
4. Copiar o conteúdo da chave pública e jogar no gitbub.

> **Adicionando a chave privada ao ssh-agent**
> 

**1º PASSO:** Startar o ssh-agent:

```powershell
$ eval "$(ssh-agent -s)"
> Agent pid 59566
# o número do processo pode variar
```

**2º PASSO:** Adicionar a chave privada:

```powershell
$ ssh-add id_ed25519
```

**É de extrema importancia que no CLI do bash estejamos no diretório /.ssh/ pois aí sim conseguiremos encontrar a chave facilmente para adicioná-la ao ssh-agent, já que estamos na própria pasta.**

<aside>
💡 Todo esse processo está na documentação do github em: [https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

</aside>

### Token de acesso pessoal

- É **a segunda forma de autenticação segura oferecida pelo GitHub**, mas que é bem mais “chatinha” por precisar sempre de **entrar com o usuário e a senha** (um token gerado por nós).
- Sempre que for fazer um **commit** o git pedirá seu usuário e a **senha token**, o que é uma desvantagem comparado a utilização das chaves SSH.

> **Gerando um Token de acesso pessoal**
> 

**1ºPASSO:** Acesse o link: [https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) e siga o passo-a-passo.

**2ºPASSO:** Para clonar uma pasta na sua máquina deverá ser usada o link HTTP desse repósitório. No **Git Bash**, em um diretório qualquer (de preferência chamada Workspace), digite:

```powershell
$ git clone (link HTTP)
```

**3ºPASSO:** Para que haja a clonagem será solicitado a senha token gerada no **PASSO 1**, assim que a colarmos o token o processo de clonagem se iniciará.

**Uma pasta clonada pelo terminal, ao invés de uma pasta baixada, já vem com a pasta .git/ que contém todo o versionamento de código e pra onde este repositório está apontado!!!**