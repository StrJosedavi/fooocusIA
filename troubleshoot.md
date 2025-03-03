### Erro em Tempo de Execução: CPUAllocator

Veja também a seção: **Swap do Sistema**

### Modelo carregou, depois pausou, depois nada acontece

Veja também a seção: **Swap do Sistema**

### Falha de Segmentação (Segmentation Fault)

Veja também a seção: **Swap do Sistema**

### Abortado

Veja também a seção: **Swap do Sistema**

### Núcleo Descartado (core dumped)

Veja também a seção: **Swap do Sistema**

### Killed

Veja também a seção: **Swap do Sistema**

### ^C, depois sai

Veja também a seção: **Swap do Sistema**

### adm 2816, depois trava

Veja também a seção: **Swap do Sistema**

### Erro de conexão

Veja também a seção: **Swap do Sistema**

### Erro 1006

Veja também a seção: **Swap do Sistema**

### WinError 10060

Veja também a seção: **Swap do Sistema**

### Tempo de leitura esgotado (Read timed out)

Veja também a seção: **Swap do Sistema**

### Nenhum erro, mas o console fecha rapidamente. Não é possível encontrar erro algum.

Veja também a seção: **Swap do Sistema**

### Carregamento de modelo extremamente lento (mais de 1 minuto)

Veja também a seção: **Swap do Sistema**

---

### Swap do Sistema

Todos os problemas acima são causados pelo fato de você não ter Swap do Sistema suficiente.

Certifique-se de ter pelo menos 40GB de Swap do Sistema. Na verdade, nem sempre precisa de tanto, mas 40GB deve ser suficiente para executar o Fooocus com 100% de sucesso.

(Se você tiver mais de 64GB de RAM, *talvez* não precise de Swap, mas não temos 100% de certeza disso.)

Além disso, se seu swap estiver em um HDD, o carregamento do modelo será muito lento. Tente colocar o swap no SSD.

#### Linux/Mac
Se estiver usando Linux ou Mac, siga as instruções oficiais da sua distribuição ou sistema operacional (Ubuntu, CentOS, Mac etc.) para configurar o swap.

#### Windows
Se estiver usando Windows, você pode configurar o Swap aqui:

