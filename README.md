# Zephyr-wiki

## Como instalar o RTOS Zephyr em uma placa de desenvolvimento no Windows

É necessário primeiro instalar as dependências, que são: ninja, gperf, python, git, dtc-msys2, wget, unzip e cmake<br><br>
Instale o `west` usando `pip install west`<br><br>
Use o comando `west init <nome do projeto>` para criar um projeto<br><br>
Dentro da pasta `<nome do projeto>` use o comando `west update` e depois `west zephyr-export`<br><br>
Agora instale as dependências python com `pip install -r zephyr\scripts\requirements.txt`<br><br>
Agora é necessário baixar e configurar o SDK do zephyr, acesse sua home usando `cd %HOMEPATH%` e baixe o SDK usando `wget https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.15.0/zephyr-sdk-0.15.0_windows-x86_64.zip`, depois descompacte usando `unzip zephyr-sdk-0.15.0_windows-x86_64.zip`<br><br>
Para configurar o SDK use `cd zephyr-sdk-0.15.0` e `setup.cmd`<br><br>
Na pasta do projeto use `set ZEPHYR_TOOLCHAIN_VARIANT=zephyr` e `set ZEPHYR_SDK_INSTALL_DIR=<caminho do sdk>` para setar as variáveis que serão usadas pelo zephyr para utilizar o SDK que foi baixado<br><br>
Dentro da pasta `zephyr` que está localizada na pasta do projeto use o comando `west build -p always -b <nome da placa> samples\synchronization` para buildar o exemplo `synchronization` que já vem no zephyr, em `<nome da placa>` coloque o nome da placa que será usada no projeto. para ver a lista de placas suportadas acesse: https://docs.zephyrproject.org/latest/boards/index.html<br><br>
A partir daqui cada placa pode ter um processo diferente de instalação, é necessário verificar no link acima o processo referente a placa que será usada, a exemplo da placa Raptor Lake CRB o processo é criar um dispositivo USB bootavel, primeiro formatando usando FAT32 e copiando o arquivo de imagem `zephyr/zephyr.efi` que foi gerado dentro da pasta `build` durante a etapa de build, no dispositivo USB, depois ligando a placa com o dispositivo USB conectado e o computador escutando a placa em uma porta serial, executando o comando `fs0:zephyr.efi`

## Referências

https://docs.zephyrproject.org/3.2.0/develop/getting_started/index.html
