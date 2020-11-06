FROM golang:1.15.3

WORKDIR /go/src/fullcycle

# Foi necessário incluir o arquivo "go.mod"
COPY . .

###### Não foi possível copiar o arquivo do diretório pai.
# ERROR: Service 'microservice-b' failed to build : COPY failed: Forbidden path outside the build context: ../go.mod ()
# COPY ../go.mod .
# RUN go mod download

###### Não foi possível apenas instalar as dependências, assim como foi feito nos outros microserviços.
# # command-line-arguments
# ./b.go:27:29: multiple-value uuid.NewV4() in single-value context
# ERROR: Service 'microservice-b' failed to build : The command '/bin/sh -c GOOS=linux go build b.go' returned a non-zero code: 2
###### Install go dependencies
# RUN go get github.com/joho/godotenv && \
#   go get github.com/satori/go.uuid && \
#   go get github.com/streadway/amqp && \
#   go get github.com/wesleywillians/go-rabbitmq/queue

# Por algum motivo que desconheço, diferente do que foi feito nos outros microserviços, foi necessário indicar o arquivo a ser utilizado para o build e o entrypoint
RUN GOOS=linux go build b.go

ENTRYPOINT [ "./b" ]
