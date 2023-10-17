# tarea-1-DNS
# Práctica DNS

# Docker-compose.yml

services:
  asir_bind9:
    container_name: asir_bind9
    image: ubuntu/bind9
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

    # docker compose -f docker-compose_client.yml up