# Knative + Istio on Kubernetes: Canary Deployment Example

## Visão Geral

Este projeto demonstra uma arquitetura moderna baseada em **Knative** e **Istio** rodando em um cluster **Kubernetes** com suporte a múltiplas plataformas de nuvem (Google Cloud, AWS, Azure) e ambientes On-Premises.

A solução permite deploys serverless e gerenciamento de tráfego com controle granular por revisão usando recursos como:

- **Knative Serving** para deploys serverless e gestão de revisões.
- **Istio** para roteamento de tráfego inteligente e observabilidade.
- **Canary deployment** com distribuição de tráfego entre múltiplas versões de uma aplicação.

## Topologia

A imagem abaixo representa a topologia de rede e fluxo de tráfego com Knative e Istio, incluindo um exemplo de Canary Deployment onde 80% do tráfego vai para a `revision v1` e 20% para a `revision v2`.

![Canary Deployment Topology](./canary-topology.png)

## Como Funciona

1. O tráfego externo passa por um Load Balancer.
2. O Istio Ingress Gateway gerencia a entrada de tráfego para o cluster Kubernetes.
3. O Knative Service controla as revisões da aplicação.
4. A distribuição de tráfego é feita entre diferentes revisões da aplicação (v1 e v2).
5. Isso permite atualizações seguras com rollback automático se necessário.

## Requisitos

- Kubernetes cluster (GKE, EKS, AKS ou On-Premise)
- Istio instalado
- Knative Serving instalado

## Exemplo de Deploy

Você pode utilizar a configuração do chart incluído nesse repo como base para um serviço com canary deployment:

Criei uma demo simples em helm, chamando variáveis (no hardcode guys, fica a fica), bem genérica para qualquer time pode utilizar, utilizei duas imagens públicas somente para testes, totalmente funcional, basicamente você só edita o values.yaml de acordo com as necessidades do seu ambiente.
Agora é só parametrizar e refatorar para ser deployada na sua esteira desejada (Gitlab, Jenkins, etc)
