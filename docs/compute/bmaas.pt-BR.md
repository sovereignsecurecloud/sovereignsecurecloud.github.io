---
sidebar_label: Bare Metal (BMaaS)
---

# Bare Metal as a Service (BMaaS)

A SovereignSecure Cloud oferece **Bare Metal as a Service (BMaaS)** com a tecnologia do **OpenStack Ironic**. O BMaaS permite que você provisione e gerencie servidores físicos dedicados com a mesma facilidade automatizada e orientada por API que as máquinas virtuais.

## Benefícios do Bare Metal

Embora as Máquinas Virtuais sejam ideais para a maioria das cargas de trabalho, certos casos de uso exigem hardware bruto:

* **Sem Sobrecarga de Hipervisor:** Alcance 100% do desempenho de computação, memória e E/S do hardware sem o custo de abstração de um hipervisor.
* **Isolamento em Nível de Hardware:** Perfeito para os mais rigorosos regimes de segurança e conformidade que proíbem o compartilhamento de hardware multilocatário.
* **Necessidades de Hardware Especializado:** Acesso direto a recursos de hardware especializados, conjuntos de instruções de CPU de baixo nível ou dispositivos PCI específicos.
* **Virtualização Aninhada:** Traga seu próprio hipervisor (BYOH). Você pode executar sua própria pilha de virtualização (como Proxmox ou VMware) diretamente em cima de nossas instâncias bare metal.

## Como Funciona

Através da Plataforma de Gerenciamento de Nuvem (CMP) ou da CLI do OpenStack, você pode selecionar um flavor (perfil/tamanho) Bare Metal em vez de um flavor de VM padrão. 

1. O serviço **Ironic** limpa com segurança o disco físico da máquina de destino.
2. O servidor é inicializado pela rede (PXE) e a imagem do sistema operacional escolhida é gravada (flashed) diretamente na unidade física.
3. A máquina é anexada à sua VPC, operando com segurança dentro da sua camada SDN privada.