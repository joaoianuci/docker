Docker - Introdução

O quê é Docker, antes de responder à esta pergunta precisamos analisar conceitos importantes

- Para que serve e o que é um container
- O que é uma imagem
- Como esses conceitos se relacionam com o Docker


Container 

Um container é um processo isolado que roda em um sistema operacional, ele é isolado de outros containers e do próprio sistema operacional, ele possui seu próprio sistema de arquivos, processos, rede, etc.
- Como isso é possível?
Para isso ser possível precisamos ter 3 conceitos fundamentais:
- Namespaces
- Cgroups
- OverlayFS

Namespaces: é o que isola os processos daquele container, sendo assim apenas processos pai e filhos dentro daquele mesmo namespace podem se comunicar diretamente.

Cgroups: é o que isola os recursos daquele container, sendo assim cada container possui sua própria cota de CPU, memória, etc.

OverlayFS: é um sistema de camadas que constrói o sistema padrão do container, sendo assim cada container levantado é feito por cima de uma camada imutável, entretanto ele possui uma camada de leitura e escrita que podemos utilizar para atualizar nossa imagem.
Quando ocorre uma mudança nas camadas de leitura e escrita, ao realizar um commit, àquelas mudanças são salvas em uma nova camada imutável, sendo assim a camada de leitura e escrita volta ao estado inicial porém com uma imagem atualizada.
Logo podemos ter imagens derivadas de diversas outras imagens, protanto temos uma imagem base que possui apenas o sistema operacional e outras imagens que possuem o sistema operacional e uma aplicação, e assim por diante.

Imagem 1 -> Ubuntu (realizo um commit adicionando o Apache)
Imagem 2 -> Ubuntu + Apache (realizo um commit adicionando o PHP)
Imagem 3 -> Ubuntu + Apache + PHP (realizo um commit adicionando o Wordpress)
Imagem Produção -> Ubuntu + Apache + PHP + Wordpress (minha imagem final)

Essas imagens em ordem seriam como camadas que constrói meu container.

Apesar de serem processos isolados, o Docker torna capaz que esses containers se comuniquem entre si, através do conceito de Networks
Além disso podemos também compartilhar arquivos entre os containers e até entre o nosso sistema operacional, através do conceito de Volumes

Por fim, Docker é uma ferramenta que facilita a criação e gerenciamento de containers, sendo assim podemos criar, iniciar, parar, remover, criar redes e volumes para nossos containers, tudo isso através do Docker Client / Daemon - API.

Docker Desktop no Windows, Docker Desktop no Linux e Docker Engine

- Docker é criado para rodar em Linux, porém podemos utilizar o Docker Desktop no Windows e no Mac, que nada mais é que uma máquina virtual com Linux que roda o Docker Engine.

- Porém no Linux podemos instalar o Docker Engine diretamente no nosso sistema operacional, sem a necessidade do Docker Desktop ou uma maquina virtual.

- Outra abordagem  é utilizarmos Windows com WSL, que é um subsistema do Windows para Linux, sendo assim podemos instalar o Docker Engine diretamente no WSL. Como o WSL é um Linux completo e o Docker Engine é feito para rodar em Linux, não temos problemas de compatibilidade.

- No MacOS, só podemos utilizar o Docker Desktop mesmo, que não é o ideal porém cumpre a maior parte das necessidades.