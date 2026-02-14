# Weather App – CI/CD Multi-Environment com Azure DevOps

## Descrição
Evolução do projeto **Weather App – Azure Static Web Apps**, com foco na aplicação de práticas reais de **DevOps, automação de deploy e segregação de ambientes.**

A aplicação é uma web app estática desenvolvida em **HTML, CSS e JavaScript puro,** hospedada no **Azure Storage (Static Website)** e publicada por meio de um pipeline completo de **CI/CD no Azure DevOps.**

O projeto simula um cenário corporativo ao implementar:
- CI/CD profissional
- Separção de ambientes
- Aprovação manual em produção
- Infraestrutura Serveless no Azure
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

