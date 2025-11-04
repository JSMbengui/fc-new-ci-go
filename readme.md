# Integração Contínua (CI)

A **Integração Contínua** é o processo de integrar modificações no *codebase* de forma **contínua e automatizada**. Isso evita erros humanos na verificação, garantindo mais **agilidade** e **segurança** no desenvolvimento de software.

---

## Principais Processos de CI

1. **Execução de testes**  
   Rodagem automática de testes unitários, de integração e *end-to-end*.
2. **Linter**  
   Verificação de padrões de codificação e detecção de erros de sintaxe.
3. **Verificações de qualidade de código**  
   Análise estática para identificar vulnerabilidades e métricas de qualidade.
4. **Geração de artefatos**  
   Criação de builds prontos para o processo de *deploy*.
5. **Identificação da próxima versão**  
   Determinação automática da versão semântica do software.
6. **Geração de tags e releases**  
   Criação de tags no Git e publicação de *releases*.

---

## Status Check

É a garantia de que uma **Pull Request** **não poderá ser mergeada** no repositório sem antes passar pelo processo de **CI** ou pelo **Code Review**.

> Isso bloqueia merges até que todos os *checks* sejam aprovados.

---

## Ferramentas Populares

| Ferramenta         | Descrição |
|--------------------|---------|
| **Jenkins**        | Servidor de automação *open-source*, altamente customizável. |
| **GitHub Actions** | Integração nativa com GitHub para *workflows* automatizados. |
| **CircleCI**       | Plataforma de CI/CD rápida e escalável. |
| **AWS CodeBuild**  | Serviço gerenciado da AWS para *builds* e testes. |
| **Azure DevOps**   | Suíte completa de DevOps da Microsoft. |
| **Google Cloud Build** | Ferramenta *serverless* para *builds* na nuvem do Google. |
| **GitHub Pipelines / CI** | Extensão do GitHub Actions para pipelines simplificados. |

---

## GitHub Actions

> **Automate your workflow from idea to production**

O **GitHub Actions** é um automatizador de *workflows* para o desenvolvimento de software. Ele utiliza eventos gerados pelo GitHub para executar tarefas variadas, incluindo processos de **CI/CD**.

---

### Dinâmica

#### 1. **Workflow**
- Conjunto de processos definidos por você (ex.: *build* + testes).
- Pode haver **múltiplos workflows** por repositório.
- Definidos em arquivos `.yml` na pasta:  .github/workflows/
- Possui um ou mais **Jobs**.
- Iniciado por:
- Eventos do GitHub (`push`, `pull_request`, etc.)
- Agendamento (`cron`)

#### 2. **Eventos → Filtros → Ambiente → Ações**

```yaml
on:
push:
  branches: [ main ]

jobs:
build-and-test:
  runs-on: ubuntu-latest
  steps:
    - uses: actions/checkout@v3
    
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
        
    - name: Install dependencies
      run: npm ci
      
    - name: Build
      run: npm run build
      
    - name: Run tests
      run: npm test