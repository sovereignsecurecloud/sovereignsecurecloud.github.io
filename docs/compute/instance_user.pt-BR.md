---
sidebar_label: Guia do Usuário
sidebar_position: 2
---

# Guia do Usuário da Instância

## Criar Instâncias
Você pode criar instâncias usando as configurações abaixo ou usando Terraform/OpenTofu. Para criar instâncias usando Terraform/OpenTofu, selecione a página Criar Instância.

### Configurações de SO
Determine como será criado o armazenamento em bloco raiz que será usado quando uma instância for criada.

* Selecione **Criar Novo e Configurar** (Create New and Set up) ou **Usar Recurso Existente** (Use Existing Resource).
* Se você selecionar Criar Novo e Configurar, crie o armazenamento em bloco raiz usando uma imagem.
* Se você selecionar Usar Recurso Existente, use um armazenamento em bloco ou snapshot criado anteriormente.

### Imagem
Selecione a imagem que contém o sistema operacional que você precisa. Você pode escolher entre imagens públicas fornecidas pela SovereignSecure Cloud, imagens que você criou anteriormente ou imagens compartilhadas.

Os flavors (tamanhos) de instância disponíveis variam de acordo com a imagem que você escolher, portanto, recomendamos que você escolha uma imagem primeiro ao criar uma instância.

| SO      | Tamanho do Disco do SO |  Memória    |
| ----------- | --------------------|-----------|
| Linux       | 10GB      | 4GB     |
| Windows       | 40GB     | 4GB     |

### Armazenamento em Bloco Raiz
Configure o armazenamento em bloco raiz de acordo com as configurações do SO.

* Se você selecionar __Criar Novo e Configurar__, crie o armazenamento em bloco raiz especificando o __tipo de armazenamento em bloco__ e o __tamanho do armazenamento em bloco__.
* Se você selecionar Usar __Recurso Existente__, especifique o __recurso original__ a ser usado como armazenamento em bloco raiz.

### Recurso Original
Você pode selecionar um __armazenamento em bloco__ ou __snapshot__ criado anteriormente.

Ao selecionar __armazenamento em bloco__, use o armazenamento em bloco criado anteriormente como o armazenamento em bloco raiz.
Ao selecionar __snapshot__, o armazenamento em bloco raiz é criado usando um snapshot criado anteriormente.

### Tamanho do Armazenamento em Bloco
Especifique o tamanho do armazenamento em bloco raiz de uma instância.

O tamanho do armazenamento em bloco deve ter pelo menos o tamanho mínimo exigido pela imagem.
O tamanho do armazenamento em bloco raiz varia dependendo do flavor da instância.

| Flavors      | Tamanho de Armazenamento em Bloco Suportado |
| ----------- | --------------------|
| g       | 10GB      |
| m       | 40GB     |

!!! note "Nota"
    Como você é cobrado pelo tamanho do armazenamento em bloco, não é eficiente aumentar o tamanho padrão do armazenamento em bloco sem consideração. Recomendamos que você adicione armazenamento em bloco adicional conforme necessário.
    * Se você selecionar armazenamento em bloco para Usar Recurso Existente nas configurações do SO, não poderá alterar o tamanho do armazenamento em bloco.
    * Se você selecionar snapshot para Usar Recurso Existente nas configurações do SO, o tamanho do armazenamento em bloco deverá ser igual ou maior que o tamanho original do armazenamento em bloco.

### Tipo de Armazenamento em Bloco
Determina o tipo de armazenamento em bloco padrão de uma instância.

Escolha entre HDD ou SSD. A escolha do tipo de armazenamento em bloco afeta o preço e o desempenho.
Você não pode alterar o tipo de armazenamento em bloco após a criação da instância.

!!! note "Nota"
    Se você selecionar Usar Recurso Existente nas configurações do SO, não poderá alterar o tipo de armazenamento em bloco.

### Zona de Disponibilidade
Se uma zona de disponibilidade não for especificada, uma zona aleatória será selecionada. Uma instância só pode usar um armazenamento em bloco se ambos existirem na mesma zona de disponibilidade. Se o armazenamento em bloco que você deseja usar existir em uma zona de disponibilidade específica, selecione essa zona.

!!! note "Nota"
    * Recursos em uma VPC podem ser usados em qualquer zona de disponibilidade.
    * Se você selecionar Usar Recurso Existente nas configurações do SO, não poderá alterar a zona de disponibilidade.

