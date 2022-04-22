# Creazione ambiente lamp 

Crea in locale tutte le immagini docker-locale/* necessarie

## Creare volume e network

Volume e network saranno usati da molteplici immagini 

docker create volume php-services
docker create network dockerlocale

## Lanciare compose

docker-compose up -d

# Note

Eventualmente far creare il network nel compose

networks:
  dockerlocale:
    # use the bridge driver, but enable IPv6
    driver: bridge
    driver_opts:
      com.docker.network.enable_ipv6: "false"
    ipam:
      driver: default
      config:
        - subnet: 172.22.0.0/24
          gateway: 172.22.0.1
        - subnet: "2001:3984:3989::/64"
          gateway: "2001:3984:3989::1"