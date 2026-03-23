---
sidebar_label: Balanceadores de Carga
---

# Balanceadores de Carga

Na SovereignSecure Cloud, os Balanceadores de Carga como Serviço (LBaaS) distribuem o tráfego de aplicativos de entrada em várias Instâncias de Computação. Isso aumenta a disponibilidade, a tolerância a falhas e a escalabilidade de seus aplicativos. Nosso serviço de balanceamento de carga é integrado nativamente ao SDN subjacente e possui a tecnologia do OpenStack Octavia.

## Componentes Principais

Para configurar um balanceador de carga, você deve configurar vários componentes interconectados:

*   **Balanceador de Carga (Load Balancer):** O objeto raiz que ocupa um endereço IP específico em sua sub-rede. Para torná-lo acessível pela Internet, você pode associar um IP Flutuante a ele.
*   **Ouvinte (Listener):** Um processo que verifica solicitações de conexão em um protocolo e porta configurados (ex.: HTTP na porta 80 ou TCP na porta 443).
*   **Pool:** Um grupo lógico de Instâncias de Computação de back-end (Membros) que atendem às solicitações roteadas pelo Ouvinte.
*   **Membro (Member):** Uma Instância de Computação individual (especificada por seu IP privado e porta) pertencente a um Pool.
*   **Monitor de Integridade (Health Monitor):** Um serviço que executa pings periodicamente nos Membros do Pool para garantir que estejam saudáveis. Se um Membro falhar em uma verificação de integridade, o balanceador de carga para de rotear o tráfego para ele até que se recupere.

## Principais Recursos

*   **Balanceamento de Carga de Camada 4 e Camada 7:** Roteie o tráfego com base em protocolos TCP/UDP de baixo nível (Camada 4) ou cabeçalhos HTTP/HTTPS em nível de aplicativo (Camada 7).
*   **Descarregamento/Terminação TLS (TLS Offloading/Termination):** Centralize os certificados SSL/TLS no próprio balanceador de carga, liberando suas instâncias de back-end da tarefa intensiva de CPU de criptografar e descriptografar o tráfego.
*   **Algoritmos de Roteamento Avançados:** Escolha como o tráfego é distribuído entre suas instâncias:
    *   *Round Robin:* Distribui as solicitações uniformemente entre todos os membros de forma sequencial.
    *   *Least Connections (Menos Conexões):* Envia novas solicitações ao membro com o menor número de conexões ativas.
    *   *Source IP (IP de Origem):* Roteia solicitações do mesmo IP de cliente para o mesmo membro de back-end (Persistência de Sessão).

## Criando um Balanceador de Carga

Você pode provisionar e configurar Balanceadores de Carga através da Plataforma de Gerenciamento de Nuvem (CMP):

1.  Navegue até **Redes > Balanceadores de Carga** (Network > Load Balancers).
2.  Clique em **Criar Balanceador de Carga** (Create Load Balancer).
3.  **Detalhes Básicos:** Forneça um nome, selecione a VPC/Sub-rede de destino onde o balanceador de carga deve residir e atribua um endereço IP.
4.  **Configuração do Ouvinte:** Especifique o protocolo (ex.: HTTP) e a porta (ex.: 80) para o tráfego de entrada.
5.  **Configuração do Pool:** Escolha um algoritmo de balanceamento de carga (ex.: Round Robin).
6.  **Membros:** Selecione as Instâncias de Computação de back-end que processarão o tráfego e especifique suas portas de escuta.
7.  **Monitor de Integridade:** Defina o protocolo de verificação de integridade, o intervalo de ping e os limites de tempo limite (timeout).

### Exposição Pública e Segurança

Por padrão, um novo balanceador de carga só é acessível dentro de sua sub-rede interna. 

*   **Acesso Público:** Para tornar o balanceador de carga acessível pela Internet pública, navegue até **Redes > IPs Flutuantes** (Network > Floating IPs) e associe um IP Flutuante diretamente à porta VIP (IP Virtual) do balanceador de carga.
*   **Grupos de Segurança:** Certifique-se de que os **Grupos de Segurança** anexados às suas Instâncias de Computação de back-end permitam o tráfego de entrada nas portas dos membros com origem no endereço IP do balanceador de carga.