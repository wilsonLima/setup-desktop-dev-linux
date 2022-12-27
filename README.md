setup-desktop-dev-linux
=========

Role do Ansible com passos para a pós-instalação de Desktops Linux com alguns pacotes utilizados em desenvolvimento de software.

Distribuições Suportadas pela Role
------------

- Fedora 28 ou superior
- Linux Mint LMDE 3 ou superior
- Linux Mint 19.1 ou superior
- openSUSE Leap 15.0 ou superior
- openSUSE Tumbleweed
- Ubuntu 18.04 ou superior


Tags da Role 
--------------

- main: Tag a ser utilizada em conjunto com outras tags, se alguma tag for especificada no comando.

- directory: Cria a estrutura de diretórios de desenvolvimento no HOME do usuário.
  
- dev: Instala os pacotes de desenvolvimento.
- vim: Instala o editor de texto Vim.

- dev-tools: Instala TODAS ferramentas de desenvolvimento da role, como Apache Maven e o Gradle.
- maven: Baixa e descompacta a ferramenta de build Apache Maven 3.
- gradle: Baixa e descompacta a ferramenta de build Gradle.

- ide: Baixa e descompacta TODAS as IDEs da role.
- idea: Baixa e descompacta a IDE IntelliJ IDEA.
- pycharm: Baixa e descompacta a IDE PyCharm.
- eclipse: Baixa e descompacta a IDE Eclipse for Enterprise Java Developers.
- sts: Baixa e descompacta a IDE Spring Tools.


Variáveis da Role 
--------------

- home_dir: Diretório home para a criação dos diretórios de desenvolvimento. Valor padrão, o HOME do usuário linux utilizado no inventário.
- root_env_dir: Nome do diretório raiz de desenvolvimento que fica dentro do HOME do usuário. Valor padrão: environment.
- maven_version: Versão da ferramenta de build Apache Maven 3. Valor padrão: "3.8.6".
- gradle_version: Versão da ferramenta de build Gradle. Valor padrão: "7.6"
- eclipse_incubation: Indica se a versão do Eclipse a ser baixada é uma versão "incubation". Valor padrão: no.
- eclipse_version: Versão da IDE Eclipse for Enterprise Java Developers. Valor padrão: "2022-12"
- idea_version: Versão da IDE IntelliJ IDEA. Valor padrão: "2022.3.1"
- pycharm_version: Versão da IDE PyCharm. Valor padrão: "2022.3"
- sts_eclipse_version: Versão da IDE Eclipse em que a IDE Spring Tools a ser baixada foi baseada. Valor padrão: "e4.26"
- sts_eclipse_minor_version: Versão Minor da IDE Eclipse em que a IDE Spring Tools a ser baixada foi baseada. Valor padrão: "0".
- sts_major_version: Versão Major da IDE Spring Tools. Valor padrão: "4".
- sts_version: Versão da IDE Spring Tools. Valor padrão: "4.17.0.RELEASE"


Dependências da Role 
--------------

Linux Mint e Ubuntu:

- openssh-server. Ex.: sudo apt install openssh-server


Exemplo de Inventario
----------------

Exemplo de arquivo de hosts: pasta_invetario/hosts

    [NOME]
    IP ansible_connection=ssh ansible_ssh_user=USUARIO ansible_ssh_pass=SENHA_URUARIO ansible_become_pass=SENHA_ROOT


Especificar interpretador python 3: pasta_invetario/group_vars/all

    ansible_python_interpreter: "/usr/bin/python3"


Exemplo de Playbook
----------------

Exemplo de uso da Role, com as configurações padrão:

    - hosts: desktop
      roles:
         - setup-desktop-dev-linux

Exemplo de uso da Role com variáveis:

    - hosts: desktop
      roles:
         - { role: setup-desktop-dev-linux, root_dir: 'developer' }


Exemplo de Comandos
----------------

Comando para executar todas as tasks:

    ansible-playbook -i <caminho_inventario> <caminho_playbook>

Comando para executar a tag "vim" (em caso de uso de tags, a tag "main" é obrigatória):

    ansible-playbook -i <caminho_inventario> <caminho_playbook> --tags "main, vim"


License
-------

MIT