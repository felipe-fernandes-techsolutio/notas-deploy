# Deploy webpages techsolutio

O processo de deploy das três landing pages é idêntico, alterando apenas o nome do container e imagem:

- https://techsolutio.com/ 	> `techsolutio-website`
- https://aiquanta.com.br/ 	> `aiquanta-website`
- https://cxsolutio.com/ 	> `cxsolutio-website`

### Local    
Gerar arquivo *.tar* localmente:
1.  `docker build -t aiquanta-website .`
2.  `docker save -o aiquanta-website.tar aiquanta-website`

### Servidor    
1. *Copiar arquivo .tar para o servidor*
2. *Parar container*
	- `docker stop techsolutio-website && docker rm techsolutio-website && docker rmi techsolutio-website`
	- `docker stop aiquanta-website && docker rm aiquanta-website && docker rmi aiquanta-website`
	- `docker stop cxsolutio-website && docker rm cxsolutio-website && docker rmi cxsolutio-website`
	
3. *Extrair imagem*
	- ` docker load -i techsolutio-website.tar`
	- ` docker load -i aiquanta-website.tar`
	- ` docker load -i cxsolutio-website.tar`

4. *Subir container* 
	- *tech*: 
		`docker run -d -p 81:80 --name techsolutio-website techsolutio-website:latest`
	- *aiquanta*: 
		`docker run -d -p 82:80 --name aiquanta-website aiquanta-website:latest`
	- *cxsolutio*: 
		`docker run -d -p 83:80 --name cxsolutio-website cxsolutio-website:latest`