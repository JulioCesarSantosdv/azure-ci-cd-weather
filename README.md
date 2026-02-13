# Weather App – CI/CD Multi-Environment com Azure DevOps

## Descrição
Aplicação web estática desenvolvida com **HTML, CSS e JavaScript puro**, publicada em **Azure Storage (Static Website)** por meio de um pipeline completo de **CI/CD no Azure DevOps**.

Este projeto simula um cenário corporativo com:

- geração de artefato imutável no **Pipeline CI (Build)**
- promoção controlada entre ambientes no **Pipeline CD (Release multi-stage)**
- separação de ambientes (**TESTE → QA → PRODUÇÃO**)
- aprovação manual em produção via **Azure DevOps Environments**
- autenticação segura com **Service Connection + RBAC**

O objetivo é demonstrar práticas reais de engenharia DevOps com **governança, rastreabilidade e controle de acesso**, sem utilização de chaves de storage.

👉 Documentação do Projeto  
👉 Diagrama de Arquitetura  
👉 Slides  

---

## Arquitetura
image

### Fluxo resumido
Commit → GitHub  
→ **Pipeline CI (Build)**  
→ geração de artefato `.zip` imutável  
→ **Pipeline CD (Release multi-stage)**  
→ TESTE → QA → (Aprovação manual) → PRODUÇÃO  
→ Deploy em **Azure Storage (Static Website)**  

A aplicação é hospedada diretamente no Storage; não há backend nem containers em produção.

---

## Ambientes

| Ambiente | Storage Account |
|----------|------------------|
| TESTE    | weatherappteste |
| QA       | weatherappqa |
| PRODUÇÃO | weatherappproduction |

Cada ambiente possui uma Storage Account dedicada, garantindo **isolamento e redução de risco**.

---

## Pipelines

### Pipeline CI (Build)
Responsável por:

- obter o código do repositório  
- empacotar os arquivos da aplicação em um `.zip`  
- publicar o artefato no Azure DevOps  

#### Características do artefato
- imutável  
- versionado  
- reutilizado em todos os ambientes  

---

### Pipeline CD (Release multi-stage)
Executado automaticamente após o sucesso do CI.

Em cada stage:

- download do artefato  
- extração do `.zip`  
- publicação no container `$web` da Storage correspondente  

#### Ordem de promoção
TESTE → QA → PRODUÇÃO  

O deploy em **PRODUÇÃO** ocorre somente após **aprovação manual**.

---

## Governança de Produção
Implementada via **Azure DevOps Environment** com:

- aprovador obrigatório  
- bloqueio de execução até validação  
- auditoria de liberações  

A regra de aprovação é configurada na plataforma (**fora do YAML**), garantindo separação entre:

- definição técnica do pipeline  
- controle operacional de releases  

---

## Segurança
Autenticação realizada por **Service Connection (Service Principal)** com:

- escopo no Resource Group `rg-weather-app-cicd`  
- role `Storage Blob Data Contributor`  

O pipeline **não utiliza Account Keys**, seguindo o princípio de **privilégio mínimo**.

---

## Infraestrutura Azure
- **Resource Group:** rg-weather-app-cicd  
- **Tipo:** StorageV2  
- **Static Website:** habilitado  
- **Container:** `$web`  
- **Região:** East US  

Arquitetura de **baixo custo** e **alta disponibilidade** para aplicações estáticas.

---

## Conceitos Azure e DevOps aplicados
- CI/CD com Azure DevOps  
- Artefato imutável  
- Promoção entre ambientes  
- Ambientes isolados  
- RBAC e Service Connections  
- Aprovação manual em produção  
- Deploy idempotente  
- Agentes efêmeros de pipeline  

---

## Limitações Encontradas
O plano gratuito do Azure DevOps limitou o paralelismo de agentes.

### Solução
- associação da organização a uma assinatura **Azure Pay-As-You-Go**  
- liberação do paralelismo  
- execução do pipeline multi-stage **sem custo**  

---

## Resultado
✔️ Deploy automático em TESTE  
✔️ Deploy automático em QA  
✔️ Deploy controlado com aprovação manual em PRODUÇÃO  
✔️ Rastreabilidade completa de build e release  

---

## Relação com o Projeto 1

| Projeto | Tecnologia de Deploy | Modelo |
|--------|----------------------|--------|
| Projeto 1 | Azure Static Web Apps | Deploy direto via GitHub Actions |
| Projeto 2 | Azure Storage + Azure DevOps | CI/CD multi-ambiente com governança |

O **Projeto 2** representa a evolução para um fluxo mais próximo de ambientes corporativos.

---

## Link da Aplicação
TESTE → (URL)  
QA → (URL)  
PRODUÇÃO → (URL)  

---

