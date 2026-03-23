---
sidebar_label: Instâncias de GPU
sidebar_position: 3
---

# Instâncias de GPU

A SovereignSecure Cloud oferece instâncias especializadas de Máquinas Virtuais equipadas com GPUs. Essas instâncias são altamente recomendadas para cargas de trabalho de computação intensiva, como Aprendizado de Máquina (Machine Learning), treinamento de IA, renderização 3D e computação de alto desempenho (HPC).

## Criar Instâncias de GPU

Você pode criar instâncias de GPU diretamente pelo Console da Nuvem ou usando ferramentas de Infraestrutura como Código (IaC), como Terraform e OpenTofu.

### Escolhendo um Flavor (Tamanho) de GPU

Ao provisionar uma instância de GPU, você deve selecionar um flavor que garanta aceleração de hardware. Em nosso ambiente, os flavors de GPU são normalmente indicados pelo prefixo `g`.

| Série de Flavor | Caso de Uso |
| ----------- | ----------- |
| **Série g** | Cargas de trabalho de GPU de uso geral, aprendizado de máquina e processamento de vídeo. |

### Considerações sobre Imagens

Para utilizar totalmente o hardware da GPU, o sistema operacional deve ter os drivers NVIDIA grid ou passthrough corretos instalados.

* Recomendamos escolher uma das **Imagens Públicas habilitadas para GPU** pré-configuradas fornecidas pela SovereignSecure Cloud, que vêm com os drivers e kits de ferramentas (toolkits) CUDA necessários pré-instalados.
* Se você trouxer sua própria imagem, será responsável por instalar os drivers apropriados por meio de um Script de Usuário (cloud-init) durante a inicialização.

### Configurações de SO

Assim como nas instâncias padrão, você deve determinar como o armazenamento de bloco raiz será criado:

* **Criar Novo e Configurar:** Crie um novo volume de armazenamento de bloco raiz usando uma Imagem selecionada. Certifique-se de que o tamanho do disco atenda aos requisitos mínimos para instalações de drivers de GPU (normalmente 40 GB+ é recomendado).
* **Usar Recurso Existente:** Inicialize a partir de um volume de armazenamento de bloco ou snapshot criado anteriormente que já contenha a configuração do seu ambiente de GPU.

### Ciclo de Vida e Faturamento de Instâncias de GPU

Os recursos de GPU têm alta demanda e são estritamente alocados no nível do hipervisor usando perfis de PCI passthrough ou vGPU. Esteja ciente dos seguintes limites operacionais:

!!! warning "Nota de Faturamento"
    Como o hardware é fortemente reservado, **Instâncias de GPU incorrerão em taxas normais (100%) mesmo quando paradas**. Para interromper completamente o faturamento de uma instância de GPU, você deve **Encerrar (Excluir)** a instância. 

!!! note "Migração ao Vivo (Live Migration)"
    Devido à vinculação de hardware de dispositivos PCI, instâncias de GPU **não podem** ser migradas ao vivo entre hipervisores. Eventos de manutenção no host subjacente exigirão que a instância seja completamente desligada e iniciada em um novo host.