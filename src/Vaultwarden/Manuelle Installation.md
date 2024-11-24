# Manuelle Installation

1. Installation von Docker-Compose
```bash
sudo dnf install docker-compose
```

2. Erstellung einer Docker-Compose Datei
```bash
vi docker-compose.yml
```

3. Setzen der richtigen Parameter in der Compose Dateis
```yml
services:
  vaultwarden:
    image: vaultwarden/server:latest
    container_name: vaultwarden
    restart: unless-stopped
    environment:
      DOMAIN: "????"
    volumes:
      - ./vw-data/:/data/   ?????
    ports:
      - 80:80
```

4. Starten des Docker-Containers
```bash
docker-compose up -d
```

Öffne einen Browser und rufe die URL des Servers auf (z. B. http://<server-ip> oder https://<domain>).

Fertig!