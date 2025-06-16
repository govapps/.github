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
1. **Lambda valid**
   * app_url = ambiente-app_url
   * roles = ambiente-roles
   * SECRET_KEY = 
3. **Lambda auth**
   * app_url = ambiente-app_url
   * group_users = ambiente-group_users
   * groups = ambiente-groups
   * people = ambiente-people
   * projects = ambiente-projects
   * projects_user = ambiente-projects_user
   * roles = ambiente-roles
   * SECRET_KEY = 
4. **Lambda people**
   * people = ambiente-people

**OBS:** a variável *SECRET_KEY* é a key do jwt que está na API principal da aplicação. Pode estar com o nome *API_SECRET_KEY*

## DynamoDB
Precisa popular o banco com as informações necessárias.

### Tipagem das tabelas:
1. **app_url**:
   * url: String
   * app: String
   * pid: String
2. **groups**:
   * gid: String
   * name: String
   * pid: String
   * roles: String set
   * status: Boolean
3. **group_users**:
   * uid: String
   * gid: String
   * pid: String
   * status: Boolean
   * valid: Boolean
4. **people**:
   * uid: String
5. **projects**:
   * pid: String
   * apps: String set
   * client: String
   * status: Boolean
6. **projects_user**:
   * uid: String
   * pid: String
   * groups: String set
   * status: Boolean
7. **roles**:
   * rid: String
   * name: String
   * pid: String
   * statement: String

## Endpoints
Os endpoints de cada lambda estão no postman na pasta **Aws** com seus devidos parâmetros e body

## Observações 
* item 3 precisa melhorar e criar o OPTIONS no endpoint, pois não está criando. <a href="https://github.com/govapps/infra-template/blob/main/aws/Function.yaml"> da linha 102 a 128 precisa ser melhorado </a>
* Bug nesse <a href="https://github.com/govapps/infra-template/blob/main/aws/Function.yaml"> .yaml </a>, não está gerando o optionsMethod de alguns endpoint.
* Tem colocar um layer na auth-func para funcionar: **firebase-admin--jwt-layer**
* Tem que dar permissão de acesso as lambdas ao dynamodb