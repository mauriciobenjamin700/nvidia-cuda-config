# Tutorial Para Configurar Sua GPU Para ML no Ubuntu 24.04

## Instalando o CUDA Toolkit

Você pode baixar usando o comando a baixo, mas observe que ele irá baixar a versão 12.0.1, que pode não ser a mais recente. Para baixar a mais recente, procure aqui neste [link](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=24.04&target_type=runfile_local)

```bash
wget https://developer.download.nvidia.com/compute/cuda/12.8.0/local_installers/cuda_12.8.0_570.86.10_linux.run
```

Em seguida, execute o arquivo que foi baixado

```bash
sudo sh cuda_12.8.0_570.86.10_linux.run
```

Quando solicitado, leia o Contrato de Licença do Usuário Final (EULA), digite `accept` e pressione `Enter` para acessar as opções de instalação.

Na lista de opções de instalação, desmarque marque todas as opções.

Vá até a opção Instalar e pressione `Enter` para iniciar o processo de instalação

Quando finalizar, você irá ver algo próximo a isso

```bash
 ===========
 = Summary =
 ===========

 Driver:   Not Selected
 Toolkit:  Installed in /usr/local/cuda-12.0/

 Please make sure that
  -   PATH includes /usr/local/cuda-12.0/bin
  -   LD_LIBRARY_PATH includes /usr/local/cuda-12.0/lib64, or, add /usr/local/cuda-12.0/lib64 to /etc/ld.so.conf and run ldconfig as root

 To uninstall the CUDA Toolkit, run cuda-uninstaller in /usr/local/cuda-12.0/bin
 ***WARNING: Incomplete installation! This installation did not install the CUDA Driver. A driver of version at least 525.00 is required for CUDA 12.0 functionality to work.
 To install the driver using this installer, run the following command, replacing <CudaInstaller> with the name of this run file:
     sudo <CudaInstaller>.run --silent --driver

 Logfile is /var/log/cuda-installer.log
```

## Configurando o CUDA Toolkit

Adicionaremos o `cuda` ao path do sistema. Lembrando de trocar `cuda-12.0` pela versão que esta usando, e troque `SEU_NOME_DE_USUARIO` pelo nome de usuário da sua maquina

```bash
echo "export PATH=/usr/local/cuda-12.0/bin${PATH:+:${PATH}}" >> /home/SEU_NOME_DE_USUARIO/.bashrc
```

Adicionaremos a biblioteca `cuda toolkit` ao path das bibliotecas (`LD_LIBRARY_PATH`). Lembrando de trocar `cuda-12.0` pela versão que esta usando, e troque `SEU_NOME_DE_USUARIO` pelo nome de usuário da sua maquina

```bash
echo "export LD_LIBRARY_PATH=/usr/local/cuda-12.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}" >> /home/SEU_NOME_DE_USUARIO/.bashrc
```

O comando LD_LIBRARY_PATH acima atualiza o carregador de link do kit de ferramentas CUDA com a localização das bibliotecas compartilhadas

Agora basta que ative as alterações nas variáveis ​​de ambiente

```bash
source /home/pythonuser/.bashrc
```

Prontinho, agora para habilitar o aprendizado profundo acelerado por GPU no Ubuntu, instale o cuDNN para otimizar o treinamento e a inferência da rede neural. [Clique Aqui](./docs/cuDNN.md)

## Referências Usadas

[docs.vultr.com-how-to-install-nvidia-cuda-toolkit-on-ubuntu-22-04](https://docs.vultr.com/how-to-install-nvidia-cuda-toolkit-on-ubuntu-22-04?ref=9141995&utm_source=performance-max-latam&utm_medium=paidmedia&obility_id=17096555207&&utm_campaign=LATAM_-_Brazil_-_Performance_Max_-_1001&utm_term=&utm_content=&ref=9141995&gad_source=1&gclid=CjwKCAiA2cu9BhBhEiwAft6IxBK9PnqkmmfKrhHOEHM8rJ-IjKftilWjJNnV-hHVo0J18rbCIFTO6hoCSKUQAvD_BwE)
[docs.vultr.com-how-to-install-nvidia-cudnn](https://docs.vultr.com/how-to-install-nvidia-cudnn-on-ubuntu-22-04)
