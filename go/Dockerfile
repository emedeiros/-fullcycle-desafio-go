#----- multistage building | stage 01 ------------------
# Imagem base
FROM golang:1.17 as buildStage01

WORKDIR /go/src/app


# Copy everything from the current directory to the PWD (Present Working Directory) inside the container
# Copiando todo o conteudo do diretorio local, para o diretorio definido no WORKDIR :  /go/src/app
COPY . .

# Comandos GO para gerar o binario que irá imprimir a mansagem "FullCycle Rocks" ao usuario
# vou nomear esse arquivo binario como fc_rocks e o codigo fonte esta no arquivo hola.go (Hola, de olá em espanhol. 
# Por que hola.go? Nao quis utilizar nomes tipicos como main.go, app.go, etc, porque é a primeira vez que trabalho com 
# go e queria entender bem o que estava ocorrendo e utilizei esse nome de arquivo.
RUN go mod init
RUN go build -o /fc_rocks

# O ENTRYPOINT a continuaçao foi utilizada somente na etapa de teste do dockerfile no inicio do exercicio, 
# uma vez realizado o test e dando inicio ao processo de multistage building, esse entrypoint é movido ao final 
# do segundo estagio
# ENTRYPOINT [ "/fc_rocks"]; 

########################################################################################################################
#----- multistage building | stage 02 ------------------
# Image Scratch foi a imagem mais leve que encontrei
# Ref: https://blog.devgenius.io/hello-world-the-smallest-docker-image-d71fe91c5aa1
FROM scratch

# Diretorio de Trahalho
WORKDIR /

# Compiando o binario gerado pelo Go que roda o print da mensagem "FullCycle Rocks !" do building do Stage 1
COPY --from=buildStage01 /fc_rocks /fc_rocks
# USER nonroot:nonroot

# Entrypoint é a execuçao do binario que imprime na tela "FullCycle Rocks !"
ENTRYPOINT [ "/fc_rocks"]; 
