# Weather App – CI/CD Multi-Environment com Azure DevOps

### Visão Geral
Este projeto é a evolução do **Weather App – Azure Static Web Apps**, com foco na aplicação de práticas reais de **DevOps**, automação de deploy e **segregação de ambientes**.

A aplicação é uma web app estática desenvolvida em **HTML, CSS e JavaScript puro**, hospedada no **Azure Storage (Static Website)** e publicada por meio de um pipeline completo de **CI/CD no Azure DevOps**.

O objetivo é simular um cenário corporativo implementando:

- pipeline de **CI/CD estruturado**
- **artefato imutável** gerado no build
- **promoção controlada entre ambientes** (TESTE → QA → PRODUÇÃO)
- **aprovação manual em produção**
- autenticação segura com **Service Connection + RBAC**
- infraestrutura **serverless de baixo custo**

Sem utilização de **Storage Account Keys**, seguindo o princípio do **menor privilégio**.
---
## Arquitetura
### Diagrama simplificado
<img width="1210" height="403" alt="image" src="https://github.com/user-attachments/assets/ca75a435-85e7-496f-a18e-693863d65fc3" />




---
### Componentes Azure
| Recurso | Função |
|--------|--------|
| Azure Storage (TESTE) | Hospedagem da aplicação – ambiente de testes |
| Azure Storage (QA) | Hospedagem da aplicação – ambiente de validação |
| Azure Storage (PRODUÇÃO) | Hospedagem da aplicação – ambiente produtivo |
| Azure DevOps Pipelines (YAML) | Orquestração do CI/CD |
| Pipeline CI | Build e geração do artefato `.zip` |
| Pipeline CD | Distribuição do artefato entre os ambientes |

A aplicação é servida diretamente pelo **Azure Storage**, sem backend ou containers.
### Fluxo resumido
<img width="1366" height="260" alt="image" src="https://github.com/user-attachments/assets/7d98841a-4092-40b4-beb8-8b9fbe3b09da" />

 

A aplicação é servida diretamente pelo Storage, sem backend ou containers.

---

## Conceitos Azure e DevOps aplicados
- CI/CD com Azure DevOps  
- Artefato imutável e versionado  
- Promoção entre ambientes isolados  
- RBAC e Service Connections  
- Aprovação manual em produção  
- Deploy idempotente  
- Agentes efêmeros de pipeline  

---

## Resultado
✔️ Deploy automático em TESTE  
✔️ Deploy automático em QA  
✔️ Deploy em PRODUÇÃO com aprovação manual  
✔️ Rastreabilidade completa de build e release  

---

## Relação com o Projeto 1

| Aspecto | Projeto 1 | Projeto 2 |
|--------|-----------|-----------|
| Serviço | Azure Static Web Apps | Azure Storage Static Website |
| CI/CD | GitHub Actions | Azure DevOps Pipelines |
| Ambientes | Produção | Teste / QA / Produção |
| Aprovação | ❌ | Manual em PRODUÇÃO |
| Artefatos | Automáticos | Build + Artifact |
| DevOps real | Básico | Profissional |

O Projeto 2 representa a evolução para um fluxo mais próximo de ambientes corporativos, com controle de promoção e segregação de ambientes.

---

## Links da Aplicação

- **TESTE** → [Acessar ambiente](https://weatherappteste.z13.web.core.windows.net/)  
- **QA** → [Acessar ambiente](https://weatherappqa.z13.web.core.windows.net/)  
- **PRODUÇÃO** → [Acessar ambiente](https://weatherappproduction.z13.web.core.windows.net/)

---
- **Link para o projeto** : [Weather App – Azure Static Web Apps](https://github.com/JulioCesarSantosdv/weather-app-azure) 
---


