# elastic-stack-eh-muito-pratica
Projeto criado para exemplificação em dojo sobre a Stack Elastic para mostrar a simplicidade do uso da mesma para monitoramento de logs e de recursos de uma máquina/ambiente docker.

# Dependências
 - Docker
 - Docker Composer

# Subindo a stack
## Passo 1 
Acesse a pasta onde está o projeto e execute o seguinte comando:
```
$ docker-compose up -d
```
>O parâmetro `-d` serve para não "inutilizar" seu terminal, fazendo o serviço rodar em background

## Passo 2
Usar.

> Utilizando as configurações default dos serviços, toda o setup necessário está contido no arquivo `docker-compose.yml`.

# Executando Metricbeat
>Para instalação a própria Elastic disponibiliza um tutorial bem simples:
>https://www.elastic.co/guide/en/beats/metricbeat/current/setup-repositories.html

## Aplicar configurações
(Dentro da pasta `Beats`) Execute o seguinte comando para substituir o arquivo de configuração do Metricbeat instalado pelo presente neste projeto
```
$ sudo cp metricbeat.yml /etc/metricbeat/metricbeat.yml
```

## Gerar Dashboards Padrões
(Com o Kibana rodando) Execute o seguinte comando para que o Metricbeat crie alguns dashboards padrões dele no Kibana
```
$ metricbeat setup --dashboards
```

## Iniciar o Metricbeat
Basta executar:
```
$ sudo service metricbeat start
```

## Ativando monitoramento do Docker
```
$ sudo metricbeat modules enable docker
```

## Ativando monitoramento da máquina onde roda o Metricbeat
```
$ sudo metricbeat modules enable system
```

# Executando Filebeat
>Para instalação a própria Elastic disponibiliza um tutorial bem simples:
>https://www.elastic.co/guide/en/beats/filebeat/current/setup-repositories.html

## Aplicar configurações
(Dentro da pasta `Beats`) Execute o seguinte comando para substituir o arquivo de configuração do Filebeat instalado pelo presente neste projeto
```
$ sudo cp filebeat.yml /etc/filebeat/filebeat.yml
```

## Iniciar o Filebeat
Basta executar:
```
$ sudo service filebeat start
```