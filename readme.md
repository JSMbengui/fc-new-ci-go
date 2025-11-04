Integração Continua: é o processo de integrar modificações do codebase de forma contínua e atuomatizada, evitando assim erros humanos de verificaçao, garantido mais agilidade e segurança no processo de desenvolvimento de um software

000. Principais processos de CI

1. Execução de testes
2. Linter
3. Verificações de qualidade de código
4. Geração de artefatos prontos para o processo de deploy
5. Identificação da próxima versão a ser gerada no software
6. Geração de tags e releases

001. Status check
É a garantia de que uma Pull Rquest não poderá ser mergeada ao repositório sem antes ter passado pelo processo de CI ou memso no processo de Code Review

002. Ferramentas populares
1. Jenkins
2. Github Actions
3. Circle CI
4. AWS Code Build
5. Azure DevOps
6. Google Cloud Build
7. Github Pipelines / CI

003. Github Actions
Automate your workflow from idea to production

É um automatizador de workflow de desenvolvimento de software. Ele utiliza os principais eventos gerados pelo GitHub para que possamos executar tarefas dos mais variados tipos, incuindo procesos de CI.

Dinâmica

1. workflow  -->   
  são conjunto de processos definidos por você. Ex.: fazer o build + rodar os testes da aplicação
  é possível ter mais do que um workflow por repositório
  definidos em arquivos .yml em .github/workflows
  possui um ou mais Jobs
  é iniciado baseado em eventos do github ou através de agendamento

2. Eventos  -->  Filtros             --> Ambiente                --> Acções
   on: push -->  branches: master        runs-on: ubuntu         steps: 
                                                                        -uses: actions/run-composer
                                                                        - run: npm run prod

Actions: é a acção que de facto será executada em um dos Steps de um Job em um Workflow. Ela pode ser criada do zero ou ser reutilizada de actions pre-existentes

Action pode ser desenvolvida:
  1. Javascript
  2. Docker Image

000. 