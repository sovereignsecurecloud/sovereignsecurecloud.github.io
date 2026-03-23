---
sidebar_label: Pares de Chaves
sidebar_position: 5
---

# Pares de Chaves

Um **Par de Chaves** é um método de autenticação seguro usado para acessar suas instâncias na SovereignSecure Cloud. Em vez de depender de senhas tradicionais, que podem ser vulneráveis a ataques de força bruta, os pares de chaves usam criptografia de chave pública (SSH) para garantir que apenas usuários autorizados possam se conectar aos recursos de computação.

Um par de chaves consiste em duas partes:

*   **Chave Pública:** Armazenada dentro do seu projeto na SovereignSecure Cloud e injetada automaticamente na sua instância (geralmente em `~/.ssh/authorized_keys` para Linux) quando ela é provisionada.
*   **Chave Privada:** Mantida de forma segura na sua máquina local e usada pelo seu cliente SSH para provar sua identidade.

## Criando um Novo Par de Chaves

Você pode gerar um novo par de chaves diretamente através do Console da Nuvem:

1. Navegue até **Computação > Pares de Chaves** no Console da Nuvem.
2. Clique em **Criar Par de Chaves** (Create Key Pair).
3. Insira um **Nome** descritivo para o seu par de chaves.
4. Selecione o **Tipo de Chave** (Key Type - SSH é o padrão).
5. Clique em **Criar**.
6. **Importante:** Seu navegador fará o download automático da Chave Privada (geralmente um arquivo `.pem`). Esta é a *única* vez que você poderá baixar esta chave privada. Armazene-a em um local seguro na sua máquina local.

## Importando um Par de Chaves Existente

Se você já possui seu próprio par de chaves SSH gerado via `ssh-keygen` (Linux/macOS) ou PuTTYgen (Windows), você pode importar a chave pública para a plataforma.

1. Navegue até **Computação > Pares de Chaves**.
2. Clique em **Importar Par de Chaves** (Import Key Pair).
3. Insira um **Nome** para identificar este par de chaves.
4. Cole o conteúdo da sua **Chave Pública** (ex.: o conteúdo do seu arquivo `id_rsa.pub` ou `id_ed25519.pub`) na caixa de texto fornecida.
5. Clique em **Importar**.

## Conectando-se à sua Instância

Uma vez que sua instância esteja em execução e tenha um IP Flutuante atribuído, você pode se conectar a ela usando sua chave privada.

### Linux / macOS

Abra seu terminal e use o comando `ssh`, especificando o caminho para o seu arquivo de chave privada usando a flag `-i`:

```bash
chmod 400 minha-chave-privada.pem  # Garanta que a chave tenha permissões estritamente seguras
ssh -i /caminho/para/minha-chave-privada.pem usuario@<IP-Flutuante-da-Instancia>
```

*(Nota: O `usuario` padrão depende da Imagem usada, como `ubuntu`, `centos`, `cloud-user` ou `debian`)*.

### Windows (PuTTY)

1. Abra o **PuTTY**.
2. No campo **Host Name (or IP address)** (Nome do Host ou endereço IP), insira o endereço IP Flutuante da instância.
3. No menu à esquerda, navegue até **Connection > SSH > Auth > Credentials** (Conexão > SSH > Autenticação > Credenciais).
4. Clique em **Browse** (Procurar) e selecione seu arquivo de chave privada (O PuTTY requer o formato `.ppk`. Se você baixou um arquivo `.pem`, use o PuTTYgen para convertê-lo).
5. Clique em **Open** (Abrir) para iniciar a conexão.