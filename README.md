# Tutorial Para Configurar Sua GPU Para ML no Ubuntu 24.04

## Instalando o CUDA Toolkit

Para baixar a mais recente, procure aqui neste [link](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=24.04&target_type=deb_local)

Lembre-se de instalar a versão usando `installe Type` `deb (local)`

## Configurando o CUDA Toolkit

```bash
sudo apt-get install -y nvidia-open
```

```bash
export PATH=/usr/local/cuda/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
```

Prontinho, agora para habilitar o aprendizado profundo acelerado por GPU no Ubuntu, instale o cuDNN para otimizar o treinamento e a inferência da rede neural. [Clique Aqui](./docs/cuDNN.md)

## Verificando a Instação

Vamos verificar se realmente instalou corretamente

Checando se os drivers estão funcionando corretamente. Irá aparecer no terminal uma tabela com as informações da sua Placa

```bash
nvidia-smi
```

Verificando se o Compilador Cuda do Nvidia está funcionando (NVCC)

```bash
nvcc --version
```

Resultado esperado

```bash
nvcc: NVIDIA (R) Cuda compiler driver 
Copyright (c) 2005-2023 NVIDIA Corporation 
Built on Tue_Jul_11_02:20:44_PDT_2023 
Cuda compilation tools, release 12.0, V12.0.140
Build cuda_12.0.r12.0/compiler.32267302_0
```

caso o resultado seja diferente do esperado, siga estes passos

Corrigindo Instalação

```bash
sudo apt install nvidia-cuda-toolkit
```

Tente novamente com

```bash
nvcc --version
```

Verificando se o software cuda está funcionando corretamente

```bash
lspci | grep -i nvidia
```

Resultado esperado proximo de:

```bash
6:00.0 VGA compatible controller: NVIDIA Corporation GA102GL [A40] (rev a1)

```

```bash
gcc --version
```

Resultado esperado, proximo de:

```bash
gcc (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0 
Copyright (C) 2021 Free Software Foundation, Inc. 
This is free software; see the source for copying conditions.  
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```


## Referências Usadas

[docs.vultr.com-how-to-install-nvidia-cuda-toolkit-on-ubuntu-22-04](https://docs.vultr.com/how-to-install-nvidia-cuda-toolkit-on-ubuntu-22-04?ref=9141995&utm_source=performance-max-latam&utm_medium=paidmedia&obility_id=17096555207&&utm_campaign=LATAM_-_Brazil_-_Performance_Max_-_1001&utm_term=&utm_content=&ref=9141995&gad_source=1&gclid=CjwKCAiA2cu9BhBhEiwAft6IxBK9PnqkmmfKrhHOEHM8rJ-IjKftilWjJNnV-hHVo0J18rbCIFTO6hoCSKUQAvD_BwE)
[docs.vultr.com-how-to-install-nvidia-cudnn](https://docs.vultr.com/how-to-install-nvidia-cudnn-on-ubuntu-22-04)
