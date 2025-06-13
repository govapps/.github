# Deploy GovOneID
## Deploy
1. <a href="https://github.com/govapps/infra-template/actions/workflows/auth.yaml"> Criar tabelas no dynamodb </a>
2. <a href="https://github.com/govapps/infra-template/actions/workflows/gateway.yaml"> Criar o gateway </a>
3. <a href="https://github.com/govapps/valid-func/actions/workflows/install.yml"> Criar lambda de validar ( /validate ) </a>
4. <a href="https://github.com/govapps/auth-func/actions/workflows/install.yml"> Criar lambda de autenticar </a>
5. <a href="https://github.com/govapps/people-func/actions/workflows/install.yml"> Criar lambda de People </a>


### descobrir o que cada lambda faz e os endpoint
* item 3 precisa melhorar e criar o OPTIONS no endpoint, pois não está criando. <a href="https://github.com/govapps/infra-template/blob/main/aws/Function.yaml"> da linha 102 a 128 precisa ser melhorado </a>

### ver a documentação no postman 