Para obter mais detalhes sobre zonas de disponibilidade, consulte Zona de Disponibilidade na Visão Geral de Instâncias.

### Flavor (Tamanho/Perfil)
Você pode selecionar vários flavors dependendo das especificações de desempenho de hardware virtual. No entanto, a escolha de alguns flavors pode ser limitada dependendo do desempenho de hardware virtual exigido pela sua imagem. Para mais detalhes, consulte Visão Geral de Instâncias.

!!! note "Nota" 
    1 vCPU refere-se a um soquete composto por um thread e um núcleo, o número de threads e o número de núcleos por soquete são constantes, um cada.

Os flavors de instância podem ser alterados no console da SovereignSecure Cloud mesmo após a criação da instância, de especificações mais altas para mais baixas e vice-versa. No entanto, observe que alguns flavors não podem ser alterados. Consulte Modificar flavor para obter detalhes.

!!! warning "Aviso"
     O armazenamento em bloco raiz de uma instância não pode ser alterado alterando os flavors da instância.

### Número de Instâncias
Você pode especificar o número de instâncias que deseja criar ao criar várias instâncias com a mesma imagem, zona de disponibilidade, flavor, tamanho de armazenamento em bloco, par de chaves e configurações de rede. Os nomes das instâncias serão o nome especificado, com números como -1 e -2 anexados ao final. Por exemplo, criar duas instâncias chamadas `minha-instancia` resultará em `minha-instancia-1` e `minha-instancia-2`. O número máximo de instâncias que você pode criar de uma vez é 10.

Ao criar várias instâncias sem especificar uma zona de disponibilidade, cada instância será criada em uma zona de disponibilidade selecionada aleatoriamente. Por exemplo, se duas instâncias forem criadas sem especificar uma zona de disponibilidade, elas poderão ser criadas na mesma zona ou em zonas diferentes. Se todas as instâncias precisarem ser criadas na mesma zona de disponibilidade, selecione uma zona específica.

!!! note "Nota" 
    Se você selecionar armazenamento em bloco para Usar Recurso Existente nas configurações do SO ou Usar Interface de Rede Existente nas configurações de rede, o número de instâncias será limitado a 1.

### Par de Chaves
Use um par de chaves existente ou crie um novo par de chaves. Para registrar um par de chaves existente, consulte Importar Par de Chaves (Windows) para usuários do Windows e Importar Par de Chaves (Mac e Linux) para usuários de Mac e Linux.

!!! note "Nota"
    O Par de Chaves é um recurso atribuído à conta do usuário, portanto, não é excluído quando você exclui um projeto.

### Rede
Selecione uma sub-rede definida na sua VPC para se conectar a uma instância. Para cada sub-rede selecionada, uma interface de rede é criada na instância para se conectar a essa sub-rede. Você pode alterar a ordem das sub-redes selecionadas para alterar as interfaces de rede, caso em que a primeira interface de rede (eth0) será definida como o gateway padrão.

Para obter mais detalhes sobre como criar e gerenciar redes, consulte a Visão Geral de VPC.

### IP Flutuante
Selecione se deseja usar um IP flutuante após a criação da instância. Se você habilitar essa opção, um novo IP flutuante será criado e conectado à primeira interface de rede. Observe que a primeira interface de rede deve estar conectada a uma sub-rede onde um gateway de internet esteja configurado.

O IP Flutuante pode ser gerenciado em Instância > Gerenciamento ou Instância > IP Flutuante. Para mais detalhes sobre IP flutuante, consulte o Guia do Console VPC.

### Grupo de Segurança
Selecione os grupos de segurança nos quais a instância será incluída. Uma instância pode ser incluída em vários grupos de segurança, caso em que:

* A instância pode se comunicar pela rede com todas as outras instâncias incluídas em cada grupo de segurança. Ao lidar com uma instância com dados confidenciais que não devem ser acessíveis por outras instâncias, você deve selecionar cuidadosamente os grupos de segurança.
* As regras de cada grupo de segurança são agregadas e aplicadas à comunicação de rede externa da instância.

Para mais detalhes sobre grupos de segurança, consulte o Guia do Console VPC.

### Armazenamento em Bloco Adicional
Selecione se você anexará um armazenamento em bloco adicional após a criação da instância. Se você habilitar essa opção, um novo armazenamento em bloco separado do armazenamento em bloco raiz será criado e anexado à instância. Assim como no armazenamento em bloco raiz, você pode especificar o nome, o tipo de armazenamento e o tamanho do armazenamento em bloco adicional que criar.

