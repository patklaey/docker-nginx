# Docker Nginx installation on ARM

## Installation

Follow those simple steps: 

1. Clone the git repo
    ```bash
    git clone https://github.com/patklaey/docker-nginx
    cd docker-nginx
    ```
1. Start up the containers
    ```bash
    docker-compose up -d
    ```
    
## Add a new site

Assuming you already cloned the repository

1. Go the the conf.d folder
    ```bash
    cd %docker-nginx-repo%/nginx/conf.d
    ```
1. Create the new conf file
    ```bash
    vi new-site.conf
    ```
1. Make sure you have all necessary certificates and key files in the ```%docker-nginx-repo%/nginx/certs``` folder: 
    * COMODORSADomainValidationSecureServerCA.crt
    * cloud.patklaey.ch.crt
    * cloud.patklaey.ch.key
    * patklaey_ch.key
    * zermatt-api_patklaey_ch.crt
    * zermatt_patklaey_ch.crt
1. Build the new image (see [wiki](http://wiki.patklaey.ch/index.php/Docker_Cheat_Sheet#Build))
    * Use ```PACKAGE_NAME="patklaey/nginx"```
    * Don't forget to increase the package version
1. Reference the new version in the ```docker-compose.yml``` file
1. Recreate the container
    ```bash
    cd %docker-nginx-repo%
    docker-compose down
    docker-compose up -d
    ```