### Desafio Go: Sistema de Temperatura por CEP com OpenTelemetry

Este projeto consiste em dois serviços em Go:

- **Serviço A**: Recebe um CEP via POST, valida o formato e encaminha para o Serviço B.
- **Serviço B**: Recebe um CEP válido, consulta a localização através do serviço ViaCEP, e consulta a temperatura atual através do serviço WeatherAPI. Retorna a temperatura em Celsius, Fahrenheit e Kelvin, juntamente com o nome da cidade.


### Instruções para Execução

1. **Construir as Imagens**: Na raiz do projeto, execute:

   ```
   docker-compose build
   ```

2. **Executar o Docker Compose**: Na raiz do projeto (onde está o arquivo `docker-compose.yml`), execute:

   ```
   docker-compose up
   ```


3. **Testar a Aplicação**: Após iniciar os serviços, você pode acessar:

- Para o serviço A:

   ```
   curl -X POST -H "Content-Type: application/json" -d '{"cep":"29902555"}' http://localhost:8080/cep
   ```
   
- Para o serviço B (substitua `CEP` por um código postal válido de 8 dígitos):
     ```
    curl -X GET "http://localhost:8081/weather?cep=29902555" -H "accept: application/json" 
     ```


4. **Testar o zipkin**:

- Abra o link no seu navegador:

   ```
   http://localhost:9411/zipkin/?lookback=15m&endTs=1716854339005&limit=10
   ```
<img width="1791" alt="image" src="https://github.com/AnaGFranco/goexpert-temperature-system/assets/55562874/c3756899-af33-4808-9d32-0718f60b5cbd">


