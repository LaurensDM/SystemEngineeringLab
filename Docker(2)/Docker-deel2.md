# Verslag Opdracht 5 deel2 (docker)

## Stap 1: Installatie Nextcloud

We maken eerst een extra folder aan genaamd nextcloud om de docker-compose.yml in aan te maken
De docker-compose.yml wordt dan opgesteld.
Voor de wachtwoorden worden omgevingsvariabelen gemaakt, wachtwoorden zouden namelijk niet in plain-text mogen staan.
Hieronder de inhoud van het docker-compose.yml file.
```

version: '2'

volumes:
  nextcloud:
  db:

networks:
  nextcloud_network:
    external: false

services:
  db:
    image: mariadb:10.5
    restart: unless-stopped
    command: --transaction-isolation=READ-COMMITTED --binlog-format=ROW
    volumes:
      - db:/var/lib/mysql
    environment:

      - MYSQL_ROOT_PASSWORD=${rootpwd}
      - MYSQL_PASSWORD=${pwd}
      - MYSQL_DATABASE=${database}
      - MYSQL_USER=${user}
    networks:
      - nextcloud_network

  app:
    image: nextcloud
    restart: unless-stopped
    ports:
      - 420:80
    links:
      - db
    volumes:
      - nextcloud:/var/www/html
    environment:
      - MYSQL_PASSWORD=${pwd}
      - MYSQL_DATABASE=${database}
      - MYSQL_USER=${user}
      - MYSQL_HOST=${host}
      - REDIS_HOST=redis
    networks:
      - nextcloud_network

  redis:
    image: redis:alpine
    container_name: redis
    volumes:
      - /docker/nextcloud/redis:/data
    networks:
      - nextcloud_network
    restart: unless-stopped
    
```
Origineel was het de bedoeling om nextcloud op poort 8080 te zetten. Deze poort was echter al bezet door vaultwarden, dus is er gekozen voor poort 420.
Met het commando `docker compose up -d` wordt het bestand uitgevoerd. Het duurt een tijdje vooraleer alles is opgestart

![voorbeeld opstarten nextcloud](images/download.png)

Nadat het opstarten voltooid is wordt gecontroleerd of alles goed is verlopen met `docker compose logs --follow`
Het volgende werd vastgesteld:

![errors in de logs](images/error.png)

In het docker-compose.yml stonden functies die overbodig waren en voor errors zorgden, dus deze werden verwijdert uit de file.
Er werd nogmaals `docker compose up -d` en docker compose logs --follow` uitgevoerd, geen errors meer op te merken.

## Stap2: Commando's uitvoeren in een container