![swap](https://github.com/lllyasviel/Fooocus/assets/19834515/2a06b130-fe9b-4504-94f1-2763be4476e9)

Se você tiver HDD e SSD, pode testar algumas configurações no passo 7 da imagem para tentar colocar o swap no SSD, acelerando o carregamento do modelo.

#### Observação Importante
O Windows 10/11 automaticamente gerencia o swap para você, então normalmente você não precisa alterar essa configuração. Apenas garanta que há pelo menos 40GB de espaço livre em cada disco. O Windows irá ajustar automaticamente.

Se você obteve o Windows 10/11 de alguma fonte não oficial (como versões modificadas da China ou da Rússia), essas versões podem ter alterado a configuração padrão de swap para promover algo como "Windows Aprimorado". Nesse caso, você pode precisar verificar manualmente se suas configurações de swap estão corretas, conforme a imagem acima.

E não se esqueça: é necessário reiniciar o computador para ativar as mudanças no swap.

---

### MetadataIncompleteBuffer

Veja também a seção: **Modelo Corrompido**

### PytorchStreamReader failed

Veja também a seção: **Modelo Corrompido**

### Modelo Corrompido

Se você receber essa mensagem, seu modelo está corrompido. O Fooocus tentará baixar novamente o modelo, se sua conexão estiver boa. Você também pode baixar manualmente — as URLs e locais de download aparecem no console quando um download é solicitado.

---

### Aviso: 'aten::std_mean.correction' não é suportado no DML

Esse é apenas um aviso, pode ignorar.

---

### Torch não compilado com suporte a CUDA

Você não seguiu o guia de instalação oficial.

Por favor, não confie em tutoriais aleatórios da internet. Siga apenas o guia oficial.

---

### subprocess-exited-with-error

Use Python 3.10.

E novamente, você não seguiu o guia de instalação oficial.

---

### SSL: CERTIFICATE_VERIFY_FAILED

Você está na China? Se sim, desligue VPN e/ou baixe os modelos manualmente.

Se você está fora da China, veja esta busca: [Erro de Certificado SSL](https://www.google.com/search?q=SSL+Certificate+Error). Não há uma solução única, já que a causa pode variar muito.

---

### Erros de Kernel CUDA podem aparecer assincronamente em outras chamadas de API

Poucos dispositivos enfrentam esse problema. Geralmente, você resolve assim:

1. Use a versão oficial mais recente do Fooocus [aqui](https://github.com/lllyasviel/Fooocus#download). (Forks podem causar esse problema.)
2. Atualize seu driver Nvidia para a versão mais recente (idealmente 53X ou superior, não 3XX ou 4XX).
3. Se o erro persistir, pode ser incompatibilidade com CUDA 12. Tente usar CUDA 11 com Xformers. Para isso:
    - Faça backup e exclua a pasta `python_embeded` (ao lado do `run.bat`).
    - Baixe `previous_old_xformers_env.7z` da [página de releases](https://github.com/lllyasviel/Fooocus/releases/tag/release).
    - Extraia e coloque a nova pasta `python_embeded` ao lado do `run.bat`.
    - Execute o Fooocus.
4. Se ainda assim não funcionar, abra uma issue.

---

### Nenhum driver Nvidia encontrado

Atualize seu driver Nvidia.

Se você usa AMD, siga o guia de instalação oficial.

---

### Driver Nvidia muito antigo

Atualize seu driver Nvidia.

---

### Mac muito lento

Alguns usuários de Mac precisam usar `--disable-offload-from-vram` para acelerar o carregamento.

O suporte para Mac é experimental. Considere usar Diffusionbee ou Drawingthings.

---

### Nvidia com 8GB VRAM: CUDA Out Of Memory

Provavelmente é um bug. Por favor, abra uma issue. Veja também [requisitos mínimos](https://github.com/StrJosedavi/fooocusIA/blob/main/readme.md#requisito-m%C3%ADnimo)

---

### Nvidia com 6GB VRAM: CUDA Out Of Memory

Provavelmente é um bug. Por favor, abra uma issue. Veja também [requisitos mínimos](https://github.com/StrJosedavi/fooocusIA/blob/main/readme.md#requisito-m%C3%ADnimo)

---

### Nvidia com 4GB VRAM (com Float16, como RTX 3050): CUDA Out Of Memory

Provavelmente é um bug. Por favor, abra uma issue. Veja também [requisitos mínimos](https://github.com/StrJosedavi/fooocusIA/blob/main/readme.md#requisito-m%C3%ADnimo)

---

### Nvidia com 4GB VRAM (sem Float16, como GTX 960): CUDA Out Of Memory

Suporte para GPUs de 4GB sem Float16 é difícil. Talvez SDXL não funcione. Você pode tentar SD1.5 no Automatic1111. Veja também [requisitos mínimos](https://github.com/StrJosedavi/fooocusIA/blob/main/readme.md#requisito-m%C3%ADnimo)

---

### AMD no Windows: CUDA Out Of Memory

Suporte experimental. Se outros programas rodam SDXL no seu hardware, avise-nos para podermos adicionar suporte. 

No Linux, o suporte AMD é um pouco melhor usando ROCm. Veja também [requisitos mínimos](https://github.com/StrJosedavi/fooocusIA/blob/main/readme.md#requisito-m%C3%ADnimo)

---

### AMD no Linux: CUDA Out Of Memory

Suporte experimental. Se SDXL rodar em outro software no seu hardware, avise-nos. Veja também [requisitos mínimos](https://github.com/StrJosedavi/fooocusIA/blob/main/readme.md#requisito-m%C3%ADnimo)

---

### Flags como --lowvram ou --gpu-only não ajudam?

Remova essas flags se seguiu tutoriais errados. Normalmente essas flags só pioram as coisas.

---

### Fooocus ficou muito lento do nada

Verifique se você não está executando duas instâncias do Fooocus ao mesmo tempo.
