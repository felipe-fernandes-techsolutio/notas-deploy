# Deploy do frontend do Pantheon 

1. cd Pantheon/repositorios/pantheon-isp_frontend-angular
2. git pull origin pre-master
3. npm i *(se o repositório for novo ou se precisar instalar novas dependências)*
4. npx ng b --configuration=production
5. docker build -t frontend-angular .
6. cd ../pantheon-isp_geral-backend-devops/ && docker compose up -d frontend

## Observações

- O caminho do passo 1 pode variar de acordo com o servidor.
- Utilizar modo sudo (sudo su) antes do passo 2.
- Em caso de erro de autenticação ao realizar o pull (git solicitando usuário e senha), informar token de login do github:
    1. No github, ir em *settings* > *Developer settings* > *Personal access tokens* > *Tokens (classic)* > *Generate new token*.
    2. No terminal, informar nome de usuário (como no github) e token gerado (`ghp_123...`).
- Em caso de erro de build (passo 4), executar o passo 3. Se o erro ainda persistir:
    1. Remover *node_modules* e *package-lock.json* (`rm -fr node_modules package-lock.json`);
    2. Executar passo 3.