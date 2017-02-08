Des variables d'environnement peuvent être ajoutés dans docker-compose, par exemple pour xdebug :
```
environment:
    XDEBUG_CONFIG: remote_host=192.168.99.1 remote_port=10000
```
