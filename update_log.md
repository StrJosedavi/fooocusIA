# [2.5.5](https://github.com/lllyasviel/Fooocus/releases/tag/v2.5.5)

* Correção do problema de inpaint no Colab ao mover uma declaração de importação

# [2.5.4](https://github.com/lllyasviel/Fooocus/releases/tag/v2.5.4)

* Correção da validação para `default_ip_image_*` e `default_inpaint_mask_sam_model`
* Correção da depuração de máscara de aprimoramento em combinação com a ordenação de imagens
* Correção do carregamento de checkpoints e LoRAs ao usar múltiplos diretórios na configuração e depois alternar predefinições

# [2.5.3](https://github.com/lllyasviel/Fooocus/releases/tag/v2.5.3)

* Carregar apenas pesos de arquivos não-safetensors, prevenindo injeção de código malicioso
* Adicionada caixa de seleção para aplicar/redefinir estilos ao descrever imagens, permitindo também múltiplos tipos de conteúdo de descrição

# [2.5.2](https://github.com/lllyasviel/Fooocus/releases/tag/v2.5.2)

* Correção para não adicionar prompt positivo quando os estilos não tinham um marcador `{prompt}` no prompt positivo
* Extensão das configurações para imagens de entrada, veja a lista no [PR](https://github.com/lllyasviel/Fooocus/pull/3382)

# [2.5.1](https://github.com/lllyasviel/Fooocus/releases/tag/v2.5.1)

* Atualização do URL de download no readme
* Aumento da velocidade de carregamento de metadados
* Correção da leitura de metadados de jpeg, jpg e webp (exif)
* Correção do depurador de pré-processador
* Atualização de atributos e adição de seção de recursos de prompt inline ao readme
* Adicionada caixa de seleção, configuração e manipulação para salvar apenas a imagem final aprimorada. Use a configuração `default_save_only_final_enhanced_image`, padrão False.
* Adicionada ordenação de imagens finais quando o aprimoramento está ativado. Use o argumento `--disable-enhance-output-sorting` para desativar.

# [2.5.0](https://github.com/lllyasviel/Fooocus/releases/tag/v2.5.0)

Esta versão inclui várias atualizações de pacotes. Se a atualização automática não funcionar, você pode fazer o seguinte:
1. Abra um terminal na pasta Fooocus (localização do config.txt) e execute `git pull`
2. Atualize os pacotes
   - Windows (instalação via arquivo zip): abra um terminal na pasta Fooocus (localização do config.txt) `..\python_embeded\python.exe -m pip install -r .\requirements_versions.txt` (Windows usando python embutido, método de instalação zip) ou baixe o Fooocus novamente (arquivo zip anexado a esta versão)
   - outros: atualize manualmente os pacotes usando `python.exe -m pip install -r requirements_versions.txt` ou use a imagem docker

---

* Atualização das dependências do python, adição de segment_anything
* Adição do recurso de aprimoramento, que oferece etapas fáceis de refinamento de imagem (semelhante ao adetailer, mas baseado em detecção dinâmica de imagem em vez de modelos específicos de detecção de máscara). Veja a [documentação](https://github.com/lllyasviel/Fooocus/discussions/3281).
* Reescreva o código do worker assíncrono, tornando o código muito mais reutilizável para permitir iterações e melhorar a reutilização
* Melhoria no mascaramento de imagem do GroundingDINO e SAM
* Correção do problema de rastreamento do contador de versão do tensor de inferência para o GroundingDINO após usar o Aprimoramento (veja [discussão](https://github.com/lllyasviel/Fooocus/discussions/3213))
* Movimento das caixas de seleção "Enable Mask Upload" e "Invert Mask When Generating" do Modo de Depuração do Desenvolvedor para Inpaint ou Outpaint
* Adição de cache persistente de modelo para metadados. Use `--rebuild-hash-cache X` (X = int, número de núcleos da CPU, padrão todos) para reconstruir manualmente o cache para todos os hashes não armazenados em cache
* Renomeação de `--enable-describe-uov-image` para `--enable-auto-describe-image`, agora também funciona para upload de imagem de aprimoramento
* Renomeação da caixa de seleção "Enable Mask Upload" para "Enable Advanced Masking Features" para melhor indicar o recurso de geração automática de máscara
* Obtenha o caminho do arquivo do modelo de upscale chamando `downloading_upscale_model()` para garantir que o modelo exista
* Renomeação dos títulos das abas e traduções de singular para plural
* Renomeação de documento para documentação
* Atualização dos modelos padrão para as versões mais recentes
  * animaPencilXL_v400 => animaPencilXL_v500
  * DreamShaperXL_Turbo_dpmppSdeKarras => DreamShaperXL_Turbo_v2_1
  * SDXL_FILM_PHOTOGRAPHY_STYLE_BetaV0.4 => SDXL_FILM_PHOTOGRAPHY_STYLE_V1
* Adição de predefinição para pony_v6 (usando ponyDiffusionV6XL)
* Adição do estilo "Fooocus Pony"
* Adição do amostrador de reinício ([paper](https://arxiv.org/abs/2306.14878))
* Adição da opção de configuração para `default_inpaint_engine_version`, define o motor de inpaint para pony_v6 e playground_v2.5 como None para resultados melhores (incompatível com o motor de inpaint)
* Adição da funcionalidade de editor de imagem para upload de máscara (igual ao inpaint, agora redimensiona corretamente e permite a criação de máscaras mais detalhadas)

# [2.4.3](https://github.com/lllyasviel/Fooocus/releases/tag/v2.4.3)

* Correção do setter de alphas_cumprod para o amostrador TCD
* Adição de parser para strings de variáveis de ambiente para tipos de valor de configuração esperados, permitindo a substituição de todas as chaves de configuração não-path

# [2.4.2](https://github.com/lllyasviel/Fooocus/releases/tag/v2.4.2)

* Correção de alguns pequenos bugs (agendador TCD quando gamma é 0, chown no Dockerfile, atualização de argumentos de cmd no readme, tradução para proporções de aspecto, vae padrão após recarregamento de arquivo)
* Correção da substituição de LoRA de desempenho quando os dados são carregados do histórico de log e prompt inline
* Adição de suporte e predefinição para playground v2.5 (funciona apenas com desempenho Quality ou Speed, use com o agendador edm_playground_v2)
* Tornar as caixas de texto (incluindo prompt positivo) redimensionáveis
* Ocultar imagens intermediárias quando o desempenho do Gradio poderia atrapalhar o processo de geração (Extreme Speed, Lightning, Hyper-SD)

# [2.4.1](https://github.com/lllyasviel/Fooocus/releases/tag/v2.4.1)

* Correção de alguns pequenos bugs (por exemplo, ajuste do valor padrão de clip skip de 1 para 2, adição de verificação de tipo para a função de atualização de proporções de aspecto js)
* Adição de construção automatizada de docker ao enviar para main, marcado com `edge`. Veja [imagens docker disponíveis](https://github.com/lllyasviel/Fooocus/pkgs/container/fooocus).

# [2.4.0](https://github.com/lllyasviel/Fooocus/releases/tag/v2.4.0)

* Alteração dos elementos da aba de configurações para serem mais compactos
* Adição de controle deslizante para clip skip
* Adição de seleção para VAE personalizado
* Adição de novo estilo "Random Style"
* Atualização do modelo de anime padrão para animaPencilXL_v310
* Adição de botão para reconectar a UI após o Fooocus crashar sem precisar reconfigurar tudo novamente (sem necessidade de recarregar a página)
* Adição de desempenho "hyper-sd" (baseado em [Hyper-SDXL 4 step LoRA](https://huggingface.co/ByteDance/Hyper-SD/blob/main/Hyper-SDXL-4steps-lora.safetensors))
* Adição do agendador [AlignYourSteps](https://research.nvidia.com/labs/toronto-ai/AlignYourSteps/) da Nvidia, veja 
* Adição do amostrador e agendador [TCD](https://github.com/jabir-zheng/TCD) (baseado em sgm_uniform)
* Adição de censura de imagens NSFW (desativa a visualização intermediária de imagens durante a geração). Defina o valor de configuração `default_black_out_nsfw` como True para ativar sempre.
* Adição do argumento `--enable-describe-uov-image` para descrever automaticamente imagens enviadas para upscaling
* Adição de referências de prompt inline para lora com suporte a subpastas, exemplo de prompt: `colorful bird <lora:toucan:1.2>`
* Adição de recomendação de tamanho e proporção de aspecto na descrição de imagem
* Adição de seletor de cor para o pincel de inpaint, útil quando a imagem e o pincel de máscara têm a mesma cor
* Adição de construção automatizada de imagem Docker usando Github Actions em cada versão.
* Adição de prompts brutos completos aos logs de histórico
* Alteração da propriedade do código de @lllyasviel para @mashb1t para notificação automatizada de problemas / MR

# [2.3.1](https://github.com/lllyasviel/Fooocus/releases/tag/2.3.1)

* Remoção do prompt positivo do prefixo de anime para não redefinir o prompt após alternar predefinições
* Correção do número da imagem ser redefinido para 1 ao alternar predefinição, agora não redefine mais
* Correção do cálculo de dimensão de outpainting ao estender para esquerda/direita
* Correção da compatibilidade de LoRA para LoRAs no esquema de metadados a1111

# [2.3.0](https://github.com/lllyasviel/Fooocus/releases/tag/2.3.0)

* Adição de desempenho "lightning" (baseado em [SDXL-Lightning 4 step LoRA](https://huggingface.co/ByteDance/SDXL-Lightning/blob/main/sdxl_lightning_4step_lora.safetensors))
* Adição de seleção de predefinição à UI, desative com o argumento `--disable-preset-selection`. Use `--always-download-new-model` para baixar modelos ausentes ao alternar predefinições.
* Melhoria na consistência da troca de rosto ao alternar mais tarde no processo para (sintético) refinador
* Adição de limpeza de caminho temporário na inicialização
* Adição de suporte para subdiretórios de wildcards
* Adição de layout de 2 colunas rolável para estilos para melhor estrutura
* Melhoria nas necessidades de recursos do Colab para instâncias T4 (padrão), testado positivamente com todos os recursos de prompt de imagem
* Melhoria na predefinição de anime, agora usa o estilo `Fooocus Semi Realistic` em vez de `Fooocus Negative` (imagens com menos aparência molhada)

# [2.2.1](https://github.com/lllyasviel/Fooocus/releases/tag/2.2.1)

* Correção de alguns pequenos bugs (por exemplo, grade de imagem, upscale rápido 2x, largura do peso LoRA no Firefox)
* Permitir pesos de prompt na sintaxe de array
* Adição de substituição de etapas e esquema de metadados ao log de histórico

# [2.2.0](https://github.com/lllyasviel/Fooocus/releases/tag/2.2.0)

* Isolamento de cada geração de imagem para permitir verdadeiramente o uso multi-usuário
* Adição de suporte a array, altera o prompt principal ao aumentar o número de imagem. Sintaxe: `[[red, green, blue]] flower`
* Adição de metadados opcionais às imagens, permitindo que você as regenere e modifique posteriormente com os mesmos parâmetros
* Agora suporta geração nativa de imagens PNG, JPG e WEBP
* Adição de suporte a Docker

# [2.1.865](https://github.com/lllyasviel/Fooocus/releases/tag/2.1.865)

* Várias correções de bugs
* Adição de autenticação ao --listen

# 2.1.864

* Nova lista de modelos. Veja também discussões.

# 2.1.861 (atualização solicitada)

(21 de dezembro de 2023) Olá a todos, a atualização de recursos do Fooocus será pausada por cerca de duas ou três semanas porque temos outras tarefas. Vejo vocês em breve e voltaremos em meados ou final de janeiro. No entanto, você ainda pode ver atualizações se outros colaboradores estiverem corrigindo bugs ou resolvendo problemas.

* Mostrar prévia da imagem no Estilo ao passar o mouse.

# 2.1.860 (atualização solicitada)

* Permitir upload de máscara de inpaint no modo de desenvolvedor.

# 2.1.857 (atualização solicitada)

* Começar a suportar GPU AMD de 8GB no Windows.

# 2.1.854

* Adição de um botão para copiar parâmetros para a área de transferência no log.
* Permitir que os usuários carreguem parâmetros diretamente colando-os no prompt.

# 2.1.853

* Adição dos estilos de Marc K3nt3L. Obrigado [Marc K3nt3L](https://github.com/K3nt3L)!

# 2.1.852

* Novo Sistema de Log: O sistema de log agora usa tabelas. Se isso estiver quebrando alguma extensão de navegador ou desenvolvimento de javascript, veja também [use a versão anterior](https://github.com/lllyasviel/Fooocus/discussions/1405).

# 2.1.846

* Muitos usuários relataram que a qualidade da imagem é diferente da 2.1.824. Revisamos todos os códigos e corrigimos vários problemas de precisão na 2.1.846.

# 2.1.843

* Muitas melhorias no Canvas. Obrigado ao autor do CanvasZoom!

# 2.1.841

* Manutenção do backend.
* Correção de alguns possíveis congelamentos após incompatibilidade de modelo.
* Correção de crash quando cfg=1 ao usar a predefinição de anime.
* Adição de algumas diretrizes para solucionar o problema "erros de kernel CUDA assincronamente".
* Correção do problema de dispositivo de inpaint no modo `--always-gpu`.

# 2.1.839

* Manutenção de alguns códigos de computação no backend para eficiência.
* Adição de uma nota sobre Mudança de Quebra de Seed.

**Mudança de Quebra de Seed**: Observe que 2.1.825-2.1.839 é uma mudança de quebra de seed. O ponto flutuante de computação foi alterado e algumas seeds podem dar resultados ligeiramente diferentes. A mudança menor em 2.1.825-2.1.839 não influencia a qualidade da imagem. Veja também [use a versão anterior](https://github.com/lllyasviel/Fooocus/discussions/1405).

# 2.1.837

* Correção de alguns problemas relacionados à precisão.

# 2.1.836

* Evitar download do tokenizador blip do torch hub

# 2.1.831

* Input Image -> Describe (Midjourney Describe)

# 2.1.830

* Suporte a SegmindVega.

# 2.1.829

* Mudança da árvore SDE para CPU em AMD/DirectMl para evitar possíveis problemas.

# 2.1.828

* Permitir desativar a análise do gradio.
* Usar tabela html no log.
* Correção de alguns problemas de SSL.

# 2.1.826

* Novo backend.
* Suporte a FP8 (veja também a nova lista de flags de cmd no Readme, por exemplo, --unet-in-fp8-e4m3fn e --unet-in-fp8-e5m2).
* Correção de alguns problemas de MPS.
* Suporte a GLoRA.
* Agendador Turbo.

# 2.1.823

(26 de novembro de 2023) Olá a todos, a atualização de recursos do Fooocus será pausada por cerca de duas ou três semanas porque temos outras tarefas. Vejo vocês em breve e voltaremos em meados de dezembro. No entanto, você ainda pode ver atualizações se outros colaboradores estiverem corrigindo bugs ou resolvendo problemas.

* Correção de alguns problemas potenciais quando LoRAs têm chaves de clip e o usuário deseja carregar esses LoRAs para refinadores.

# 2.1.822

* Novo sistema de inpaint (fim do teste beta de inpaint).

# 2.1.821

* Nova UI para LoRAs.
* Sistema de predefinições aprimorado: normalização de chaves de predefinições e nomes de arquivos.
* Sistema de sessão aprimorado: agora vários usuários podem usar um Fooocus ao mesmo tempo sem ver os resultados dos outros.
* Melhoria em alguns cálculos relacionados à precisão do modelo.
* Sistema de carregamento de configuração aprimorado com impressões amigáveis ao usuário.

# 2.1.820

* Suporte a "--disable-image-log" para evitar a gravação de imagens e logs no disco rígido.

# 2.1.819

* Permitir desativar a pré-visualização nas ferramentas de desenvolvedor.

# 2.1.818

* Correção do carregamento de LoRA de predefinição falhar quando o peso é exatamente um.

# 2.1.817

* Suporte a "--theme dark" e "--theme light".
* Adição de arquivos de predefinição "default" e "lcm", essas predefinições existem, mas não criarão arquivos de inicialização (não serão expostas aos usuários) para manter a entrada limpa. O "--preset lcm" é equivalente a selecionar "Extreme Speed" na UI, mas provavelmente facilitará a implantação de alguns serviços online.

# 2.1.815

* Múltiplos LoRAs em predefinição.

# 2.1.814

* Permitir o uso de predefinições anteriores do SAI SDXL oficial modificando os argumentos para '--preset sai'. ~Observe que essa predefinição definirá o motor de inpaint de volta para a versão anterior v1 para obter os mesmos resultados de antes. Para alterar o motor de inpaint para v2.6, use as ferramentas de desenvolvedor -> motor de inpaint -> v2.6.~ (atualização: não é mais necessário após alguns testes.)

# 2.1.813

* Permitir que a predefinição defina o motor de inpaint padrão.

# 2.1.812

* Permitir que a predefinição defina o desempenho padrão.
* Amostrador heunpp2.

# 2.1.810

* Adição de dicas ao config_modification_tutorial.txt
* Remoção de proporções de aspecto hackeadas pelo usuário nos modelos de inglês I18N, mas ainda será lido como antes.
* Correção de alguns problemas de ordenação de estilos novamente (talvez deva tentar o Gradio 4.0 mais tarde).
* Atualização dos modelos de inglês I18N com mais chaves.

# 2.1.809

* Correção de alguns problemas de ordenação.

# 2.1.808

* Proporções de aspecto agora mostram proporções de aspecto.
* Adição de pesquisa de estilos.
* Adição de ordenação/favoritos de estilos.

# 2.1.807

* Clique na imagem para vê-la em tela cheia.

# 2.1.806

* Correção de alguns problemas de LoRA relacionados ao clip.

# 2.1.805

* UI responsiva para telas pequenas.
* Adição de pular pré-processador nas ferramentas de desenvolvedor.

# 2.1.802

* Motor de inpaint padrão alterado para v2.6. Você ainda pode usar o motor de inpaint v1 nas ferramentas de desenvolvedor.
* Correção de alguns problemas de VRAM.

# 2.1.799

* Adição do modo de desempenho 'Extreme Speed' (baseado em LCM). As configurações complicadas anteriores não são mais necessárias.

# 2.1.798

* Adição do agendador LCM - LCM pode precisar definir tanto o amostrador quanto o agendador para "lcm". Além disso, veja a descrição nos logs da 2.1.782.

# 2.1.797

* Correção de alguns problemas de dependência com facexlib e filterpy.

# 2.1.793

* Adição de muitos scripts javascript para melhorar a experiência do usuário. Agora usuários com telas pequenas sempre verão o canvas completo sem precisar rolar.

# 2.1.790

* Troca de rosto (alinhado com o InsightFace do Midjourney): Input Image -> Image Prompt -> Advanced -> FaceSwap
* O desempenho é super alto. Use com cuidado e nunca use em nada ilegal!
* Esta implementação cortará rostos para você e você NÃO precisa cortar rostos antes de alimentar imagens no Fooocus. (Se você anteriormente cortava rostos manualmente de imagens para outros softwares, não precisa mais fazer isso no Fooocus.)

# 2.1.788

* Correção de alguns problemas matemáticos em versões anteriores.
* Motor de inpaint v2.6 junta-se ao teste beta dos modelos de inpaint do Fooocus. Use-o nas ferramentas de desenvolvedor -> motor de inpaint -> v2.6.

# 2.1.785

* O `user_path_config.txt` foi descontinuado desde a 2.1.785. Se você estiver usando agora, use o novo `config.txt`. Veja também a nova documentação no Readme.
* Os caminhos no `user_path_config.txt` ainda serão carregados em versões recentes, mas serão removidos em breve.
* Usamos um método muito amigável ao usuário para transferir automaticamente suas configurações de caminho do `user_path_config.txt` para o `config.txt` e geralmente você não precisa fazer nada.
* O novo `config.txt` nunca salvará valores padrão, para que as alterações de valores padrão nos scripts não sejam impedidas por arquivos de configuração antigos.

# 2.1.782

A versão 2.1.782 é principalmente uma atualização para um novo sistema de LoRA que suporta LoRAs tanto do SDXL quanto do SD1.5.

Agora, quando você carrega um LoRA, as seguintes coisas acontecerão:

1. Tente carregar o LoRA no modelo base, se falhar (incompatibilidade de modelo), tente carregar o LoRA no refinador.
2. Tente carregar o LoRA no refinador, se falhar (incompatibilidade de modelo), não faça nada.

Dessa forma, o Fooocus 2.1.782 pode se beneficiar de todos os modelos e LoRAs do CivitAI com os ecossistemas SDXL e SD1.5, usando o algoritmo único de troca do Fooocus, para alcançar resultados de qualidade extremamente alta (embora a configuração padrão já seja de alta qualidade), especialmente em alguns casos de uso de anime, se os usuários realmente quiserem brincar com todas essas coisas.

Recentemente, a comunidade também desenvolveu LoRAs LCM. Os usuários podem usá-los definindo o amostrador como 'LCM', o agendador como 'sgm_uniform' (Atualização na 2.1.798: o agendador também deve ser "lcm"), a substituição forçada da etapa de amostragem como 4 a 8 e a orientação CFG como 1.0, nas ferramentas de desenvolvedor. Não se esqueça de alterar o peso do LoRA LCM para 1.0 (muitas pessoas esquecem disso e relatam falhas). Além disso, defina o refinador como None. Se o feedback do LCM na comunidade de artistas for bom (não o feedback na comunidade de programadores do Stable Diffusion), o Fooocus pode adicionar alguns outros atalhos no futuro.

# 2.1.781

(26 de outubro de 2023) Olá a todos, a atualização de recursos do Fooocus será (realmente, realmente, desta vez) pausada por cerca de duas ou três semanas porque realmente temos outras tarefas. Obrigado pela paixão de todos (e, de fato, continuamos atualizando mesmo após o anúncio de pausa da semana passada, devido a muitos feedbacks excelentes) - vejo vocês em breve e voltaremos em meados de novembro. No entanto, você ainda pode ver atualizações se outros colaboradores estiverem corrigindo bugs ou resolvendo problemas.

* Desativar o refinador para acelerar quando novos usuários definirem o mesmo modelo para base e refinador.

# 2.1.779

* Desativar a grade de imagens por padrão porque muitos usuários relatam problemas de desempenho. Por exemplo, https://github.com/lllyasviel/Fooocus/issues/829 e assim por diante. A grade de imagens causará problemas quando o disco rígido do usuário não for super rápido ou quando a conexão com a internet não for muito boa (por exemplo, rodando remotamente). A opção foi movida para as ferramentas de desenvolvedor se os usuários quiserem usá-la. Vamos dar uma olhada nisso mais tarde.

# 2.1.776

* Suporte a Ctrl+Up/Down Arrow para alterar os pesos de ênfase do prompt.

# 2.1.750

* Nova UI: agora você pode obter cada imagem durante a geração.

# 2.1.743

* Melhoria no GPT2 ao remover alguns tokens que podem corromper estilos.

# 2.1.741

Atualizações de Estilo:

* "Default (Slightly Cinematic)" foi renomeado para "Fooocus Cinematic".
* "Default (Slightly Cinematic)" foi removido das seleções de estilo padrão.
* Adição de "Fooocus Sharp". Este estilo combina muitos prompts do CivitAI que reduzem a borrão do SDXL e melhoram a nitidez de uma forma relativamente natural.
* Adição de "Fooocus Enhance". Este estilo usa principalmente os [prompts negativos padrão do JuggernautXL](https://civitai.com/models/133005) muito populares e algumas outras palavras de aprimoramento. O prompt negativo do JuggernautXL provou ser muito eficaz em muitos posts recentes de imagens no CivitAI para melhorar o JuggernautXL e muitos outros modelos.
* "Fooocus Sharp", "Fooocus Enhance" e "Fooocus V2" tornam-se o novo conjunto padrão de estilos.
* Remoção do texto padrão na área de entrada de "prompt negativo", pois não é mais necessário.
* Você pode reproduzir resultados anteriores usando "Fooocus Cinematic".
* "Fooocus Sharp" e "Fooocus Enhance" podem passar por revisões menores em atualizações futuras.

# 2.1.739

* Adição de suporte para autenticação no modo --share (via auth.json).

# 2.1.737

* Permitir personalização de resoluções na configuração.

Modificar isso piorará os resultados se você não entender como o Positional Encoding funciona.

Você foi avisado.

Se você não sabe por que os números devem ser transformados com muitas funções Sin e Cos (sim, aquelas funções trigonométricas que você aprende no ensino fundamental) antes de serem alimentados ao SDXL, não encorajamos você a mudar isso - você se tornará uma vítima do Positional Encoding. É provável que você sofra com uma ferramenta fácil de falhar, em vez de obter mais controle.

O conhecimento que você ganhou do SD1.5 (por exemplo, números de resolução divididos por 8 ou 64 são bons o suficiente para a UNet) não funciona no SDXL. O SDXL usa Positional Encoding. O SD1.5 não usa Positional Encoding. Eles são completamente diferentes.

O conhecimento que você ganhou de outros recursos (por exemplo, resoluções em torno de 1024 são boas o suficiente para o SDXL) está errado. O SDXL usa Positional Encoding. As pessoas que dizem "todas as resoluções em torno de 1024 são boas" não entendem o que é Positional Encoding. Elas não estão intencionalmente enganando. Elas simplesmente não estão cientes do fato de que o SDXL está usando Positional Encoding.

O número 1152 deve ser exatamente 1152, não 1152-1, não 1152+1, não 1152-8, não 1152+8. O número 1152 deve ser exatamente 1152. Apenas pesquise no Google o que é Positional Encoding.

Novamente, se você não entende como o Positional Encoding funciona, simplesmente não mude os números de resolução.

# 2.1.735

* Correção de muitos problemas relacionados ao autocast do torch.

# 2.1.733

* Aumento do intervalo de seed aleatório permitido.

# 2.1.728

* Correção de alguns problemas numéricos potenciais desde a 2.1.723

# 2.1.723

* Melhoria no Fooocus Anime ao usar uma formulação de refinamento SD1.5 melhor.

# 2.1.722

* Agora é possível traduzir 100% de todos os textos na UI.

# 2.1.721

* Adição de language/en.json para facilitar a tradução.

# 2.1.720

* Adição de Canvas Zoom ao canvas de inpaint
* Correção do problema de a imagem ser cortada na UI quando a imagem enviada é muito larga.

# 2.1.719

* I18N

# 2.1.718

* Correção do tratamento de traço em nomes de wildcards, mais wildcards (extended-color).

# 2.1.717

* Correção da exibição de prompts de várias linhas no Log Privado.

# 2.1.716

* Adição de suporte para wildcards aninhados, mais wildcards (flor, color_flower).

# 2.1.714

* Correção de problemas de resolução.

# 2.1.712

* Limpeza do Log Privado (a maioria dos usuários não precisará de informações sobre prompts brutos).

# 2.1.711

* Adição de mais informações sobre prompts no Log Privado.
* Wildcards no prompt negativo agora usam seeds diferentes.

# 2.1.710

* Adição de informações sobre o uso de wildcards no log do console.

# 2.1.709

* Permitir alteração dos valores padrão da caixa de seleção avançada e do número de imagens.

# 2.1.707

* Atualização do Gradio para v3.41.2.

# 2.1.703

* Correção de muitos problemas anteriores relacionados ao inpaint.

# 2.1.702

* Correção da leitura de prompt negativo vazio na configuração (não deve se tornar None).

# 2.1.701

* Atualização do nó FreeU para v2 (resultados menos exagerados).

# 2.1.699

* Desativação do gerenciamento inteligente de memória (resolve alguns problemas de memória).

# 2.1.698

* Adição de suporte para carregar arquivos de modelo de subpastas.

# 2.1.696

* Melhoria na implementação de wildcards (usar o mesmo wildcard várias vezes agora retornará valores diferentes).

**(18 de outubro de 2023) Novamente, a atualização de recursos do Fooocus será pausada por cerca de duas ou três semanas porque temos outras tarefas - voltaremos no início ou meados de novembro. No entanto, você ainda pode ver atualizações se outros colaboradores estiverem corrigindo bugs ou resolvendo problemas.**

# 2.1.695 (correção de bug de emergência solicitada)

* Redução de 3,4 GB de uso de RAM ao trocar o modelo base.
* Redução de 372 MB de uso de VRAM na decodificação VAE após usar o modelo de controle no prompt de imagem.
* Observe que o ComfyUI oficial (d44a2de) ficará sem VRAM ao usar sdxl e control-lora em 2060 6GB que não suporta float16 na resolução 1024. O Fooocus 2.1.695 conseguiu gerar imagens sem OOM usando exatamente os mesmos dispositivos.

(17 de outubro de 2023) Anúncio de pausa nas atualizações.

# 2.1.693

* Colocando estilos personalizados antes de estilos predefinidos.
* Evitando a confusão entre a predefinição Fooocus Anime e o estilo Fooocus Anime (o estilo Fooocus Anime foi renomeado para Fooocus Masterpiece porque não torna as imagens com aparência de anime se não for usado com a predefinição Fooocus Anime).
* Correção de alguns pequenos bugs na ênfase de vírgulas no prompt da predefinição Fooocus Anime.
* Suporte e documentação da gramática de embedding (e gramática de wildcards).
* Esta versão é uma versão relativamente estável e muitos recursos estão determinados agora.

# 2.1.687

* Adição de suporte para wildcards (usando arquivos da pasta wildcards - tente prompts como `__color__ sports car` com seeds diferentes).

# 2.1.682

* Adição de suporte para estilos personalizados (carregados de arquivos JSON colocados na pasta sdxl_styles).

# 2.1.681

* Adição de suporte para atalho de geração (CTRL+ENTER).
* Adição de suporte para gerar para sempre (botão direito no botão Gerar).
* Adição de suporte para tocar som quando a geração terminar ('notification.ogg' ou 'notification.mp3').

# 2.1.62

* Sistema de predefinições. Adição de suporte a anime e realista.

# 2.1.52

* Remoção da dependência pygit2 (espera-se atualização automática) para que as pessoas nunca tenham problemas de permissão negada.

# 2.1.50

* Começo do suporte a sd1.5 como refinador. Este método escala sigmas dada a escala latente SD15/Xl e provavelmente é a maneira mais correta de fazer isso. Vou escrever uma discussão em breve.

# 2.1.25

Suporte a AMD no Linux e Windows.

# 2.1.0

* Prompt de Imagem
* Conclusão da tabela "Moving from Midjourney"

# 2.0.85

* Aceleração Novamente

# 2.0.80

* Melhoria no agendamento da orientação ADM e imitação CFG para melhor qualidade visual em domínio de alta frequência e pequenos objetos.

# 2.0.80

* Retrabalho de muitos patches e alguns detalhes da UI.
* Aceleração do processamento.
* Mudança do Colab para um branch independente.
* Implementação da Escala CFG e correção TSNR quando CFG é maior que 10.
* Implementação do Modo de Desenvolvedor com mais opções para depuração.

### 2.0.72

(21 de setembro de 2023) A atualização de recursos do Fooocus será pausada por cerca de duas ou três semanas porque temos alguns eventos e viagens - voltaremos no início ou meados de outubro.

### 2.0.72

* Permitir que os usuários escolham o caminho dos modelos.

### 2.0.65

* Modelo de inpaint lançado.

### 2.0.50

* Variação/Upscale (Barra de Ferramentas do Midjourney) implementada.

### 2.0.16

* Sistema de memória virtual implementado. Agora o Colab pode rodar tanto o modelo base quanto o refinador com 7,8 GB de RAM + 5,3 GB de VRAM, e nunca trava.
* Se você for sortudo o suficiente para ler esta linha, lembre-se que o ComfyUI não pode fazer isso. É muito razoável que o Fooocus seja mais otimizado porque só precisa lidar com um pipeline fixo, mas o ComfyUI precisa considerar pipelines arbitrários.
* Mas se considerarmos apenas a otimização dessa carga de trabalho fixa, após a 2.0.16, o Fooocus se tornou o aplicativo SDXL mais otimizado, superando o ComfyUI.

### 2.0.0

* V2 lançada.
* Reescreva completamente o pipeline de processamento de texto (maior qualidade de imagem e compreensão de prompt).
* Suporte a multi-estilo.
* Em 100 testes (prompts escritos pelo ChatGPT), os resultados padrão do V2 superaram os resultados padrão do V1 em 87 casos, avaliados por dois humanos.
* Em 100 testes (prompts escritos pelo ChatGPT), a compreensão de prompt do V2 superou a compreensão de prompt do V1 em 81 casos, avaliados por dois humanos, tanto na configuração padrão quanto no modo multi/único estilo.
* Como o número acima é superior a 80%, consideramos isso uma grande atualização e pulamos diretamente para 2.0.0.
* Algumas outras coisas foram renomeadas.

### 1.0.67

* Uso de ponderação dinâmica e pesos mais baixos para expansão de prompt.

### 1.0.64

* Correção de um pequeno problema de OOM.

### 1.0.62

* Mudança da expansão de prompt para o modo de sufixo para melhor equilíbrio entre semântica e estilo (e depuração).

### 1.0.60

* Ajuste do equilíbrio entre estilo e Expansão de Prompt.

### 1.0.56

* Começo do uso de divisão mágica.

### 1.0.55

* Pequenas alterações na Expansão de Prompt.

### 1.0.52

* Redução da corrupção semântica da Expansão de Prompt.

### 1.0.51

* Aceleração da Expansão de Prompt um pouco.

### 1.0.50

* Expansão de prompt e um "Modo Raw" para desativá-la (semelhante ao "raw" do Midjourney).

### 1.0.45

* Retrabalho do SAG, remoção de patch desnecessário
* Retrabalho de filtros anisotrópicos para computação mais rápida.
* Substituição por filtro anisotrópico guiado para menos distorção.

### 1.0.41

(A atualização do Fooocus será pausada por um período de tempo para o sd-webui 1.6.X do AUTOMATIC1111, e alguns recursos também serão implementados como extensões do webui)

### 1.0.40

* Comportamentos revertidos para 1.0.36 novamente (etapas do refinador). O 1.0.36 é muito perfeito e típico; superar o 1.0.36 é simplesmente impossível.

### 1.0.39

* Reversão de mudanças instáveis entre 1.0.37 e 1.0.38.
* Aumento das etapas do refinador para metade das etapas de amostragem.

### 1.0.36

* Mudança do kernel gaussiano para kernel anisotrópico.

### 1.0.34

* Restauração de seed aleatória.

### 1.0.33

* Ocultar itens no log quando as imagens são removidas.

### 1.0.32

* Log privado do Fooocus

### 1.0.31

* Correção de erro de digitação e UI.

### 1.0.29

* Adição do bloco "Advanced->Advanced->Advanced" para desenvolvimento futuro.

### 1.0.29

* Correção do problema de supercozimento na 1.0.28

### 1.0.28

* SAG implementado

### 1.0.27

* Correção de pequeno problema no css da caixa de texto

### 1.0.25

* suporte a sys.argv --listen --share --port

### 1.0.24

* Caixa de texto de entrada mais alta.

### 1.0.23

* Adição de algumas dicas no linux após o início da UI para que os usuários saibam que o aplicativo não falhou.

### 1.0.20

* Suporte a linux.

### 1.0.20

* Aceleração do codificador de texto.

### 1.0.20

* Reescreva a UI para usar códigos assíncronos: (1) para início mais rápido e (2) para melhor pré-visualização ao vivo.
* Remoção da dependência do opencv
* Planejamento para suportar Linux em breve

### 1.0.19

* Desbloqueio para permitir a mudança de modelo.

### 1.0.17

* Mudança do modelo padrão para SDXL-1.0-vae-0.9. (Isso significa que os modelos serão baixados novamente, mas devemos fazer isso o mais cedo possível para que todos os novos usuários só precisem baixar uma vez. Realmente desculpe pelos usuários do dia 0. Mas, francamente, isso não é muito tarde, considerando que o projeto está publicamente disponível há menos de 24 horas - se já fosse uma semana, preferiríamos truques mais leves para atualizar.)

### 1.0.16

* Implementação da pasta "Fooocus/outputs" para salvar os resultados do usuário.
* Ignorar erros do cv2 quando a pré-visualização falhar.
* Menção ao futuro suporte a AMD no Readme.
* Criação deste log.

### 1.0.15

Disponível publicamente.

### 1.0.0

Versão inicial.
