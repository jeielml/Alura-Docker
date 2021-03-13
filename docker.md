# Introdução ao Docker


* Imagens do Docker possuem um sistema de arquivos em camadas (Layered File System) e os benefícios dessa abordagem principalmente para o download de novas imagens.
* Imagens são Read-Only sempre (apenas para leitura)
* Containers representam uma instância de uma imagem
* Como imagens são Read-Only os containers criam nova camada (layer) para guardar as alterações
* O comando Docker run e as possibilidades de execução de um container


* Comandos básicos do Docker para podermos baixar imagens e interagir com o container.

    `docker ps` - exibe todos os containers em execução no momento.

    `docker ps -a` - exibe todos os containers, independentemente de estarem em execução ou não.

    `docker run -it NOME_DA_IMAGEM` - conecta o terminal que estamos utilizando com o do container.

    `docker start ID_CONTAINER` - inicia o container com id em questão.

    `docker stop ID_CONTAINER` - interrompe o container com id em questão.

    `docker start -a -i ID_CONTAINER` - inicia o container com id em questão e integra os terminais, além de permitir interação entre ambos.

    `docker rm ID_CONTAINER` - remove o container com id em questão.

    `docker container prune` - remove todos os containers que estão parados.

    `docker rmi NOME_DA_IMAGEM` - remove a imagem passada como parâmetro.

    `docker run -d -P --name NOME dockersamples/static-site` - ao executar, dá um nome ao container.

    `docker run -d -p 12345:80 dockersamples/static-site` - define uma porta específica para ser atribuída à porta 80 do container, neste `caso 12345.

    `docker run -d -P -e AUTHOR="Fulano" dockersamples/static-site` - define uma variável de ambiente AUTHOR com o valor Fulano no container criado.


----

# Trabalhando com Volumes

* Criando o volume "/var/www":

    `docker run -v "/var/www" ubuntu`

    `docker ps -a` > bca3ff41a484   ubuntu    "/bin/bash"   17 seconds ago   Exited (0) 15 seconds ago             loving_ishizaka

    `docker inspect bca` >     
    ```ssh
    [
        {
            "Id": "bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e",
            "Created": "2021-03-13T12:17:12.961541371Z",
            "Path": "/bin/bash",
            "Args": [],
            "State": {
                "Status": "exited",
                "Running": false,
                "Paused": false,
                "Restarting": false,
                "OOMKilled": false,
                "Dead": false,
                "Pid": 0,
                "ExitCode": 0,
                "Error": "",
                "StartedAt": "2021-03-13T12:17:13.395593684Z",
                "FinishedAt": "2021-03-13T12:17:13.414919738Z"
            },
            "Image": "sha256:4dd97cefde62cf2d6bcfd8f2c0300a24fbcddbe0ebcd577cc8b420c29106869a",
            "ResolvConfPath": "/var/lib/docker/containers/bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e/resolv.conf",
            "HostnamePath": "/var/lib/docker/containers/bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e/hostname",
            "HostsPath": "/var/lib/docker/containers/bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e/hosts",
            "LogPath": "/var/lib/docker/containers/bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e/bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e-json.log",
            "Name": "/loving_ishizaka",
            "RestartCount": 0,
            "Driver": "overlay2",
            "Platform": "linux",
            "MountLabel": "",
            "ProcessLabel": "",
            "AppArmorProfile": "docker-default",
            "ExecIDs": null,
            "HostConfig": {
                "Binds": null,
                "ContainerIDFile": "",
                "LogConfig": {
                    "Type": "json-file",
                    "Config": {}
                },
                "NetworkMode": "default",
                "PortBindings": {},
                "RestartPolicy": {
                    "Name": "no",
                    "MaximumRetryCount": 0
                },
                "AutoRemove": false,
                "VolumeDriver": "",
                "VolumesFrom": null,
                "CapAdd": null,
                "CapDrop": null,
                "CgroupnsMode": "host",
                "Dns": [],
                "DnsOptions": [],
                "DnsSearch": [],
                "ExtraHosts": null,
                "GroupAdd": null,
                "IpcMode": "private",
                "Cgroup": "",
                "Links": null,
                "OomScoreAdj": 0,
                "PidMode": "",
                "Privileged": false,
                "PublishAllPorts": false,
                "ReadonlyRootfs": false,
                "SecurityOpt": null,
                "UTSMode":    {
            "Id": "bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e",
            "Created": "2021-03-13T12:17:12.961541371Z",
            "Path": "/bin/bash",
            "Args": [],
            "State": {
                "Status": "exited",
                "Running": false,
                "Paused": false,
                "Restarting": false,
                "OOMKilled": false,
                "Dead": false,
                "Pid": 0,
                "ExitCode": 0,
                "Error": "",
                "StartedAt": "2021-03-13T12:17:13.395593684Z",
                "FinishedAt": "2021-03-13T12:17:13.414919738Z"
            },
            "Image": "sha256:4dd97cefde62cf2d6bcfd8f2c0300a24fbcddbe0ebcd577cc8b420c29106869a",
            "ResolvConfPath": "/var/lib/docker/containers/bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e/resolv.conf",
            "HostnamePath": "/var/lib/docker/containers/bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e/hostname",
            "HostsPath": "/var/lib/docker/containers/bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e/hosts",
            "LogPath": "/var/lib/docker/containers/bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e/bca3ff41a484e0fe0110ff06eb3b897c16187047e104c5095295b79e3055934e-json.log",
            "Name": "/loving_ishizaka",
            "RestartCount": 0,
            "Driver": "overlay2",
            "Platform": "linux",
            "MountLabel": "",
            "ProcessLabel": "",
            "AppArmorProfile": "docker-default",
            "ExecIDs": null,
            "HostConfig": {
                "Binds": null,
                "ContainerIDFile": "",
                "LogConfig": {
                    "Type": "json-file",
                    "Config": {}
                },
                "NetworkMode": "default",
                "PortBindings": {},
                "RestartPolicy": {
                    "Name": "no",
                    "MaximumRetryCount": 0
                },
                "AutoRemove": false,
                "VolumeDriver": "",
                "VolumesFrom": null,
                "CapAdd": null,
                "CapDrop": null,
                "CgroupnsMode": "host",
                "Dns": [],
                "DnsOptions": [],
                "DnsSearch": [],
                "ExtraHosts": null,
                "GroupAdd": null,
                "IpcMode": "private",
                "Cgroup": "",
                "Links": null,
                "OomScoreAdj": 0,
                "PidMode": "",
                "Privileged": false,
                "PublishAllPorts": false,
                "ReadonlyRootfs": false,
                "SecurityOpt": null,
                "UTSMode": "",
                "UsernsMode": "",
                "ShmSize": 67108864,
                "Runtime": "runc",
                "ConsoleSize": [
                    0,
                    0
                ],
                "Isolation": "",
                "CpuShares": 0,
                "Memory": 0,
                "NanoCpus": 0,
                "CgroupParent": "",
                "BlkioWeight": 0,
                "BlkioWeightDevice": [],
                "BlkioDeviceReadBps": null,
                "BlkioDeviceWriteBps": null,
                "BlkioDeviceReadIOps": null,
                "BlkioDeviceWriteIOps": null,
                "CpuPeriod": 0,
                "CpuQuota": 0,
                "CpuRealtimePeriod": 0,
                "CpuRealtimeRuntime": 0,
                "CpusetCpus": "",
                "CpusetMems": "",
                "Devices": [],
                "DeviceCgroupRules": null,
                "DeviceRequests": null,
                "KernelMemory": 0,
                "KernelMemoryTCP": 0,
                "MemoryReservation": 0,
                "MemorySwap": 0,
                "MemorySwappiness": null,
                "OomKillDisable": false,
                "PidsLimit": null,
                "Ulimits": null,
                "CpuCount": 0,
                "CpuPercent": 0,
                "IOMaximumIOps": 0,
                "IOMaximumBandwidth": 0,
                "MaskedPaths": [
                    "/proc/asound",
                    "/proc/acpi",
                    "/proc/kcore",
                    "/proc/keys",
                    "/proc/latency_stats",
                    "/proc/timer_list",
                    "/proc/timer_stats",
                    "/proc/sched_debug",
                    "/proc/scsi",
                    "/sys/firmware"
                ],
                "ReadonlyPaths": [
                    "/proc/bus",
                    "/proc/fs",
                    "/proc/irq",
                    "/proc/sys",
                    "/proc/sysrq-trigger"
                ]
            },
            "GraphDriver": {
                "Data": {
                    "LowerDir": "/var/lib/docker/overlay2/71af21989de0abb9c1f57aa79c0a67d009d7e60e356f6776b709aa26da3e57f7-init/diff:/var/lib/docker/overlay2/3ad2fc7c2f406d3ff29a5aec77f906243c47eb9b1a693dd98855dfd6ac0af683/diff:/var/lib/docker/overlay2/b65f5d67459acd814836d8d6c1f32785dbe6c5f38c54e8cfdf42eb9fa4938b58/diff:/var/lib/docker/overlay2/03075b4ee52b673a8bd77c1f9670db272d14cb1d8794ec66d61673a198905a59/diff",
                    "MergedDir": "/var/lib/docker/overlay2/71af21989de0abb9c1f57aa79c0a67d009d7e60e356f6776b709aa26da3e57f7/merged",
                    "UpperDir": "/var/lib/docker/overlay2/71af21989de0abb9c1f57aa79c0a67d009d7e60e356f6776b709aa26da3e57f7/diff",
                    "WorkDir": "/var/lib/docker/overlay2/71af21989de0abb9c1f57aa79c0a67d009d7e60e356f6776b709aa26da3e57f7/work"
                },
                "Name": "overlay2"
            },
            "Mounts": [
                {
                    "Type": "volume",
                    "Name": "6205058dbc27147f53bebb4abec5961367e2f021b1aabf81980aba1c0a620772",
                    "Source": "/var/lib/docker/volumes/6205058dbc27147f53bebb4abec5961367e2f021b1aabf81980aba1c0a620772/_data",
                    "Destination": "/var/www",
                    "Driver": "local",
                    "Mode": "",
                    "RW": true,
                    "Propagation": ""
                }
            ],
            "Config": {
                "Hostname": "bca3ff41a484",
                "Domainname": "",
                "User": "",
                "AttachStdin": false,
                "AttachStdout": true,
                "AttachStderr": true,
                "Tty": false,
                "OpenStdin": false,
                "StdinOnce": false,
                "Env": [
                    "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
                ],
                "Cmd": [
                    "/bin/bash"
                ],
                "Image": "ubuntu",
                "Volumes": {
                    "/var/www": {}
                },
                "WorkingDir": "",
                "Entrypoint": null,
                "OnBuild": null,
                "Labels": {}
            },
            "NetworkSettings": {
                "Bridge": "",
                "SandboxID": "d4b14f5b49a7d2781ef99426c1d4f2818ba981a1129cf72e89c117a8f533dc07",
                "HairpinMode": false,
                "LinkLocalIPv6Address": "",
                "LinkLocalIPv6PrefixLen": 0,
                "Ports": {},
                "SandboxKey": "/var/run/docker/netns/d4b14f5b49a7",
                "SecondaryIPAddresses": null,
                "SecondaryIPv6Addresses": null,
                "EndpointID": "",
                "Gateway": "",
                "GlobalIPv6Address": "",
                "GlobalIPv6PrefixLen": 0,
                "IPAddress": "",
                "IPPrefixLen": 0,
                "IPv6Gateway": "",
                "MacAddress": "",
                "Networks": {
                    "bridge": {
                        "IPAMConfig": null,
                        "Links": null,
                        "Aliases": null,
                        "NetworkID": "076acb80b091ccbe5cf71d6aa9b94ce83a0921ba8c2308cfd89770d8052184b4",
                        "EndpointID": "",
                        "Gateway": "",
                        "IPAddress": "",
                        "IPPrefixLen": 0,
                        "IPv6Gateway": "",
                        "GlobalIPv6Address": "",
                        "GlobalIPv6PrefixLen": 0,
                        "MacAddress": "",
                        "DriverOpts": null
                    }
                }
            }
        }
    ] "",
                "UsernsMode": "",
                "ShmSize": 67108864,
                "Runtime": "runc",
                "ConsoleSize": [
                    0,
                    0
                ],
                "Isolation": "",
                "CpuShares": 0,
                "Memory": 0,
                "NanoCpus": 0,
                "CgroupParent": "",
                "BlkioWeight": 0,
                "BlkioWeightDevice": [],
                "BlkioDeviceReadBps": null,
                "BlkioDeviceWriteBps": null,
                "BlkioDeviceReadIOps": null,
                "BlkioDeviceWriteIOps": null,
                "CpuPeriod": 0,
                "CpuQuota": 0,
                "CpuRealtimePeriod": 0,
                "CpuRealtimeRuntime": 0,
                "CpusetCpus": "",
                "CpusetMems": "",
                "Devices": [],
                "DeviceCgroupRules": null,
                "DeviceRequests": null,
                "KernelMemory": 0,
                "KernelMemoryTCP": 0,
                "MemoryReservation": 0,
                "MemorySwap": 0,
                "MemorySwappiness": null,
                "OomKillDisable": false,
                "PidsLimit": null,
                "Ulimits": null,
                "CpuCount": 0,
                "CpuPercent": 0,
                "IOMaximumIOps": 0,
                "IOMaximumBandwidth": 0,
                "MaskedPaths": [
                    "/proc/asound",
                    "/proc/acpi",
                    "/proc/kcore",
                    "/proc/keys",
                    "/proc/latency_stats",
                    "/proc/timer_list",
                    "/proc/timer_stats",
                    "/proc/sched_debug",
                    "/proc/scsi",
                    "/sys/firmware"
                ],
                "ReadonlyPaths": [
                    "/proc/bus",
                    "/proc/fs",
                    "/proc/irq",
                    "/proc/sys",
                    "/proc/sysrq-trigger"
                ]
            },
            "GraphDriver": {
                "Data": {
                    "LowerDir": "/var/lib/docker/overlay2/71af21989de0abb9c1f57aa79c0a67d009d7e60e356f6776b709aa26da3e57f7-init/diff:/var/lib/docker/overlay2/3ad2fc7c2f406d3ff29a5aec77f906243c47eb9b1a693dd98855dfd6ac0af683/diff:/var/lib/docker/overlay2/b65f5d67459acd814836d8d6c1f32785dbe6c5f38c54e8cfdf42eb9fa4938b58/diff:/var/lib/docker/overlay2/03075b4ee52b673a8bd77c1f9670db272d14cb1d8794ec66d61673a198905a59/diff",
                    "MergedDir": "/var/lib/docker/overlay2/71af21989de0abb9c1f57aa79c0a67d009d7e60e356f6776b709aa26da3e57f7/merged",
                    "UpperDir": "/var/lib/docker/overlay2/71af21989de0abb9c1f57aa79c0a67d009d7e60e356f6776b709aa26da3e57f7/diff",
                    "WorkDir": "/var/lib/docker/overlay2/71af21989de0abb9c1f57aa79c0a67d009d7e60e356f6776b709aa26da3e57f7/work"
                },
                "Name": "overlay2"
            },
            "Mounts": [
                {
                    "Type": "volume",
                    "Name": "6205058dbc27147f53bebb4abec5961367e2f021b1aabf81980aba1c0a620772",
                    "Source": "/var/lib/docker/volumes/6205058dbc27147f53bebb4abec5961367e2f021b1aabf81980aba1c0a620772/_data",
                    "Destination": "/var/www",
                    "Driver": "local",
                    "Mode": "",
                    "RW": true,
                    "Propagation": ""
                }
            ],
            "Config": {
                "Hostname": "bca3ff41a484",
                "Domainname": "",
                "User": "",
                "AttachStdin": false,
                "AttachStdout": true,
                "AttachStderr": true,
                "Tty": false,
                "OpenStdin": false,
                "StdinOnce": false,
                "Env": [
                    "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
                ],
                "Cmd": [
                    "/bin/bash"
                ],
                "Image": "ubuntu",
                "Volumes": {
                    "/var/www": {}
                },
                "WorkingDir": "",
                "Entrypoint": null,
                "OnBuild": null,
                "Labels": {}
            },
            "NetworkSettings": {
                "Bridge": "",
                "SandboxID": "d4b14f5b49a7d2781ef99426c1d4f2818ba981a1129cf72e89c117a8f533dc07",
                "HairpinMode": false,
                "LinkLocalIPv6Address": "",
                "LinkLocalIPv6PrefixLen": 0,
                "Ports": {},
                "SandboxKey": "/var/run/docker/netns/d4b14f5b49a7",
                "SecondaryIPAddresses": null,
                "SecondaryIPv6Addresses": null,
                "EndpointID": "",
                "Gateway": "",
                "GlobalIPv6Address": "",
                "GlobalIPv6PrefixLen": 0,
                "IPAddress": "",
                "IPPrefixLen": 0,
                "IPv6Gateway": "",
                "MacAddress": "",
                "Networks": {
                    "bridge": {
                        "IPAMConfig": null,
                        "Links": null,
                        "Aliases": null,
                        "NetworkID": "076acb80b091ccbe5cf71d6aa9b94ce83a0921ba8c2308cfd89770d8052184b4",
                        "EndpointID": "",
                        "Gateway": "",
                        "IPAddress": "",
                        "IPPrefixLen": 0,
                        "IPv6Gateway": "",
                        "GlobalIPv6Address": "",
                        "GlobalIPv6PrefixLen": 0,
                        "MacAddress": "",
                        "DriverOpts": null
                    }
                }
            }
        }
    ]
    ```

    `docker container prune`

    `docker run -it -v "/home/jeiel.lopes/development/github/jeielml/alura/docker/volumes:/var/www" ubuntu` 
    ```
        root@be01d4699587:/# cd var/www/
        root@be01d4699587:/var/www# ls
        root@be01d4699587:/var/www# touch novo-arquivo.txt
        root@be01d4699587:/var/www# echo "este arquivo foi criado dentro do volume" > novo-arquivo.txt 
        root@be01d4699587:/var/www# 
    ```


    * Rodando código dentro de um containder

        `docker run -d -p 8081:3000 -v "/home/jeiel.lopes/development/github/jeielml/alura/docker/volumes/volume-exemplo:/var/www"  -w "/var/www" node npm start`  > roda o `npm start` ao startar o servidor > `-w` seta o "working directory"


----
----
# Criando um Dockerfile

Criar o arquivo `/${dir}/volume-exemplo/Dockerfile` 

Incluir o seguinte conteúdo:

```
FROM node:latest 
MAINTAINER Jeiel Miguel Lopes
COPY . /var/www
WORKDIR /var/www
RUN npm install
ENTRYPOINT npm start
EXPOSE 3000
```

 * `FROM node:latest` : Imagem criada a partir da ultima imagem do node
 * `MAINTAINER Jeiel Miguel Lopes` Mantenedor da imagem
 * `COPY . /var/www`: copia os arquivos do diretorio corrente para a pasta `/var/www` dentro do container
 * `WORKDIR /var/www`: seta o work directory onde o comando de `run` e `entrypoint` serão executados
 * `RUN npm install` : comando a ser executado na inicialização do container
 * `ENTRYPOINT npm start`: instrução a ser executada quando o container estiver pronto
 * `EXPOSE 3000` porta que será exposta


Buildando a imagem:

`docker build -t jeielml/node .` : Se o dockerfile tem o nome default não precisa especificar o nome (`-f Dockerfile`)

`docker run -d -p 8080:3000 jeielml/node`


----
----

# Subindo uma imagem no docker hub

* Criar uma conta do docker hub

* Fazer login no docker via terminal

    `docker login`

* Publicar a imagem do docker hub

    `docker push jeielml/node` > https://hub.docker.com/repository/docker/jeielml/node

* baixar imagem

    `docker pull jeielml/node`


----
----
# Networking no Docker


* Criando uma network docker
    `docker network create --driver bridge minha-rede`

    `docker run -it --name meu-container-de-ubuntu --network minha-rede ubuntu` 

    `docker run -it --name meu-container-de-ubuntu-B --network minha-rede ubuntu`

    `docker run -it --name meu-container-de-ubuntu-C --network minha-rede ubuntu apt-get update && apt-get install iputils-ping`


    ```
    ...
    "Networks": {
                "minha-rede": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": [
                        "fa7ed6314b30"
                    ],
                    "NetworkID": "bff834883487c9c253df4e1982d2af091f6ea53e3953b35cc04a13acb9b6fec9",
                    "EndpointID": "a1af437e6d1cc420928a01186f69c4a1a03c23b7318a5f8a18aeb9993f573508",
                    "Gateway": "172.18.0.1",
                    "IPAddress": "172.18.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:12:00:02",
                    "DriverOpts": null
                }
            }
            ...
    ```

 * Criando o projeto Alura Books com Node e MongoDB

    `docker pull douglasq/alura-books:cap05`

    `docker pull mongo`

    `docker run -d --name meu-mongo --network minha-rede mongo`

    `docker run --network minha-rede -d -p 8080:3000 douglasq/alura-books:cap05`

    `http://localhost:8080/seed` >  cadsatrar livros

    `http://localhost:8080/` consultar livros


    `docker network inspect minha-rede` inspeciona containers na rede

    ```
    [
        {
            "Name": "minha-rede",
            "Id": "bff834883487c9c253df4e1982d2af091f6ea53e3953b35cc04a13acb9b6fec9",
            "Created": "2021-03-13T11:28:26.999834751-03:00",
            "Scope": "local",
            "Driver": "bridge",
            "EnableIPv6": false,
            "IPAM": {
                "Driver": "default",
                "Options": {},
                "Config": [
                    {
                        "Subnet": "172.18.0.0/16",
                        "Gateway": "172.18.0.1"
                    }
                ]
            },
            "Internal": false,
            "Attachable": false,
            "Ingress": false,
            "ConfigFrom": {
                "Network": ""
            },
            "ConfigOnly": false,
            "Containers": {
                "416531717e1e5c6344dbb3d6f49d243573f5121bbb314249922e72f0eb5130ba": {
                    "Name": "meu-mongo",
                    "EndpointID": "c6bbfd8246eb87d5aeb06b0c943f820afb31c53b93ae867bfeedad204873e38a",
                    "MacAddress": "02:42:ac:12:00:02",
                    "IPv4Address": "172.18.0.2/16",
                    "IPv6Address": ""
                },
                "854a869a906b86ebfd2afaee907d7910c32e1a94c5e0cd4ec7677127cad925c2": {
                    "Name": "stoic_northcutt",
                    "EndpointID": "c9a90b9f616b7b109323ce139770264a1e65746a561629771cd444889afa2529",
                    "MacAddress": "02:42:ac:12:00:03",
                    "IPv4Address": "172.18.0.3/16",
                    "IPv6Address": ""
                }
            },
            "Options": {},
            "Labels": {}
        }
    ]


    ```

