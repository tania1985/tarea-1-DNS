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


## DOCKER COMPOSE CLIENT 

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
    # apk add --no-cache bind-tools

## db.asircastelao.int
$TTL 38400	; 10 hours 40 minutes
@		IN SOA	ns.asircastelao.int. some.email.address. (
				17161016   ; serial
				10800      ; refresh (3 hours)
				3600       ; retry (1 hour)
				604800     ; expire (1 week)
				38400      ; minimum (10 hours 40 minutes)
				)
@		IN NS	ns.asircastelao.int.
ns		IN A 	172.28.5.1
test	IN A	172.28.5.4
wwww    IN A    172.28.5.7
alias	IN CNAME  test
texto   IN TXT 	mensaje
