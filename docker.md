# Fooocus no Docker

A imagem Docker é baseada no NVIDIA CUDA 12.4 e PyTorch 2.1. Veja o [Dockerfile](Dockerfile) e o [requirements_docker.txt](requirements_docker.txt) para detalhes.

## Requisitos

- Um computador com especificações suficientes para rodar o Fooocus, e drivers proprietários da Nvidia
- Docker, Docker Compose ou Podman

## Início rápido

**Mais informações nas [notas](#notas).**

### Executar com Docker Compose

1. Clone este repositório
2. Execute o container Docker com `docker compose up`.

### Executar com Docker

```sh
docker run -p 7865:7865 -v fooocus-data:/content/data -it \
--gpus all \
-e CMDARGS=--listen \
-e DATADIR=/content/data \
-e config_path=/content/data/config.txt \
-e config_example_path=/content/data/config_modification_tutorial.txt \
-e path_checkpoints=/content/data/models/checkpoints/ \
-e path_loras=/content/data/models/loras/ \
-e path_embeddings=/content/data/models/embeddings/ \
-e path_vae_approx=/content/data/models/vae_approx/ \
-e path_upscale_models=/content/data/models/upscale_models/ \
-e path_inpaint=/content/data/models/inpaint/ \
-e path_controlnet=/content/data/models/controlnet/ \
-e path_clip_vision=/content/data/models/clip_vision/ \
-e path_fooocus_expansion=/content/data/models/prompt_expansion/fooocus_expansion/ \
-e path_outputs=/content/app/outputs/ \
ghcr.io/lllyasviel/fooocus
```

### Executar com Podman

```sh
podman run -p 7865:7865 -v fooocus-data:/content/data -it \
--security-opt=no-new-privileges --cap-drop=ALL --security-opt label=type:nvidia_container_t --device=nvidia.com/gpu=all \
-e CMDARGS=--listen \
-e DATADIR=/content/data \
-e config_path=/content/data/config.txt \
-e config_example_path=/content/data/config_modification_tutorial.txt \
-e path_checkpoints=/content/data/models/checkpoints/ \
-e path_loras=/content/data/models/loras/ \
-e path_embeddings=/content/data/models/embeddings/ \
-e path_vae_approx=/content/data/models/vae_approx/ \
-e path_upscale_models=/content/data/models/upscale_models/ \
-e path_inpaint=/content/data/models/inpaint/ \
-e path_controlnet=/content/data/models/controlnet/ \
-e path_clip_vision=/content/data/models/clip_vision/ \
-e path_fooocus_expansion=/content/data/models/prompt_expansion/fooocus_expansion/ \
-e path_outputs=/content/app/outputs/ \
ghcr.io/lllyasviel/fooocus
```

Quando você ver a mensagem `Use the app with http://0.0.0.0:7865/` no console, você pode acessar esse endereço no seu navegador.

Seus modelos e saídas (outputs) são armazenados no volume `fooocus-data`, que geralmente fica em `/var/lib/docker/volumes/` (ou `~/.local/share/containers/storage/volumes/` se estiver usando `podman`).

## Construindo a imagem localmente

Clone o repositório primeiro e abra um terminal na pasta.

Para construir com `docker`:
```sh
docker build . -t fooocus
```

Para construir com `podman`:
```sh
podman build . -t fooocus
```

## Detalhes

### Atualizar o container manualmente (docker compose)

Se você estiver usando `docker compose up` continuamente, o container não será atualizado automaticamente para a última versão do Fooocus.
Execute `git pull` antes de rodar `docker compose build --no-cache` para construir a imagem com a versão mais recente do Fooocus.
Depois, você pode iniciar com `docker compose up`.

### Importar modelos e outputs

Se você quiser importar arquivos de modelos ou da pasta outputs, pode adicionar os seguintes "bind mounts" no [docker-compose.yml](docker-compose.yml) ou no seu método preferido de rodar o container:
```
#- ./models:/import/models   # Depois de importar os arquivos, você não precisa montar de novo.
#- ./outputs:/import/outputs  # Depois de importar os arquivos, você não precisa montar de novo.
```
Após rodar o container, seus arquivos serão copiados para `/content/data/models` e `/content/data/outputs`.
Como `/content/data` é uma pasta de volume persistente, seus arquivos serão preservados mesmo se você reexecutar o container sem essas montagens.

### Caminhos dentro do container

|Caminho|Detalhes|
|-|-|
|/content/app|Pasta onde o aplicativo é armazenado|
|/content/app/models.org|Pasta "models" original.<br>Os arquivos são copiados para `/content/app/models`, que é um link simbólico para `/content/data/models` toda vez que o container inicia. (Arquivos existentes não serão sobrescritos.)|
|/content/data|Ponto de montagem do volume persistente|
|/content/data/models|Essa pasta é linkada para `/content/app/models`|
|/content/data/outputs|Essa pasta é linkada para `/content/app/outputs`|

### Variáveis de ambiente

Você pode alterar parâmetros do `config.txt` usando variáveis de ambiente.
**O valor definido nas variáveis de ambiente tem prioridade sobre o valor definido no `config.txt`, e será salvo no `config_modification_tutorial.txt`**

As variáveis específicas do Docker estão abaixo. Elas são usadas pelo `entrypoint.sh`:
|Variável|Detalhes|
|-|-|
|DATADIR|Localização de `/content/data`.|
|CMDARGS|Argumentos para o [entry_with_update.py](entry_with_update.py), chamado pelo [entrypoint.sh](entrypoint.sh)|
|config_path|Localização do `config.txt`|
|config_example_path|Localização do `config_modification_tutorial.txt`|
|HF_MIRROR|Domínio do site mirror do Huggingface|

Você também pode usar as mesmas chaves e valores JSON explicados em `config_modification_tutorial.txt` como variáveis de ambiente.
Veja exemplos no [docker-compose.yml](docker-compose.yml)

## Notas

- Por favor, mantenha `path_outputs` dentro de `/content/app`. Caso contrário, você pode ter erro ao abrir o histórico.
- Docker no Mac/Windows ainda possui problemas de lentidão no acesso a volumes quando você usa volumes do tipo "bind mount". Consulte [este artigo](https://docs.docker.com/storage/volumes/#use-a-volume-with-docker-compose) para não usar "bind mount".
- O backend MPS (Metal Performance Shaders, Apple Silicon M1/M2/etc.) ainda não é suportado no Docker. Veja https://github.com/pytorch/pytorch/issues/81224
- Você também pode usar `docker compose up -d` para iniciar o container em modo "detached" e acompanhar os logs com `docker compose logs -f`. Assim, você pode fechar o terminal e manter o container rodando.
