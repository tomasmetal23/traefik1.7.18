# traefik1.7.18


Para comprender todas las banderas (fllags) porfavor use la documentacion del sitio web de traefik.

Recuerde tener los puertos 80 y 443 desocupados, si usa otro proxy como apache2 o nginx, fijese que
no esten ocupando los puertos http y https.


 docker run -d -e CLOUDFLARE_EMAIL=correo-de-nuestra-cuenta-cloudflare-aqui -e CLOUDFLARE_API_KEY=colocarsuapiaqui \
      -v /var/run/docker.sock:/var/run/docker.sock \
      -v /opt/traefik/traefik.toml:/traefik.toml \
      -v /opt/traefik/servers.toml:/servers.toml \
      -v /opt/traefik/acme.json:/acme.json \
      -p 80:80 \
      -p 443:443 \
      -l traefik.frontend.rule=Host:monitor.tudominio.com \
      -l traefik.port=8080 \
      --network web \
      --name traefik \
      traefik:1.7.18-alpine
