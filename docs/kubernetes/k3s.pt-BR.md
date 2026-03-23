---
sidebar_label: K3s Kubernetes
---

# Kubernetes com K3s

Para cargas de trabalho que exigem uma plataforma de orquestração de contêineres leve e altamente eficiente, a SovereignSecure Cloud oferece suporte para o **K3s**.

## O que é o K3s?

O K3s é uma distribuição Kubernetes certificada e de alta disponibilidade, projetada para cargas de trabalho de produção em ambientes com recursos restritos, de borda (edge) ou IoT. Ele empacota todos os componentes do Kubernetes em um único binário.

## Principais Vantagens

* **Leve:** Tem um uso de memória (footprint) muito pequeno em comparação com o Kubernetes padrão, deixando mais recursos disponíveis para seus aplicativos reais.
* **Provisionamento Rápido:** Os clusters inicializam incrivelmente rápido, tornando-o ideal para pipelines de CI/CD efêmeros ou escalonamento rápido.
* **Seguro por Padrão:** Projetado com a segurança em mente, fornecendo uma superfície de ataque reduzida devido às suas dependências enxutas.

## Implantação

Os clusters K3s podem ser ativados rapidamente usando nossos Catálogos de Serviços do CMP ou gerenciados via Infraestrutura como Código (Terraform) em instâncias de computação da SovereignSecure.