Neste capítulo aprendemos:

* Que imagens criadas pelo Docker acessam a mesma rede, porém apenas através de IP.
* Ao criar uma rede é possível realizar a comunicação entre os containers através do seu nome.
* Que durante a criação de uma rede precisamos indicar qual driver utilizaremos, geralmente, o driver bridge.
* Segue também uma breve lista dos comandos utilizados:

    * `hostname -i` - mostra o ip atribuído ao container pelo docker (funciona apenas dentro do container).
    * `docker network create --driver bridge NOME_DA_REDE` - cria uma rede especificando o driver desejado.
    * `docker run -it --name NOME_CONTAINER --network NOME_DA_REDE NOME_IMAGEM` - cria um container especificando seu nome e qual rede deverá ser usada.


----
----
# Entendendo o Docker Compose

* Instalando o docker compose:
    `sudo curl -L https://github.com/docker/compose/releases/download/1.15.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose`

    `sudo chmod +x /usr/local/bin/docker-compose`

* Faz o build do arquivo docker-compose.yml

    `docker-compose build` 

    `docker-compose up`


    http://localhost:81/

    http://localhost:81/seed


    `docker-compose up -d`

    `docker-compose down` > para o serviço e remove o container

    `docker exec -it alura-books-1 ping alura-books-2`

    `docker exec -it alura-books-1 ping node2`


Segue a lista com os principais comandos utilizados durante o curso:

* Comandos relacionados às informações
    * `docker version` - exibe a versão do docker que está instalada.
    * `docker inspect ID_CONTAINER` - retorna diversas informações sobre o container.
    * `docker ps` - exibe todos os containers em execução no momento.
    * `docker ps -a` - exibe todos os containers, independentemente de estarem em execução ou não.
* Comandos relacionados à execução
    * `docker run NOME_DA_IMAGEM` - cria um container com a respectiva imagem passada como parâmetro.
    * `docker run -it NOME_DA_IMAGEM` - conecta o terminal que estamos utilizando com o do container.
    * `docker run -d -P --name NOME dockersamples/static-site` - ao executar, dá um nome ao container e define uma porta aleatória.
    * `docker run -d -p 12345:80 dockersamples/static-site` - define uma porta específica para ser atribuída à porta 80 do container, neste caso 12345.
    * `docker run -v "CAMINHO_VOLUME" NOME_DA_IMAGEM` - cria um volume no respectivo caminho do container.
    * `docker run -it --name NOME_CONTAINER --network NOME_DA_REDE NOME_IMAGEM` - cria um container especificando seu nome e qual rede deverá ser usada.
