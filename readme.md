<div align=center>
<img src="https://github.com/lllyasviel/Fooocus/assets/19834515/483fb86d-c9a2-4c20-997c-46dafc124f25">
</div>

# Fooocus

[>>> Clique Aqui para Instalar o Fooocus <<<](#download)

Fooocus é um software de geração de imagens (baseado em [Gradio](https://www.gradio.app/) <a href='https://github.com/gradio-app/gradio'><img src='https://img.shields.io/github/stars/gradio-app/gradio'></a>).

Fooocus apresenta uma reimaginação do design de geradores de imagens. O software é offline, de código aberto e gratuito, e ao mesmo tempo, semelhante a muitos geradores de imagens online como o Midjourney, o ajuste manual não é necessário, e os usuários só precisam se concentrar nos prompts e nas imagens. O Fooocus também simplificou a instalação: entre pressionar "download" e gerar a primeira imagem, o número de cliques necessários é estritamente limitado a menos de 3. A memória mínima de GPU necessária é de 4GB (Nvidia).

**Recentemente, muitos sites falsos apareceram no Google quando você pesquisa por “fooocus”. Não confie neles – esta é a única fonte oficial do Fooocus.**

# Status do Projeto: Suporte de Longo Prazo (LTS) Limitado com Correções de Bugs Apenas

O projeto Fooocus, construído inteiramente na arquitetura **Stable Diffusion XL**, está agora em um estado de suporte de longo prazo (LTS) limitado, com correções de bugs apenas. Como as funcionalidades existentes são consideradas quase livres de problemas programáticos (graças aos enormes esforços de [mashb1t](https://github.com/mashb1t)), as atualizações futuras se concentrarão exclusivamente em corrigir quaisquer bugs que possam surgir.

**Não há planos atuais para migrar ou incorporar arquiteturas de modelos mais novas.** No entanto, isso pode mudar com o tempo com o desenvolvimento da comunidade de código aberto. Por exemplo, se a comunidade convergir para um único método dominante para geração de imagens (o que pode realmente acontecer em meio ou um ano, dado o status atual), o Fooocus também pode migrar para esse método exato.

Para aqueles interessados em utilizar modelos mais novos, como **Flux**, recomendamos explorar plataformas alternativas como [WebUI Forge](https://github.com/lllyasviel/stable-diffusion-webui-forge) (também de nossa autoria), [ComfyUI/SwarmUI](https://github.com/comfyanonymous/ComfyUI). Além disso, vários [excelentes forks do Fooocus](https://github.com/lllyasviel/Fooocus?tab=readme-ov-file#forks) estão disponíveis para experimentação.

Novamente, recentemente muitos sites falsos apareceram no Google quando você pesquisa por “fooocus”. **NÃO** obtenha o Fooocus desses sites – esta página é a única fonte oficial do Fooocus. Nunca tivemos nenhum site como “fooocus.com”, “fooocus.net”, “fooocus.co”, “fooocus.ai”, “fooocus.org”, “fooocus.pro”, “fooocus.one”. Esses sites são TODOS FALSOS. **Eles NÃO têm ABSOLUTAMENTE nenhuma relação conosco. Fooocus é um software 100% não comercial, offline e de código aberto.**

# Recursos

Abaixo está uma lista rápida usando exemplos do Midjourney:

| Midjourney | Fooocus |
| - | - |
| Geração de texto para imagem de alta qualidade sem precisar de muita engenharia de prompt ou ajuste de parâmetros. <br> (Método desconhecido) | Geração de texto para imagem de alta qualidade sem precisar de muita engenharia de prompt ou ajuste de parâmetros. <br> (Fooocus tem um motor de processamento de prompt baseado em GPT-2 offline e muitas melhorias de amostragem, de modo que os resultados são sempre bonitos, não importa se seu prompt é tão curto quanto “casa no jardim” ou tão longo quanto 1000 palavras) |
| V1 V2 V3 V4 | Imagem de Entrada -> Upscale ou Variação -> Vary (Sutil) / Vary (Forte)|
| U1 U2 U3 U4 | Imagem de Entrada -> Upscale ou Variação -> Upscale (1.5x) / Upscale (2x) |
| Inpaint / Up / Down / Left / Right (Pan) | Imagem de Entrada -> Inpaint ou Outpaint -> Inpaint / Up / Down / Left / Right <br> (Fooocus usa seu próprio algoritmo de inpaint e modelos de inpaint, de modo que os resultados são mais satisfatórios do que todos os outros softwares que usam o método/modelo de inpaint padrão do SDXL) |
| Prompt de Imagem | Imagem de Entrada -> Prompt de Imagem <br> (Fooocus usa seu próprio algoritmo de prompt de imagem, de modo que a qualidade do resultado e a compreensão do prompt são mais satisfatórias do que todos os outros softwares que usam métodos SDXL padrão como IP-Adapters ou Revisions padrão) |
| --style | Avançado -> Estilo |
| --stylize | Avançado -> Avançado -> Orientação |
| --niji | [Múltiplos lançadores: "run.bat", "run_anime.bat", e "run_realistic.bat".](https://github.com/lllyasviel/Fooocus/discussions/679) <br> Fooocus suporta modelos SDXL no Civitai <br> (Você pode pesquisar no Google “Civitai” se não souber sobre isso) |
| --quality | Avançado -> Qualidade |
| --repeat | Avançado -> Número de Imagens |
| Múltiplos Prompts (::) | Basta usar várias linhas de prompts |
| Pesos de Prompt | Você pode usar "Eu estou (feliz:1.5)". <br> Fooocus usa o algoritmo de reponderação do A1111, de modo que os resultados são melhores do que o ComfyUI se os usuários copiarem prompts diretamente do Civitai. (Porque se os prompts são escritos na reponderação do ComfyUI, os usuários são menos propensos a copiar textos de prompt, pois preferem arrastar arquivos) <br> Para usar embedding, você pode usar "(embedding:file_name:1.1)" |
| --no | Avançado -> Prompt Negativo |
| --ar | Avançado -> Proporções de Aspecto |
| InsightFace | Imagem de Entrada -> Prompt de Imagem -> Avançado -> Troca de Rosto |
| Descrever | Imagem de Entrada -> Descrever |

Abaixo está uma lista rápida usando exemplos do LeonardoAI:

| LeonardoAI | Fooocus |
| - | - |
| Prompt Magic | Avançado -> Estilo -> Fooocus V2 |
| Parâmetros Avançados de Amostragem (como Contraste/Nitidez/etc) | Avançado -> Avançado -> Nitidez de Amostragem / etc |
| ControlNets Amigáveis ao Usuário | Imagem de Entrada -> Prompt de Imagem -> Avançado |

Além disso, [clique aqui para explorar os recursos avançados.](https://github.com/lllyasviel/Fooocus/discussions/117)

# Download

### Windows

Você pode baixar o Fooocus diretamente com:

**[>>> Clique aqui para baixar <<<](https://github.com/lllyasviel/Fooocus/releases/download/v2.5.0/Fooocus_win64_2-5-0.7z)**

Depois de baixar o arquivo, descompacte-o e execute o "run.bat".

![image](https://github.com/lllyasviel/Fooocus/assets/19834515/c49269c4-c274-4893-b368-047c401cc58c)

Na primeira vez que você iniciar o software, ele baixará automaticamente os modelos:

1. Ele baixará [modelos padrão](#modelos-padrão) para a pasta "Fooocus\models\checkpoints" de acordo com diferentes predefinições. Você pode baixá-los antecipadamente se não quiser o download automático.
2. Observe que, se você usar inpaint, na primeira vez que fizer inpaint em uma imagem, ele baixará [o modelo de controle de inpaint do Fooocus daqui](https://huggingface.co/lllyasviel/fooocus_inpaint/resolve/main/inpaint_v26.fooocus.patch) como o arquivo "Fooocus\models\inpaint\inpaint_v26.fooocus.patch" (o tamanho deste arquivo é 1.28GB).

Após o Fooocus 2.1.60, você também terá `run_anime.bat` e `run_realistic.bat`. Eles são diferentes predefinições de modelos (e exigem modelos diferentes, mas eles serão baixados automaticamente). [Confira aqui para mais detalhes](https://github.com/lllyasviel/Fooocus/discussions/679).

Após o Fooocus 2.3.0, você também pode alternar predefinições diretamente no navegador. Lembre-se de adicionar esses argumentos se quiser alterar o comportamento padrão:
* Use `--disable-preset-selection` para desativar a seleção de predefinições no navegador.
* Use `--always-download-new-model` para baixar modelos ausentes ao alternar predefinições. O padrão é voltar para `previous_default_models` definido na predefinição correspondente, veja também a saída do terminal.

![image](https://github.com/lllyasviel/Fooocus/assets/19834515/d386f817-4bd7-490c-ad89-c1e228c23447)

Se você já tiver esses arquivos, pode copiá-los para os locais acima para acelerar a instalação.

Observe que, se você vir **"MetadataIncompleteBuffer" ou "PytorchStreamReader"**, seus arquivos de modelo estão corrompidos. Baixe os modelos novamente.

Abaixo está um teste em um laptop relativamente básico com **16GB de RAM do sistema** e **6GB de VRAM** (Nvidia 3060 laptop). A velocidade nesta máquina é de cerca de 1,35 segundos por iteração. Muito impressionante – atualmente, laptops com 3060 geralmente têm um preço muito acessível.

![image](https://github.com/lllyasviel/Fooocus/assets/19834515/938737a5-b105-4f19-b051-81356cb7c495)

Além disso, recentemente muitos outros softwares relataram que o driver Nvidia acima da versão 532 é às vezes 10x mais lento que o driver Nvidia 531. Se o tempo de geração for muito longo, considere baixar [Nvidia Driver 531 Laptop](https://www.nvidia.com/download/driverResults.aspx/199991/en-us/) ou [Nvidia Driver 531 Desktop](https://www.nvidia.com/download/driverResults.aspx/199990/en-us/).

Observe que o requisito mínimo é **4GB de memória de GPU Nvidia (4GB VRAM)** e **8GB de memória do sistema (8GB RAM)**. Isso requer o uso da técnica de Troca Virtual da Microsoft, que é automaticamente habilitada pela sua instalação do Windows na maioria dos casos, então você geralmente não precisa fazer nada sobre isso. No entanto, se você não tiver certeza, ou se você desativou manualmente (alguém realmente faria isso?), ou **se você vir qualquer "RuntimeError: CPUAllocator"**, você pode habilitá-lo aqui:

<details>
<summary>Clique aqui para ver as instruções de imagem. </summary>

![image](https://github.com/lllyasviel/Fooocus/assets/19834515/2a06b130-fe9b-4504-94f1-2763be4476e9)

**E certifique-se de que você tem pelo menos 40GB de espaço livre em cada unidade se ainda vir "RuntimeError: CPUAllocator"!**

</details>

Abra um problema se você usar dispositivos semelhantes, mas ainda não conseguir alcançar desempenhos aceitáveis.

Observe que o [requisito mínimo](#requisito-mínimo) para diferentes plataformas é diferente.

Veja também os problemas comuns e soluções [aqui](troubleshoot.md).

### Colab

(Último teste - 12 de agosto de 2024 por [mashb1t](https://github.com/mashb1t))

| Colab | Info
| --- | --- |
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lllyasviel/Fooocus/blob/main/fooocus_colab.ipynb) | Fooocus Oficial

No Colab, você pode modificar a última linha para `!python entry_with_update.py --share --always-high-vram` ou `!python entry_with_update.py --share --always-high-vram --preset anime` ou `!python entry_with_update.py --share --always-high-vram --preset realistic` para a Edição Padrão/Anime/Realista do Fooocus.

Você também pode alterar a predefinição na interface do usuário. Esteja ciente de que isso pode levar a timeouts após 60 segundos. Se for o caso, aguarde até que o download seja concluído, altere a predefinição para inicial e volte para a que você selecionou ou recarregue a página.

Observe que este Colab desativará o refiner por padrão, pois os recursos do Colab free são relativamente limitados (e alguns recursos "grandes" como prompt de imagem podem fazer com que o Colab de nível gratuito se desconecte). Garantimos que a geração básica de texto para imagem sempre funcione no Colab de nível gratuito.

Usar `--always-high-vram` desloca a alocação de recursos da RAM para a VRAM e alcança o melhor equilíbrio geral entre desempenho, flexibilidade e estabilidade na instância T4 padrão. Encontre mais informações [aqui](https://github.com/lllyasviel/Fooocus/pull/1710#issuecomment-1989185346).

Agradecemos a [camenduru](https://github.com/camenduru) pelo template!

### Linux (Usando Anaconda)

Se você quiser usar Anaconda/Miniconda, você pode

    git clone https://github.com/lllyasviel/Fooocus.git
    cd Fooocus
    conda env create -f environment.yaml
    conda activate fooocus
    pip install -r requirements_versions.txt

Em seguida, baixe os modelos: baixe [modelos padrão](#modelos-padrão) para a pasta "Fooocus\models\checkpoints". **Ou deixe o Fooocus baixar automaticamente os modelos** usando o lançador:

    conda activate fooocus
    python entry_with_update.py

Ou, se você quiser abrir uma porta remota, use

    conda activate fooocus
    python entry_with_update.py --listen

Use `python entry_with_update.py --preset anime` ou `python entry_with_update.py --preset realistic` para a Edição Anime/Realista do Fooocus.

### Linux (Usando Python Venv)

Seu Linux precisa ter **Python 3.10** instalado, e digamos que seu Python pode ser chamado com o comando **python3** com seu sistema venv funcionando; você pode

    git clone https://github.com/lllyasviel/Fooocus.git
    cd Fooocus
    python3 -m venv fooocus_env
    source fooocus_env/bin/activate
    pip install -r requirements_versions.txt

Veja as seções acima para o download dos modelos. Você pode iniciar o software com:

    source fooocus_env/bin/activate
    python entry_with_update.py

Ou, se você quiser abrir uma porta remota, use

    source fooocus_env/bin/activate
    python entry_with_update.py --listen

Use `python entry_with_update.py --preset anime` ou `python entry_with_update.py --preset realistic` para a Edição Anime/Realista do Fooocus.

### Linux (Usando Python nativo do sistema)

Se você sabe o que está fazendo, e seu Linux já tem **Python 3.10** instalado, e seu Python pode ser chamado com o comando **python3** (e Pip com **pip3**), você pode

    git clone https://github.com/lllyasviel/Fooocus.git
    cd Fooocus
    pip3 install -r requirements_versions.txt

Veja as seções acima para o download dos modelos. Você pode iniciar o software com:

    python3 entry_with_update.py

Ou, se você quiser abrir uma porta remota, use

    python3 entry_with_update.py --listen

Use `python entry_with_update.py --preset anime` ou `python entry_with_update.py --preset realistic` para a Edição Anime/Realista do Fooocus.

### Linux (GPUs AMD)

Observe que o [requisito mínimo](#requisito-mínimo) para diferentes plataformas é diferente.

O mesmo que as instruções acima. Você precisa mudar o torch para a versão AMD

    pip uninstall torch torchvision torchaudio torchtext functorch xformers 
    pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm5.6

O suporte à AMD não é intensivamente testado, no entanto. O suporte à AMD está em beta.

Use `python entry_with_update.py --preset anime` ou `python entry_with_update.py --preset realistic` para a Edição Anime/Realista do Fooocus.

### Windows (GPUs AMD)

Observe que o [requisito mínimo](#requisito-mínimo) para diferentes plataformas é diferente.

O mesmo que o Windows. Baixe o software e edite o conteúdo de `run.bat` como:

    .\python_embeded\python.exe -m pip uninstall torch torchvision torchaudio torchtext functorch xformers -y
    .\python_embeded\python.exe -m pip install torch-directml
    .\python_embeded\python.exe -s Fooocus\entry_with_update.py --directml
    pause

Em seguida, execute o `run.bat`.

O suporte à AMD não é intensivamente testado, no entanto. O suporte à AMD está em beta.

Para AMD, use `.\python_embeded\python.exe Fooocus\entry_with_update.py --directml --preset anime` ou `.\python_embeded\python.exe Fooocus\entry_with_update.py --directml --preset realistic` para a Edição Anime/Realista do Fooocus.

### Mac

Observe que o [requisito mínimo](#requisito-mínimo) para diferentes plataformas é diferente.

O Mac não é intensivamente testado. Abaixo está um guia não oficial para usar o Mac. Você pode discutir problemas [aqui](https://github.com/lllyasviel/Fooocus/pull/129).

Você pode instalar o Fooocus no Apple Mac silicon (M1 ou M2) com macOS 'Catalina' ou uma versão mais recente. O Fooocus é executado em computadores Apple silicon via aceleração de dispositivo [PyTorch](https://pytorch.org/get-started/locally/) MPS. Computadores Mac Silicon não vêm com uma placa gráfica dedicada, resultando em tempos de processamento de imagem significativamente mais longos em comparação com computadores com placas gráficas dedicadas.

1. Instale o gerenciador de pacotes conda e o pytorch nightly. Leia o guia [Accelerated PyTorch training on Mac](https://developer.apple.com/metal/pytorch/) da Apple Developer para obter instruções. Certifique-se de que o pytorch reconheça seu dispositivo MPS.
1. Abra o aplicativo Terminal do macOS e clone este repositório com `git clone https://github.com/lllyasviel/Fooocus.git`.
1. Mude para o novo diretório Fooocus, `cd Fooocus`.
1. Crie um novo ambiente conda, `conda env create -f environment.yaml`.
1. Ative seu novo ambiente conda, `conda activate fooocus`.
1. Instale os pacotes necessários para o Fooocus, `pip install -r requirements_versions.txt`.
1. Inicie o Fooocus executando `python entry_with_update.py`. (Alguns usuários de Mac M2 podem precisar de `python entry_with_update.py --disable-offload-from-vram` para acelerar o carregamento/descarregamento do modelo.) Na primeira vez que você executar o Fooocus, ele baixará automaticamente os modelos Stable Diffusion SDXL e levará um tempo significativo, dependendo da sua conexão com a internet.

Use `python entry_with_update.py --preset anime` ou `python entry_with_update.py --preset realistic` para a Edição Anime/Realista do Fooocus.

### Docker

Veja [docker.md](docker.md)

### Baixar Versão Anterior

Veja as diretrizes [aqui](https://github.com/lllyasviel/Fooocus/discussions/1405).

## Requisito Mínimo

Abaixo está o requisito mínimo para executar o Fooocus localmente. Se a capacidade do seu dispositivo for menor que esta especificação, você pode não conseguir usar o Fooocus localmente. (Por favor, nos informe, em qualquer caso, se a capacidade do seu dispositivo for menor, mas o Fooocus ainda funcionar.)

| Sistema Operacional  | GPU                          | Memória Mínima de GPU           | Memória Mínima do Sistema     | [Troca do Sistema](troubleshoot.md) | Nota                                                                       |
|-------------------|------------------------------|------------------------------|---------------------------|--------------------------------|----------------------------------------------------------------------------|
| Windows/Linux     | Nvidia RTX 4XXX              | 4GB                          | 8GB                       | Necessária                       | mais rápido                                                                    |
| Windows/Linux     | Nvidia RTX 3XXX              | 4GB                          | 8GB                       | Necessária                       | geralmente mais rápido que RTX 2XXX                                               |
| Windows/Linux     | Nvidia RTX 2XXX              | 4GB                          | 8GB                       | Necessária                       | geralmente mais rápido que GTX 1XXX                                               |
| Windows/Linux     | Nvidia GTX 1XXX              | 8GB (&ast; 6GB incerto)    | 8GB                       | Necessária                       | apenas marginalmente mais rápido que a CPU                                            |
| Windows/Linux     | Nvidia GTX 9XX               | 8GB                          | 8GB                       | Necessária                       | mais rápido ou mais lento que a CPU                                                  |
| Windows/Linux     | Nvidia GTX < 9XX             | Não suportado                | /                         | /                              | /                                                                          |
| Windows           | AMD GPU                      | 8GB    (atualizado em 30 de dezembro de 2023) | 8GB                       | Necessária                       | via DirectML (&ast; ROCm está em espera), cerca de 3x mais lento que Nvidia RTX 3XXX |
| Linux             | AMD GPU                      | 8GB                          | 8GB                       | Necessária                       | via ROCm, cerca de 1.5x mais lento que Nvidia RTX 3XXX                           |
| Mac               | M1/M2 MPS                    | Compartilhada                       | Compartilhada                    | Compartilhada                         | cerca de 9x mais lento que Nvidia RTX 3XXX                                       |
| Windows/Linux/Mac | apenas CPU                 | 0GB                          | 32GB                      | Necessária                       | cerca de 17x mais lento que Nvidia RTX 3XXX                                      |

&ast; AMD GPU ROCm (em espera): A AMD ainda está trabalhando no suporte ao ROCm no Windows.

&ast; Nvidia GTX 1XXX 6GB incerto: Algumas pessoas relatam sucesso com 6GB em GTX 10XX, mas outras relatam casos de falha.

*Observe que o Fooocus é apenas para geração de imagens de qualidade extremamente alta. Não vamos suportar modelos menores para reduzir o requisito e sacrificar a qualidade do resultado.*

## Solução de Problemas

Veja os problemas comuns [aqui](troubleshoot.md).

## Modelos Padrão
<a name="models"></a>

Dependendo de diferentes objetivos, os modelos e configurações padrão do Fooocus são diferentes:

| Tarefa      | Windows | Argumentos do Linux | Modelo Principal                  | Refiner | Configuração                                                                         |
|-----------| --- | --- |-----------------------------| --- |--------------------------------------------------------------------------------|
| Geral   | run.bat |  | juggernautXL_v8Rundiffusion | não usado | [aqui](https://github.com/lllyasviel/Fooocus/blob/main/presets/default.json)   |
| Realista | run_realistic.bat | --preset realistic | realisticStockPhoto_v20     | não usado | [aqui](https://github.com/lllyasviel/Fooocus/blob/main/presets/realistic.json) |
| Anime     | run_anime.bat | --preset anime | animaPencilXL_v500          | não usado | [aqui](https://github.com/lllyasviel/Fooocus/blob/main/presets/anime.json)     |

Observe que o download é **automático** - você não precisa fazer nada se a conexão com a internet estiver OK. No entanto, você pode baixá-los manualmente se você (ou movê-los de outro lugar) tiver sua própria preparação.

## Acesso à UI e Autenticação
Além de ser executado no localhost, o Fooocus também pode expor sua UI de duas maneiras: 
* Ouvinte de UI local: use `--listen` (especifique a porta, por exemplo, com `--port 8888`). 
* Acesso à API: use `--share` (registra um endpoint em `.gradio.live`).

Em ambos os casos, o acesso não é autenticado por padrão. Você pode adicionar autenticação básica criando um arquivo chamado `auth.json` no diretório principal, que contém uma lista de objetos JSON com as chaves `user` e `pass` (veja o exemplo em [auth-example.json](./auth-example.json)).

## Lista de Truques "Ocultos"
<a name="tech_list"></a>

<details>
<summary>Clique para ver uma lista de truques. Eles são baseados no SDXL e não estão muito atualizados com os modelos mais recentes.</summary>

1. Expansão de prompt baseada em [GPT2 como um estilo dinâmico "Fooocus V2"](https://github.com/lllyasviel/Fooocus/discussions/117#raw). (semelhante ao pré-processamento oculto do Midjourney e ao modo "raw", ou ao Prompt Magic do LeonardoAI).
2. Troca de refiner nativa dentro de um único k-sampler. A vantagem é que o modelo refiner agora pode reutilizar o momentum (ou parâmetros de histórico do ODE) coletado do k-sampling para alcançar uma amostragem mais coerente. No high-res fix do Automatic1111 e no sistema de nós do ComfyUI, o modelo base e o refiner usam dois k-samplers independentes, o que significa que o momentum é amplamente desperdiçado e a continuidade da amostragem é quebrada. O Fooocus usa seu próprio k-diffusion sampling avançado que garante uma troca de refiner nativa, contínua e sem interrupções. (Atualização em 13 de agosto: Na verdade, discuti isso com o Automatic1111 há alguns dias, e parece que a “troca de refiner nativa dentro de um único k-sampler” foi [mesclada]( https://github.com/AUTOMATIC1111/stable-diffusion-webui/pull/12371) no branch de desenvolvimento do webui. Ótimo!)
3. Orientação ADM negativa. Como o nível de maior resolução do XL Base não tem atenções cruzadas, os sinais positivos e negativos para o nível de maior resolução do XL não podem receber contrastes suficientes durante a amostragem CFG, fazendo com que os resultados pareçam um pouco plásticos ou excessivamente suaves em certos casos. Felizmente, como o nível de maior resolução do XL ainda é condicionado às proporções de imagem (ADM), podemos modificar o adm no lado positivo/negativo para compensar a falta de contraste CFG no nível de maior resolução. (Atualização em 16 de agosto, o aplicativo IOS [Draw Things](https://apps.apple.com/us/app/draw-things-ai-generation/id6444050820) suportará Orientação ADM Negativa. Ótimo!)
4. Implementamos uma variação cuidadosamente ajustada da Seção 5.1 de ["Improving Sample Quality of Diffusion Models Using Self-Attention Guidance"](https://arxiv.org/pdf/2210.00939.pdf). O peso é definido como muito baixo, mas esta é a garantia final do Fooocus para garantir que o XL nunca produza uma aparência excessivamente suave ou plástica (exemplos [aqui](https://github.com/lllyasviel/Fooocus/discussions/117#sharpness)). Isso pode quase eliminar todos os casos em que o XL ainda ocasionalmente produz resultados excessivamente suaves, mesmo com orientação ADM negativa. (Atualização em 18 de agosto de 2023, o kernel Gaussiano do SAG foi alterado para um kernel anisotrópico para melhor preservação da estrutura e menos artefatos.)
5. Modificamos um pouco os templates de estilo e adicionamos o "cinematic-default".
6. Testamos o "sd_xl_offset_example-lora_1.0.safetensors" e parece que quando o peso do lora está abaixo de 0.5, os resultados são sempre melhores do que o XL sem lora.
7. Os parâmetros dos samplers são cuidadosamente ajustados.
8. Como o XL usa codificação posicional para a resolução de geração, as imagens geradas por várias resoluções fixas parecem um pouco melhores do que aquelas de resoluções arbitrárias (porque a codificação posicional não é muito boa em lidar com números inteiros que não foram vistos durante o treinamento). Isso sugere que as resoluções na UI podem ser codificadas para os melhores resultados.
9. Prompts separados para dois diferentes codificadores de texto parecem desnecessários. Prompts separados para o modelo base e refiner podem funcionar, mas os efeitos são aleatórios, e nos abstemos de implementar isso.
10. A família DPM parece bem adequada para o XL, já que o XL às vezes gera texturas excessivamente suaves, mas a família DPM às vezes gera texturas excessivamente densas em detalhes. Seu efeito conjunto parece neutro e atraente para a percepção humana.
11. Um sistema cuidadosamente projetado para equilibrar múltiplos estilos, bem como a expansão de prompt.
12. Usando o método do automatic1111 para normalizar a ênfase do prompt. Isso melhora significativamente os resultados quando os usuários copiam prompts diretamente do civitai.
13. O sistema de troca conjunta do refiner agora também suporta img2img e upscale de forma contínua.
14. Escala CFG e correção TSNR (ajustada para SDXL) quando CFG é maior que 10.
</details>

## Personalização

Após a primeira vez que você executar o Fooocus, um arquivo de configuração será gerado em `Fooocus\config.txt`. Este arquivo pode ser editado para alterar o caminho do modelo ou os parâmetros padrão.

Por exemplo, um `Fooocus\config.txt` editado (este arquivo será gerado após o primeiro lançamento) pode parecer com isso:

```json
{
    "path_checkpoints": "D:\\Fooocus\\models\\checkpoints",
    "path_loras": "D:\\Fooocus\\models\\loras",
    "path_embeddings": "D:\\Fooocus\\models\\embeddings",
    "path_vae_approx": "D:\\Fooocus\\models\\vae_approx",
    "path_upscale_models": "D:\\Fooocus\\models\\upscale_models",
    "path_inpaint": "D:\\Fooocus\\models\\inpaint",
    "path_controlnet": "D:\\Fooocus\\models\\controlnet",
    "path_clip_vision": "D:\\Fooocus\\models\\clip_vision",
    "path_fooocus_expansion": "D:\\Fooocus\\models\\prompt_expansion\\fooocus_expansion",
    "path_outputs": "D:\\Fooocus\\outputs",
    "default_model": "realisticStockPhoto_v10.safetensors",
    "default_refiner": "",
    "default_loras": [["lora_filename_1.safetensors", 0.5], ["lora_filename_2.safetensors", 0.5]],
    "default_cfg_scale": 3.0,
    "default_sampler": "dpmpp_2m",
    "default_scheduler": "karras",
    "default_negative_prompt": "low quality",
    "default_positive_prompt": "",
    "default_styles": [
        "Fooocus V2",
        "Fooocus Photograph",
        "Fooocus Negative"
    ]
}
```

Muitos outros parâmetros, formatos e exemplos estão em `Fooocus\config_modification_tutorial.txt` (esse arquivo será gerado após o primeiro lançamento).

Pense duas vezes antes de realmente modificar a configuração. Se você acabar quebrando alguma coisa, basta excluir `Fooocus\config.txt`. O Fooocus retornará ao padrão.

Uma forma mais segura é apenas executar `"run_anime.bat"` ou `"run_realistic.bat"` – eles já devem ser bons o suficiente para diferentes tarefas.

~Observe que o arquivo `user_path_config.txt` está obsoleto e será removido em breve.~ (Edit: ele já foi removido.)

### Todos os parâmetros de linha de comando (CMD Flags)

```
entry_with_update.py  [-h] [--listen [IP]] [--port PORT]
                      [--disable-header-check [ORIGIN]]
                      [--web-upload-size WEB_UPLOAD_SIZE]
                      [--hf-mirror HF_MIRROR]
                      [--external-working-path PATH [PATH ...]]
                      [--output-path OUTPUT_PATH]
                      [--temp-path TEMP_PATH] [--cache-path CACHE_PATH]
                      [--in-browser] [--disable-in-browser]
                      [--gpu-device-id DEVICE_ID]
                      [--async-cuda-allocation | --disable-async-cuda-allocation]
                      [--disable-attention-upcast]
                      [--all-in-fp32 | --all-in-fp16]
                      [--unet-in-bf16 | --unet-in-fp16 | --unet-in-fp8-e4m3fn | --unet-in-fp8-e5m2]
                      [--vae-in-fp16 | --vae-in-fp32 | --vae-in-bf16]
                      [--vae-in-cpu]
                      [--clip-in-fp8-e4m3fn | --clip-in-fp8-e5m2 | --clip-in-fp16 | --clip-in-fp32]
                      [--directml [DIRECTML_DEVICE]]
                      [--disable-ipex-hijack]
                      [--preview-option [none,auto,fast,taesd]]
                      [--attention-split | --attention-quad | --attention-pytorch]
                      [--disable-xformers]
                      [--always-gpu | --always-high-vram | --always-normal-vram | --always-low-vram | --always-no-vram | --always-cpu [CPU_NUM_THREADS]]
                      [--always-offload-from-vram]
                      [--pytorch-deterministic] [--disable-server-log]
                      [--debug-mode] [--is-windows-embedded-python]
                      [--disable-server-info] [--multi-user] [--share]
                      [--preset PRESET] [--disable-preset-selection]
                      [--language LANGUAGE]
                      [--disable-offload-from-vram] [--theme THEME]
                      [--disable-image-log] [--disable-analytics]
                      [--disable-metadata] [--disable-preset-download]
                      [--disable-enhance-output-sorting]
                      [--enable-auto-describe-image]
                      [--always-download-new-model]
                      [--rebuild-hash-cache [CPU_NUM_THREADS]]
```


## Recursos de Prompt Inline

### Curingas (Wildcards)

Exemplo de prompt: `__color__ flower`

Processado para prompt positivo e negativo.

Seleciona um curinga aleatório de uma lista predefinida de opções, nesse caso, do arquivo `wildcards/color.txt`. O curinga será substituído por uma cor aleatória (baseada na seed). Você também pode desativar a aleatoriedade e processar o arquivo de curinga de cima para baixo, ativando a caixa de seleção `Read wildcards in order` no modo Developer Debug.

Curingas podem ser aninhados e combinados, e múltiplos curingas podem ser usados no mesmo prompt (exemplo em `wildcards/color_flower.txt`).

### Processamento de Arrays

Exemplo de prompt: `[[red, green, blue]] flower`

Processado apenas para o prompt positivo.

Processa o array da esquerda para a direita, gerando uma imagem separada para cada elemento do array. Neste caso, seriam geradas 3 imagens, uma para cada cor. Aumente o número de imagens para 3 para gerar todas as variantes.

Arrays não podem ser aninhados, mas múltiplos arrays podem ser usados no mesmo prompt. Suporta LoRAs inline como elementos do array.

### LoRAs Inline

Exemplo de prompt: `flower <lora:sunflowers:1.2>`

Processado apenas para o prompt positivo.

Aplica um LoRA ao prompt. O arquivo LoRA deve estar localizado no diretório `models/loras`.

### Recursos Avançados

[Clique aqui para ver os recursos avançados.](https://github.com/lllyasviel/Fooocus/discussions/117)

### Forks

Abaixo estão alguns forks do Fooocus:

| Forks do Fooocus |
| - |
| [fenneishi/Fooocus-Control](https://github.com/fenneishi/Fooocus-Control) </br>[runew0lf/RuinedFooocus](https://github.com/runew0lf/RuinedFooocus) </br> [MoonRide303/Fooocus-MRE](https://github.com/MoonRide303/Fooocus-MRE) </br> [mashb1t/Fooocus](https://github.com/mashb1t/Fooocus) </br> e outros... |

### Agradecimentos

Muito obrigado a [twri](https://github.com/twri), [3Diva](https://github.com/3Diva) e [Marc K3nt3L](https://github.com/K3nt3L) por criarem estilos adicionais de SDXL disponíveis no Fooocus.

O projeto começou a partir de uma mistura dos códigos do [Stable Diffusion WebUI](https://github.com/AUTOMATIC1111/stable-diffusion-webui) e [ComfyUI](https://github.com/comfyanonymous/ComfyUI).

Também agradecemos [daswer123](https://github.com/daswer123) por contribuir com o recurso de Zoom da Tela!

### Log de Atualizações

O log está disponível [aqui](update_log.md).

### Localização/Tradução/I18N

Você pode colocar arquivos JSON na pasta `language` para traduzir a interface do usuário.

Por exemplo, abaixo está o conteúdo de `Fooocus/language/example.json`:

```json
{
    "Generate": "Gerar",
    "Input Image": "Imagem de Entrada",
    "Advanced": "Avançado",
    "SAI 3D Model": "Modelo SAI 3D"
}
```

Se você adicionar a flag `--language example`, o Fooocus lerá `Fooocus/language/example.json` para traduzir a interface.

Por exemplo, você pode editar a linha final do run.bat do Windows para:

```
.\python_embeded\python.exe -s Fooocus\entry_with_update.py --language example
```

Ou editar run_anime.bat para:

```
.\python_embeded\python.exe -s Fooocus\entry_with_update.py --language example --preset anime
```

Ou editar run_realistic.bat para:

```
.\python_embeded\python.exe -s Fooocus\entry_with_update.py --language example --preset realistic
```

Para uma tradução completa, você pode criar seu próprio arquivo como `Fooocus/language/pt-br.json` e usar a flag `--language pt-br`.

Se nenhum `--language` for especificado e existir `Fooocus/language/default.json`, o Fooocus sempre carregará `Fooocus/language/default.json` para a tradução. Por padrão, esse arquivo `default.json` não existe.


