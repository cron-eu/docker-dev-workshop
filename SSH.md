Dev (SSH) container
===================

We will setup a separate Container which runs as a SSH server.

## Setup

cp `authorized_keys` file for the dev Container:

```
cp ~/.ssh/id_rsa-cron.pub dev/authorized_keys
```

Build the Stack

```
docker-compose up -d
```

SSH to the dev container:

```
ssh -p 2200 www-data@$(docker-machine ip workshop)
```
