## Tworzenie Gitea za pomocą dockera

1. docker run -d --name gitea, flaga oznacza aby uruchomić w tle
2. --restart unless-stopped, uruchom ponownie jeśli zatrzymano
3. -p 3000:3000, port hosta:port kontenera
4. -v ~/homelab-ops/gitea/data:/data, ścieżka do zapisywania danych z gitea
5. gitea/gitea:latest, instalacja najnowszej wersji
6. 192.168.137.10:3000, ip oraz port do zalogowania z przeglądarki

## Polecenie instalacji

```docker
docker run -d \
  --name gitea \
  --restart unless-stopped \
  -p 3000:3000 \
  -v ~/homelab-ops/gitea/data:/data \
  gitea/gitea:latest
```
