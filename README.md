setup-desktop-dev-linux
=========

Role do Ansible com passos para a pós-instalação de Desktops Linux com programas e ferramentas mais utilizadas para desenvolvimento de software.

Distribuições Suportadas pela Role
------------

- Fedora 30 ou inferior
- Linux Mint LMDE 3 ou superior
- Linux Mint 19.2 ou inferior
- openSUSE Leap 15.0 ou superior
- openSUSE Tumbleweed
- Ubuntu 18.04 ou superior


Tags da Role 
--------------

- main: Tag a ser utilizada em conjunto com outras tags, se alguma tag for especificada no comando.

- directory: Cria a estrutura de diretórios de desenvolvimento no HOME do usuário.
  
- dev: Instala os pacotes de desenvolvimento.
- vim: Instala o editor de texto Vim.


Variáveis da Role 
--------------

- root_dir: Nome do diretório raiz de desenvolvimento que fica dentro do HOME do usuário. Valor padrão: environment.


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

MIT License