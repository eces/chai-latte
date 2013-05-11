# Chai-latte
### A tool for parallel deployment with Play Framework 2
It allows developers publish to dedicate server in a blink.

This is especially for

- Play Framework 2.x
- Server can use SSH
- Proxy enabled web server with load balancer (an example of Apache is below)

## Getting Started

0. Download [Zip File](https://github.com/eces/chai-latte/archive/master.zip) and unzip into the working directory (where `README`, `app`, `conf`, `public` are located).

0. Configure `deploy.conf` file. *SERVER_HOST*, *SERVER_USER* and *BASE_DIR* are must be set.
    ```python
    #!/bin/bash

    # deploy.conf
    #
    # Author: Jinhyuk Lee <eces at mstock.org>
    # Organization: MINTPRESSO <support at mintpresso.com>
    # Repository: https://github.com/eces/chai-latte
    #
    # Description: This is a configuration file for the command 'deploy' of executable script file.
    #

    ORGANIZATION_NAME='MINTPRESSO'
    USER_NAME='Jinhyuk Lee'

    SERVER_NAME='trinity.so (IDC)'
    SERVER_HOST='trinity.so'
    SERVER_USER='trinity'

    # without slash '/' at the end
    BASE_DIR='/home/trinity/playframework'
    PLAY_OPTIONS=''
    ```

0. (Optional) You may need to type `../path/to/chai-latte/deploy` all the time, so let's go easy! Create symbolic link with `ln -s` or just add one line `alias deploy="~/chai-latte/deploy"` in your shell configuration file (For bash shell, edit `~/.profile` and reload `. ~/.profile` ) so now you can use `deploy` everywhere.

0. Run `deploy` in command line and you will see 
    ```bash
    Eces-Mac-Mini:soran-ui eces$ deploy
    usage: deploy [port_number]
    ```

0. See what's going on. All output from remote server displays in yellow.
    ```bash
    Eces-Mac-Mini:soran-ui eces$ deploy 10000

    [ MINTPRESSO ]

    Auto Deployment to trinity.so (IDC) will be processed in /Users/eces/soran-ui

    [1/5] clean-compile-staged /Users/eces/soran-ui/target is okay? [y/n]: 
    y
    [2/5] Port 10000 is okay? [y/n]: 
    y
    [3/5] Waiting for upload ... 

    trinity@trinity.so's password: 
    ```

0. (Optional) For your information, you don't need to enter the password in every deployment process. Using some sugar `ssh-keygen` and `ssh-copy-id` you can just skip it. **If your deployment is for prototyping**, it's very nice and highly recommended.

    >TODO
    >
    > check this out:
    > http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/

## Setting up web server

### Basic Concept

>TODO

### Apache Web Server

>TODO

# Further information

Please email to [support@mintpresso.com](mailto:support@mintpresso.com) or create issue on [Github Issues](https://github.com/eces/chai-latte/issues).
