📦 Knative com Istio - Hello World com Canary Deployment
🚀 Overview
Knative é uma plataforma Kubernetes para construir, implantar e gerenciar cargas de trabalho serverless. Ele abstrai a complexidade de criação e gerenciamento de contêineres, oferecendo recursos como autoscaling, roteamento e versões de deploy integradas.

Istio é uma malha de serviço que complementa o Kubernetes oferecendo observabilidade, segurança, e controle de tráfego. Quando integrado ao Knative, o Istio gerencia o roteamento do tráfego entre versões de um serviço (como em deploys canário), além de prover métricas e tracing.

🌐 Fluxo
O usuário faz uma requisição para a aplicação (ex: https://hello.example.com).

A requisição passa pelo Load Balancer (GKE/EKS/AKS).

O tráfego é roteado para o Istio Ingress Gateway.

O Knative Service (hello-world) recebe a requisição.

O serviço roteia o tráfego entre duas revisões: v1 (90%) e v2 (10%), conforme configurado em uma estratégia de canary deployment.
