# Deploy da interface web do Meu Provedor 

> Passar toda alteração pendente para a `main`.
> O build é realizado durante o docker build.

1. cd app-cliente/app-cliente-front
2. git pull origin main
3. docker build -t tech-app-cliente .
4. docker stop app-frontend && docker rm app-frontend
5. docker run -d -p 80:80 --restart=always --name app-frontend tech-app-cliente

## Observações

- Utilizar modo sudo (sudo su) antes do passo 2.
- Em caso de erro de autenticação ao realizar o pull (git solicitando usuário e senha), informar token de login do github:
    1. No github, ir em *settings* > *Developer settings* > *Personal access tokens* > *Tokens (classic)* > *Generate new token*.
    2. No terminal, informar nome de usuário (como no github) e token gerado (`ghp_123...`).
- Em caso de erro de build (passo 3):
    1. Remover *node_modules* e *package-lock.json* (`rm -fr node_modules package-lock.json`);
    2. Executar passo 3 novamente.