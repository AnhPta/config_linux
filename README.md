# Git: 
    - sudo apt install git-allgit
    - config --global user.name "<your_user_name>"
    - git config --global user.email <your_email>

# SSH key:
    - ssh-keygen -t rsa -b 2048 -f ~/.ssh/<key-name-you-want>
    - cd .ssh/
    - ls (output: display file <key-name-you-want>.pub)
    - cat <key-name-you-want>.pub (1)
    - copy result of (1) to SSH keys on git

# SSH key Bitbucket:
    - ssh-keygen -> Enter
    - ls ~/.ssh (output: display file <key-name-you-want>.pub)
    - ssh-add ~/.ssh/<key-name-you-want>
    - cat ~/.ssh/<key-name-you-want>.pub (2)
    - copy result of (2) to SSH keys on bitbucket

# Xed:
    - sudo add-apt-repository ppa:embrosyn/xapps
    - sudo apt-get update
    - sudo apt-get install xed
    - sudo dpkg -l xed

# Zsh, Oh-my-zsh: 
    - sudo apt-get install zsh
    - sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

    + Zsh-autosuggestions:
        - git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
        - sudo xed ~/.zshrc
        - find "plugins" and replace: plugins=(zsh-autosuggestions)
            
        + Config Suggestion Highlight Style:
            - sudo xed ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
            - find ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE and set ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=white' 
           
    + Zsh-syntax-highlighting:
        - git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
        - sudo xed ~/.zshrc
        - find "plugins" and replace: plugins=(zsh-syntax-highlighting)

# PHP:
    - sudo apt-get install software-properties-common
    - sudo add-apt-repository ppa:ondrej/php
    - sudo apt-get update
    - sudo apt-get install libapache2-mod-php7.1 php7.1-bcmath php7.1-bz2 php7.1-cli php7.1-common php7.1-curl php7.1-dba php7.1-gd php7.1-gmp php7.1-imap php7.1-intl php7.1-ldap php7.1-mbstring php7.1-mcrypt php7.1-mysql php7.1-pgsql php7.1-snmp php7.1-soap php7.1-sqlite php7.1-tidy php7.1-xml php7.1-xmlrpc php7.1-xsl php7.1-zip
    - php --ini |grep Loaded
    - sudo nano /etc/php/7.1/cli/php.ini
    - cgi.fix_pathinfo=0 

# Composer: 
    - curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
    - export PATH="$HOME/.composer/vendor/bin:$PATH"

# Valet:
    - sudo apt-get install libnss3-tools jq xsel
    - composer global require cpriego/valet-linux
    - valet install

# Mariadb:
    - https://downloads.mariadb.org/mariadb/repositories/#mirror=shanghai-university&distro=Mint&distro_release=bionic--mint19&version=10.3

# Nodejs:
    - sudo apt install nodejs
    - sudo apt install npm
    - curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
      echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
    - sudo apt-get update && sudo apt-get install yarn

# Config network (not required):
    - /opt/valet-linux/dns-servers shows nameserver 8.8.8.8
    - /opt/valet-linux/resolv.conf shows nameserver 127.0.0.1

# Insomnia:
    - In browser download this file: https://builds.insomnia.rest/downloads/ubuntu/latest
    - echo "deb https://dl.bintray.com/getinsomnia/Insomnia /" \
    | sudo tee -a /etc/apt/sources.list.d/insomnia.list
    - wget --quiet -O - https://insomnia.rest/keys/debian-public.key.asc \
    | sudo apt-key add -
    - sudo apt-get update
    - sudo apt-get install insomnia

# Android Studio
    https://www.itzgeek.com/how-tos/linux/linux-mint-how-tos/how-to-install-android-studio-on-linux-mint-19-tara.html
    https://docs.expo.io/versions/v32.0.0/workflow/android-studio-emulator/

# Docker CE (Linux Mint 18 Sylvia):
    - sudo apt-get remove docker docker-engine docker.io
    - sudo apt-get update
    - sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
    - curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    - sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"
    - sudo apt-get update
    - sudo apt-get install docker-ce
    - sudo groupadd docker
    - sudo usermod -aG docker $USER -> restart
    - docker run hello-world
        Err: docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.26/containers/create: dial unix /var/run/docker.sock: connect: permission denied.
See 'docker run --help'. 
        -> sudo usermod -a -G docker $USER 
        -> restart

# Xdebug:
    - sudo apt-get install php-xdebug
    - sudo nano /etc/php/7.1/mods-available/xdebug.ini
        -> Add on this file:
            zend_extension=xdebug.so
            xdebug.remote_enable = 1
            xdebug.remote_port = 9000
            xdebug.idekey = PHPSTORM
            xdebug.show_error_trace = 1
            xdebug.remote_autostart = 0
    - sudo service apache2 restart
    - sudo service nginx restart
    - sudo phpenmod xdebug

# Redis:
    - sudo apt install redis-server 
        Test redis installed: redis-cli

# MySQLdb python:
    - sudo apt-get install python-mysqldb

# Python:
    + MySQLdb:
        - sudo apt-get install python-mysqldb 
    + Redis python:
        - pip install redis
    + Memcached python: pylibmc
        - sudo pip install pylibmc
    + Requests:
        - sudo pip install requests

# Photoshop CS6 Extend:
    + Wine:
        - sudo dpkg --add-architecture i386 
        - sudo apt-key add Release.key && sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/
        + Linux Mint 17.x: 
            - sudo apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ trusty main'
        + Linux Mint 18.x: 
            - sudo apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main'
        + Linux Mint 19.x: 
            - sudo apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main'
        - sudo apt-get update
        - sudo apt-get install --install-recommends winehq-stable
    + Download Photoshop CS6: 
        - https://mega.nz/#!vplRRKCB!ml6VzTqgdZXerPDheRNDoeWdIAguIKAe8zm8eNrhKcc
    + Run file exe: 
        - wine PhotoshopCS6_Linux.exe

# Flutter:
    + Doc: https://flutter.dev/docs/get-started/install/linux
    + Download Flutter SDK:
      - https://storage.googleapis.com/flutter_infra/releases/stable/linux/flutter_linux_v1.7.8+hotfix.4-stable.tar.xz
    + Install:
      - cd Sites
      - tar xf ~/Downloads/flutter_linux_v1.7.8+hotfix.4-stable.tar.xz
      + Get PATH: 
        - cd flutter/bin
        - pwd -> Copy (1)
      - xed ~/.zshrc
      - Add a line: export PATH="$PATH:(1)" (Ex: export PATH="$PATH:/home/anhpta/Sites/flutter/bin")
      - flutter precache
      - flutter doctor
      - Open Android Studio/File/Settings/ -> Install Plugin Flutter, Dart -> Restart
      - Open Android Studio/File/New/New Flutter Project -> ...
      
