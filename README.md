# Weather App – CI/CD Multi-Environment com Azure DevOps

## Descrição
Evolução do projeto **Weather App – Azure Static Web Apps**, com foco na aplicação de práticas reais de **DevOps**, automação de deploy e **segregação de ambientes**.

A aplicação é uma web app estática desenvolvida em **HTML, CSS e JavaScript puro**, hospedada no **Azure Storage (Static Website)** e publicada por meio de um pipeline completo de **CI/CD no Azure DevOps**.

Este projeto simula um cenário corporativo ao implementar:

- pipeline de **CI/CD estruturado**  
- **artefato imutável** gerado no processo de build  
- **promoção controlada entre ambientes** (TESTE → QA → PRODUÇÃO)  
- **aprovação manual em produção** via Azure DevOps Environments  
- autenticação segura com **Service Connection + RBAC**  
- infraestrutura **serverless de baixo custo** no Azure  

O objetivo é demonstrar práticas de **governança, rastreabilidade e controle de acesso**, sem utilização de chaves de Storage.

---

## Arquitetura

### Componentes Azure

| Recurso | Função |
|--------|--------|
| Azure Storage (TESTE) | Hospedagem da aplicação – ambiente de testes |
| Azure Storage (QA) | Hospedagem da aplicação – ambiente de validação |
| Azure Storage (PRODUÇÃO) | Hospedagem da aplicação – ambiente produtivo |
| Azure DevOps Pipelines (YAML) | Orquestração do CI/CD |
| Pipeline CI | Build e geração do artefato `.zip` |
| Pipeline CD | Distribuição do artefato entre os ambientes |

### Fluxo resumido
Commit → GitHub  
→ **Pipeline CI (Build)**  
→ geração de artefato `.zip` imutável  
→ **Pipeline CD (Release multi-stage)**  
→ TESTE → QA → (Aprovação manual) → PRODUÇÃO  
→ Deploy no **Azure Storage (Static Website)**  

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

| Projeto | Tecnologia de Deploy | Modelo |
|--------|----------------------|--------|
| Projeto 1 | Azure Static Web Apps | Deploy direto via GitHub Actions |
| Projeto 2 | Azure Storage + Azure DevOps | CI/CD multi-ambiente com governança |

O **Projeto 2** representa a evolução para um fluxo mais próximo de ambientes corporativos, com controle de promoção e segregação de ambientes.

---

## Links da Aplicação
TESTE → (URL)  
QA → (URL)  
PRODUÇÃO → (URL)


