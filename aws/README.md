# Deploy GovOneID
## Install
1. <a href="https://github.com/govapps/infra-template/actions/workflows/auth.yaml"> Criar tabelas no dynamodb </a>
2. <a href="https://github.com/govapps/infra-template/actions/workflows/gateway.yaml"> Criar o gateway </a>
3. <a href="https://github.com/govapps/valid-func/actions/workflows/install.yml"> Criar lambda de validar ( /validate ) </a>
4. <a href="https://github.com/govapps/auth-func/actions/workflows/install.yml"> Criar lambda de autenticar ( /auth ) </a>
5. <a href="https://github.com/govapps/people-func/actions/workflows/install.yml"> Criar lambda de People ( /people ) </a>

## Deploy
1. <a href="https://github.com/govapps/valid-func/actions/workflows/deploy-dev.yml"> Deploy lambda de validar ( /validate ) </a>
2. <a href="https://github.com/govapps/auth-func/actions/workflows/deploy-dev.yml"> Deploy lambda de autenticar ( /auth ) </a>
3. <a href="https://github.com/govapps/people-func/actions/workflows/deploy-dev.yml"> Deploy lambda de People ( /people ) </a>

## Variáveis de ambiente
1. Lambda valid
   * app_url = ambiente-app_url
   * roles = ambiente-roles
   * SECRET_KEY = 
3. Lambda auth
   * app_url = ambiente-app_url
   * group_users = ambiente-group_users
   * groups = ambiente-groups
   * people = ambiente-people
   * projects = ambiente-projects
   * projects_user = ambiente-projects_user
   * roles = ambiente-roles
   * SECRET_KEY = 
4. Lambda people
   * people = ambiente-people

  
## Observações 
* item 3 precisa melhorar e criar o OPTIONS no endpoint, pois não está criando. <a href="https://github.com/govapps/infra-template/blob/main/aws/Function.yaml"> da linha 102 a 128 precisa ser melhorado </a>
* Bug nesse <a href="https://github.com/govapps/infra-template/blob/main/aws/Function.yaml"> .yaml </a>, não está gerando o optionsMethod de alguns endpoint.
* Tem colocar os layers nas functions **firebase-admin--jwt-layer**
* Tem que dar permissão de acesso as lambdas ao dynamodb

### ver a documentação no postman 

### editar as actions para colocar os defeault de cada lambda/endpoint

### popular o banco