# tarea-1-DNS
# Práctica DNS

# Docker-compose.yml

services:
  <br>asir_bind9:</br>
    container_name: asir_bind9
    image: internetsystemsconsortium/bind9:9.16
    platform: linux/amd64
    ports:
      - 53:53
    networks:
      bind9_subnet:
        ipv4_address: 172.28.5.1
    volumes:
      - ./conf:/etc/bind
      - ./zonas:/var/lib/bind
networks:
  bind9_subnet:
    external: true