# Chai Latte
### A tool for parallel deployment with Play Framework 2
It allows developers publish to dedicate server in a blink.


## Naming
Chai-tea Latte is one of the most favorite hot beverage of @eces. An english word (formerly from Persian/Hindustani language) 'chai' pronounces like the word 'difference' in Korean. Chai Latte means that differences of local and server are softly going together like soft steamed milk.

@eces가 제일 좋아하는 Chai-tea Latte로 이름을 정했습니다. "서버와 로컬의 Chai(차이)를 Latte(라떼)처럼 합치자"라는 뜻을 가지고 있습니다.

## Requirements
- Play Framework 2.x
- Server can use SSH
- Proxy enabled web server with port-based load balancer (an example of Apache is below)

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
    PLAY_OPTIONS='-Dconfig.file=../production.conf'
    ```

0. (Optional) You may need to type `../path/to/chai-latte/deploy` all the time, so let's go easy! Create symbolic link with `ln -s` or just add one line `alias deploy="~/chai-latte/deploy"` in your shell configuration file (For bash shell, edit `~/.profile` and reload `. ~/.profile` ) so now you can use `deploy` everywhere.

0. Prepare the compiled `target` source by typing `play clean compile stage` in your working directory.

0. Run `deploy` in command line and you will see 
    ```bash
    $ deploy
    usage: deploy [port_number]
    ```

0. See what's going on. All output from remote server displays in yellow.
    ```bash
    $ deploy 10000

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

    > Check this out: [3 Steps to perform SSH login without password using ssh-key and ssh-copy-id](http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id)

    This is an **5 seconds deployment** example if you've followed the guide above.
    ```bash
    $ deploy 15000

    [ MINTPRESSO ]

    Auto Deployment to trinity.so (IDC) will be processed in /Users/eces/panel

    [1/5] clean-compile-staged /Users/eces/panel/target is okay? [y/n]: 
    y
    [2/5] Port 15000 is okay? [y/n]: 
    y
    [3/5] Waiting for upload ... 

     Uploaded in 4s
    [4/5] Waiting for restart ... 

    ...
    # remote console displays in here with yellow color
    ...

     Executed in 1s
     Total 5s

    [5/5] DONE!
    ```

    Please don't do this.
    ```bash
    $ yes | deploy 15000
    ```

## Setting up web server

### Basic Concept

>TODO

### Apache Web Server

>TODO

# Further information

Please email to [support@mintpresso.com](mailto:support@mintpresso.com) or create issue on [Github Issues](https://github.com/eces/chai-latte/issues).

This is a by-product of [MINTPRESSO](http://mintpresso.com).
