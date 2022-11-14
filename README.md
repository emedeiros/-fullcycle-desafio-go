# FullCycle 3.0
## Desafio GO do módulo Docker

Esse projeto é o exercício proposto como desafio do módulo Docker (curso Docker), do curso FullCycle 3.0
Ref: https://fullcycle.com.br/

## Descrição do desafio:
- Gerar uma imagem Go, usando Go Lang.
- Quando essa imagem Go rodar no container, deve ser retornado para o usuário final a seguinte mensagem: “FullCycle Rocks !”. 
- A imagem GO Lang não pode ter mais do que 2MB.


## Executar a imagem desde o DockerHub
Você pode rodar a imagem utilizando o seguinte comando docker no Terminal:
```sh
docker run estevaomc/codeeducation:latest
```

## Gerar a imagem fazendo o build com docker-compose
Na raiz do projeto, você encontrará o arquivo docker-compose.yaml.
Para gerar a imagem com o docker-compose, basta executar o seguinte comando no Terminal
```sh
docker-compose up
```

ou então
```sh
docker-compose up --build
```

## Gerar a imagem fazendo o build sem o docker-compose
```sh
cd go
docker build -t <nome usuário no dockerhub>/codeeducation:latest .
docker run estevaomc/codeeducation:latest
```

## Código Fonte
Dentro da pasta go, há dois arquivos, hola.go e Dockerfile

O arquivo hola.go contém o código fonte da aplicação GO, que irá imprimir na tela o texto "FullCycle Rocks !"

O arquivo Dockerfile, realiza o build da imagem em 2 etapas. 
Na primeira etapa, é utilizada como imagem base a imagem golang versao 1.17 e sua funçao principal é gerar o arquivo binário da app GO, utilizando o fonte do arquivo hola.go .

Na segunda etapa de building, uma imagem scratch foi utilizada para cumprir o objetivo de gerar uma imagem final que tenha menos de 2MB, copiando o arquigo binário executavel da app GO, e executando essa app automaticamente quando a imagem é rodada no container.