Ao usar o armazenamento em bloco raiz apenas para o SO e armazenar seus aplicativos e dados usados com frequência no armazenamento em bloco adicional, você pode facilmente migrar ou copiar seus aplicativos e dados usando os recursos de anexar/desanexar e de snapshot de armazenamento em bloco. Além disso, quando ocorrer uma falha na instância, você poderá recuperar facilmente seus serviços simplesmente desanexando o armazenamento em bloco adicional e anexando-o a outra instância.

O armazenamento em bloco também pode ser gerenciado em Instância > Armazenamento em Bloco. Para obter mais detalhes sobre armazenamento em bloco, consulte o Guia de Armazenamento em Bloco.

### Política de Posicionamento
Você pode usar políticas de posicionamento (placement policies) para colocar instâncias em hypervisors diferentes. Ao definir uma política de posicionamento no momento da criação da instância, as instâncias atribuídas à mesma política de posicionamento são criadas em hypervisors diferentes.

!!! warning "Aviso"
    A criação da instância pode falhar em situações em que a implantação distribuída não for possível.

### Script de Usuário
Você pode especificar um script a ser executado após a criação da instância. O script de usuário é executado após a inicialização inicial da instância e após a conclusão do processo de inicialização, incluindo a configuração de rede. Os scripts de usuário na SovereignSecure Cloud são executados por ferramentas automatizadas, como cloud-init (Linux) e Cloudbase-init (Windows), que são incorporadas nas imagens oficiais.

!!! warning "Aviso"
    Scripts de usuário são executados com privilégios de root (Linux) / Administrador (Windows).

#### Linux
A primeira linha de um script de usuário deve começar com `#!`.

```bash
#!/bin/bash
```
...
Para que um script de usuário seja executado com êxito, os arquivos de log na instância devem ser verificados. Você pode verificar os logs de saída impressos pela saída/erro padrão do script em `/var/log/cloud-init-output.log`.

#### Windows
As imagens do Windows suportam os formatos Batch e PowerShell para scripts de usuário. O formato é determinado por um indicador especificado na primeira linha.

* Script Batch
```batch
rem cmd
...
```

* Script PowerShell
```powershell
#ps1_sysnative
...
```
Para usar tanto Batch quanto PowerShell no seu script, use o formato a seguir.

* Formato EC2
```
<script>
...
</script>
<powershell>
...
</powershell>
```
Logs de scripts de usuário podem ser encontrados em 
>  *C:\Program Files\Cloudbase Solutions\Cloudbase-Init\log\cloudbase-init.*

Para obter mais detalhes sobre os scripts de usuário, consulte os guias do cloud-init ou Cloudbase-init.

### Recursos Adicionais da Instância
#### Alterar o Status da Instância
O status de uma instância pode ser alterado parando, encerrando (terminando), excluindo e iniciando-a.

Para obter mais detalhes sobre os recursos do hypervisor e as taxas de parada, encerramento e exclusão de instâncias, consulte a tabela abaixo.

| Classificação | Parar Instância | Encerrar Instância | Excluir Instância |
| -------------- | ------------- | ------------------ | --------------- |
| **Recursos do Hypervisor** | O recurso permanece alocado | O recurso é devolvido e realocado quando a instância é iniciada | O recurso é removido |
| **Preço da instância** | Preço da parada aplicado | Gratuito | Gratuito |
| **Preço de outros recursos conectados** | Cobrado | Cobrado | Cobrado |

!!! note "Nota"
    Instâncias de GPU não podem ser encerradas e incorrerão em taxas normais (100%) quando paradas.

#### Criar Imagem
Crie uma imagem a partir do armazenamento em bloco raiz de uma instância. É recomendável parar as instâncias antes de criar uma imagem para garantir a integridade dos dados.

Embora seja possível criar uma imagem a partir de uma instância que não tenha espaço livre disponível em seu armazenamento em bloco raiz, essas imagens são inutilizáveis por outras instâncias porque não podem ser inicializadas corretamente. Antes de criar uma imagem, certifique-se de que sua instância tenha pelo menos 100 KB de espaço livre.

As imagens criadas são registradas como imagens privadas em Computação > Imagem. Você pode usar a imagem registrada para criar uma instância com um armazenamento em bloco idêntico ao da instância original.

