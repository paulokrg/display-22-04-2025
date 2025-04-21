# 🌆 SmartCities Project - DevOps CI/CD Implementation (.NET)

Este projeto é parte de uma atividade avaliativa do capítulo 6 da disciplina de Application Lifecycle Management, com foco na aplicação de práticas modernas de DevOps, incluindo CI/CD, Docker e provisionamento em nuvem via GitHub e Azure.

## 📌 Descrição Geral

O projeto **SmartCities** foi desenvolvido com base no conceito de Cidades Inteligentes, abordando soluções tecnológicas sustentáveis para ambientes urbanos. O foco principal da atividade foi implementar práticas de DevOps no ciclo de vida da aplicação .NET.

## 🐳 Como Rodar o Projeto Localmente com Docker ou Docker Compose

### Pré-requisitos

- Docker instalado (Docker Desktop ou CLI)
- Docker Compose (separado ou embutido no Docker Desktop)

### Passos

1. Clone o repositório:

```bash
git clone https://github.com/seu-usuario/smartcities-devops.git
cd smartcities-devops
```

2. Build e execução via Docker:

```bash
docker build -t smartcities-app .
docker run -d -p 5000:80 smartcities-app
```

3. Ou utilizando o Docker Compose (caso tenha o `docker-compose.yml` configurado):

```bash
docker-compose up --build
```

O projeto estará acessível em `http://localhost:5000`.

## 🔁 Pipeline CI/CD

O pipeline de integração e entrega contínua foi implementado utilizando **GitHub Actions** e **Azure App Service**. O processo inclui:

- Versionamento automático com base no repositório GitHub.
- Build contínuo via Azure DevOps com base na branch principal.
- Deploy automatizado em ambiente de produção assim que o build é finalizado com sucesso.
- Monitoramento de logs e histórico de builds pelo portal do Azure.

### Etapas de CI/CD

1. Push de código no GitHub dispara pipeline.
2. Azure App Service consome o repositório GitHub.
3. Configuração automática com:
   - Stack: .NET
   - Região: South America (Brazil)
   - Acesso público habilitado
4. Deploy contínuo sem necessidade de interação manual.

## 🚀 Executando Build e Deployment

### Ambiente de Staging

> Caso tenha configurado um ambiente de staging no Azure, use o slot de staging do App Service para fazer testes antes do deploy final:

```bash
az webapp deployment slot create --name smartcities-app --resource-group rg-smartcities --slot staging
```

### Ambiente de Produção

O deploy ocorre automaticamente após o push na branch principal. Caso deseje forçar um deploy manual:

```bash
az webapp deployment source sync --name smartcities-app --resource-group rg-smartcities
```

## 🧰 Tecnologias Utilizadas

- .NET 6+
- Docker
- GitHub Actions
- Azure App Service
- Dockerfile
- Azure CLI

## 💻 Requisitos do Sistema

- .NET SDK 6.0+
- Docker
- Conta no GitHub
- Conta no Azure (com App Service ativo)

## 👨‍💻 Autores / Contribuidores

- **Gabriel Araújo Ferraz de Melo**  
  **Jonas Alves Moreira**  
  **Diego Brasileiro Vilela Dias**  
   **Paulo Cauê Krüger Costa**  
   **Gabriel Paulucci**  
  Estudantes de Análise e Desenvolvimento de Sistemas - FIAP  
  GitHub: [https://github.com/DiegoBr7/display-22-04-2025/tree/main](https://github.com/DiegoBr7/display-22-04-2025/tree/main)

## 📄 Outros Detalhes

- O projeto já possui um `Dockerfile` pronto para build e execução em containers.
- Todos os prints do processo de CI/CD, desde a criação do repositório até o deploy, estão documentados no arquivo PDF incluso na entrega.
- Aplicação acessível via Azure com monitoramento de desempenho e logs disponíveis no portal.

---
