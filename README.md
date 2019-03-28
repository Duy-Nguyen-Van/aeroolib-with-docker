# aeroolib-with-docker

1. Log into docker container
    ```
    docker exec -u root -it <container_name> bin/bash
    ```
    (if don't know <container_name>, use ``` docker ps ```)

2. Install git
    ```
    apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y git
    ```
3. Install python 2
    ```
    apt-get update
    apt-get install python-pip
    ```
4. Install Dependencies
    ```
    apt-get install libreoffice*
    pip install genshi
    apt-get install python-cairo python3-uno python-lxml
    apt-get install zip bzr python-setuptools
    ```
5. Install Aeroo Library
    ```
    pip3 install git+https://github.com/aeroo/currency2text.git
    git clone https://github.com/aeroo/aeroolib
    cd aerolib
    python3 setup.py install
    ```
6. Install & setup Aeroo Docs
    ```
    apt-get install python3-pip
    pip3 install jsonrpc2 daemonize
    mkdir /opt/aeroo
    cd /opt/aeroo
    git clone https://github.com/aeroo/aeroo_docs.git
    ```
7. Set up default config
    ```
    python3 /opt/aeroo/aeroo_docs/aeroo-docs start -c /etc/aeroo-docs.conf
    ```
8. Set up Aeroo Docs service
    ```
    ln -s /opt/aeroo/aeroo_docs/aeroo-docs /etc/init.d/aeroo-docs
    update-rc.d aeroo-docs defaults
    ```
9. Test service
    ```
    service aeroo-docs restart
    ```
10. Create & Paste the content in the file openoffice.sh
    ```
    nano /etc/init.d/openoffice.sh
    ```
11. Make the file executable and add init script to the startup
    ```
    chmod 0755 /etc/init.d/openoffice.sh
    update-rc.d openoffice.sh defaults
    ```
12. Run openoffice
    ```
    /etc/init.d/openoffice.sh start
    ```
13. Test connection
<img src="/images/pic_1.png">
<img src="/images/pic_2.png">
          
REFERENCES:

https://serpentcs.com/serpentcs-setup-aeroo-report-engine-for-openerp-272