!!! warning "Aviso"
    O tamanho da imagem criada pode ser maior do que o uso real do armazenamento em bloco raiz.

#### Associar/Desassociar IP Flutuante
O IP flutuante pode ser associado ou desassociado de uma instância, independentemente do status da instância. Se você não tiver nenhum IP flutuante disponível ou se o IP flutuante que deseja não estiver disponível, poderá criar um clicando em Criar. Como alternativa, o IP flutuante também pode ser criado em Rede > VPC > IP Flutuante.

Para obter mais detalhes sobre IPs flutuantes, consulte a Visão Geral de VPC.

#### Modificar Grupo de Segurança
Os grupos de segurança de uma instância podem ser modificados independentemente do status da instância. Os grupos de segurança modificados são aplicados imediatamente.

Para obter mais detalhes sobre grupos de segurança, consulte Grupo de Segurança e a Visão Geral de VPC.

#### Alterar Sub-rede de Rede
A sub-rede de rede de uma instância só pode ser alterada enquanto a instância estiver parada. Ao adicionar uma sub-rede, uma interface de rede que será conectada a essa sub-rede é criada automaticamente na sua instância. Se você adicionar várias sub-redes de uma só vez, a ordem das interfaces de rede recém-criadas na instância será definida aleatoriamente. A exclusão de uma sub-rede de uma instância exclui automaticamente a interface de rede que foi criada junto com a sub-rede.

#### Modificar Flavor
Os flavors de instância podem ser alterados quando uma instância for parada. Se uma instância estiver em execução, clique em Parar Instância em Recursos Adicionais para parar a instância.

Você só pode alterar uma instância para outro flavor que seja compatível com o seu flavor atual.

* Instâncias de flavor `m2`, `c2`, `r2`, `t2`, `x1` podem ser alteradas para flavors `m2`, `c2`, `r2`, `t2`, `x1`.
* Instâncias de flavor `m2`, `c2`, `r2`, `t2`, `x1` não podem ser alteradas para flavors `u2`.
* Instâncias de flavor `u2` não podem ser alteradas para outros flavors depois de criadas, nem mesmo para as do mesmo flavor `u2`.

Ao modificar flavors, as tarefas de redimensionamento e confirmação de redimensionamento da instância continuam. Quando todas as tarefas são concluídas, a VM muda seu status para Shutoff (Desligada). Você pode iniciar a instância clicando em Iniciar Instância em Recursos Adicionais.

!!! note "Nota" 
    O tamanho do armazenamento em bloco raiz da instância não pode ser modificado. Se uma instância exigir espaço de armazenamento em bloco adicional, anexe um armazenamento em bloco. Para obter detalhes sobre como anexar o armazenamento em bloco, consulte a Visão Geral de Armazenamento em Bloco.

As instâncias serão cobradas usando o novo flavor a partir do momento em que a modificação for concluída.

#### Alterar Detalhes do SO da Instância
Você pode alterar as informações do SO da instância, independentemente do estado da instância. 

Na página Computação > Instância, clique na instância cujas informações do SO você deseja alterar. Na guia Informações Básicas da tela de detalhes dessa instância, clique em SO > Modificar.

!!! note "Nota" 
    Você não pode alterar o tipo de SO.

#### Alterar a Descrição da Instância
Você pode alterar a descrição da instância independentemente do estado da instância. 

Na página Computação > Instância, clique na instância cujas informações deseja alterar. Na guia Informações Básicas da tela de detalhes dessa instância, clique em Descrição > Alterar.

#### Alterar o Par de Chaves da Instância
Você só poderá alterar o par de chaves da instância se a instância estiver ativa.

Na página Computação > Instância, clique na instância cujas informações do par de chaves você deseja alterar. Na guia Informações Básicas da tela de detalhes dessa instância, clique em Par de Chaves > Alterar.

Altere o par de chaves da conta padrão da instância para o par de chaves selecionado. A conta padrão da instância pode ser encontrada na guia Informações de Conexão da tela inferior de detalhes da instância.

!!! warning "Aviso"
    A alteração de um par de chaves de instância exclui todas as informações de chave pública na instância, exceto o par de chaves selecionado.

!!! note "Nota" 
    Apenas membros do projeto com permissões ADMIN para a infraestrutura básica podem alterar o par de chaves da instância, o qual não pode ser alterado se for uma instância de SO Windows.

!!! note "Nota" 
    Se a versão da imagem usada para criar a instância for baixa, o recurso para alterar os pares de chaves pode não estar disponível.

