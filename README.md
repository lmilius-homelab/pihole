# pihole
Repo for storing pihole configuration for my homelab

[![Build Status](http://drone.lukemilius.com/api/badges/lmilius-homelab/pihole/status.svg)](http://drone.lukemilius.com/lmilius-homelab/pihole)

## Required Manual Step
The proxy stack is not deployed via drone because of inter-dependencies 
(drone receives webhooks through the proxy) which is not possible if the
proxy doesn't exist and drone is only exposed by the proxy itself.

On the docker host, clone the repo to a local directory and change directory into 
the `proxy` dir. Make a copy of the `example.env` file and name it `.env`. 
You will need to fill in the values for the secrets. Finally, run the following command:

```shell script
docker network create -d macvlan --subnet=10.10.200.4/24 --gateway=10.10.200.1 --ip-range=10.10.200.4/29 -o parent=eno1 lan_net
docker-compose up -d
```