#### Gerenciar Políticas de Posicionamento
Você pode criar e excluir políticas de posicionamento e exibir uma lista de instâncias atribuídas a políticas de posicionamento.

Somente o tipo de política de posicionamento antiafinidade (anti-affinity) para posicionamento distribuído é fornecido.

Você pode excluir uma política de posicionamento mesmo se houver instâncias atribuídas a ela, caso em que as instâncias não serão excluídas.

### Pares de Chaves
#### Importar Pares de Chaves (Windows)
Você pode usar o puttygen, que é instalado quando você instala o cliente SSH PuTTY, para criar um par de chaves e registrá-lo na SovereignSecure Cloud.

Certifique-se de ter o PuTTY instalado.

Execute o puttygen.

*[Imagem: PuTTYgen]*

Selecione RSA (ou SSH-2 RSA em versões mais antigas do puttygen) em Parameters. Clique em Generate em Actions. Mova continuamente o mouse no espaço vazio para gerar a chave.

Após a geração da chave, o conteúdo do arquivo de chave pública ficará visível conforme mostrado abaixo. Cole o conteúdo da chave pública no campo Chave Pública em Obter Par de Chaves para registrar o par de chaves.

*[Imagem: Chave gerada pelo PuTTYgen]*

Clique em Save private key em Actions para salvar a chave privada. Se você salvar a chave privada deixando o campo Key passphrase em branco, aparecerá a mensagem "Are you sure you want to save this key without a passphrase to protect it?" (Tem certeza de que deseja salvar esta chave sem uma frase secreta para protegê-la?). Para usar sua chave privada convertida com mais segurança, defina uma frase secreta (passphrase) antes de salvar.

!!! warning "Aviso"
    Se você deseja fazer login automaticamente na sua instância, não deve definir uma frase secreta para a chave. Quando uma frase secreta for usada, você deve inserir manualmente a frase secreta da chave privada durante o login.

O par de chaves registrado pode ser usado para criar instâncias, e a chave privada do par de chaves deve ser usada ao acessar as instâncias. Para mais detalhes sobre como acessar instâncias, consulte Visão Geral de Instâncias.

Assim como com os pares de chaves criados na SovereignSecure Cloud, os pares de chaves importados também precisam ser gerenciados com cautela, pois chaves privadas expostas podem ser abusadas por qualquer pessoa para acessar instâncias.

#### Importar Pares de Chaves (Mac e Linux)
Pares de chaves criados usando ssh-keygen no Mac ou Linux podem ser registrados na SovereignSecure Cloud. Use o seguinte comando para criar um par de chaves.

```
$ ssh-keygen -t rsa -f minha_chave.key
```

Você pode optar por definir uma frase secreta para o par de chaves, embora isso não seja obrigatório. Se desejar usar seu par de chaves com mais segurança, recomendamos definir uma frase secreta. O arquivo com `.pub` anexado ao nome do par de chaves especificado contém a chave pública.

```
$ cat minha_chave.key.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCnnUAe36txQqk8J7VzbNuYKVQQ3gbNoClndHMX49OD+1Rw5xrDFLUKQqxbBDtlNMoA9tKBZNrQBpKr1kFEtvMIj1HPkH9ocb4MbuoVVjpkIhixbKMMJPDQ4JQJxaifsjR59YsZyDAp0aXZp+o+OB97P3S4AKPY2kQR0JdSr30+6Av6smf+3mZceAE4abzklfbyWT5slP1im/wfYEPO3QBEDl/0JbmTjKWPYI6QnbwnPRHS63SJ+Kd2QeYQYJCadv7X4mXnw81qEIWq/dx1SQkGDTNgR7lnN2ApFlU5EZcow69z6tiCr0hlyigwjGooMg3wTZvcSlYcVeTzZ755RArd ...
```
Cole o conteúdo da chave pública no campo Chave Pública em Obter Par de Chaves para registrar o par de chaves.

O par de chaves registrado pode ser usado para criar instâncias, e a chave privada do par de chaves deve ser usada ao acessar instâncias. Para mais detalhes sobre como acessar instâncias, consulte Como Acessar Instâncias.

Assim como com os pares de chaves criados na SovereignSecure Cloud, os pares de chaves importados também precisam ser gerenciados com cautela, pois chaves privadas expostas podem ser abusadas por qualquer pessoa para acessar as instâncias.