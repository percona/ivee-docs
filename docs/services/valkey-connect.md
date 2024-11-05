# Connecting to a Valkey Server

This document describes how to connect to a Valkey server. You must have the instance endpoint, and then you can use either of the following methods:

* `valkey-cli` command-line interface
* Python with `redis-py` library

## 0. Get the endpoint

To get the endpoint to connect to, go to [Ivee portal](https://app.ivee.cloud) and in the "Instances" choose the Valkey instance.
In the "Connectivity" section you will find the Global endpoint and the Port.

## 1. Connect with `valkey-cli`

`valkey-cli` is a command-line interface (CLI) for interacting with Valkey servers.
The CLI allows you to execute commands, inspect data, and manage your Valkey instance.

To connect, simply open your terminal and type:

```bash
valkey-cli -h "ENDPOINT" -p "PORT" --tls
```
Ivee enforces TLS, so it is a must to use --tls flag.

## 2. Connect with python

There is no valkey library for python right now, but as valkey is an open-source fork,
[redis-py](https://github.com/redis/redis-py) library would just work.

Here is an example of how to connect to Valkey with redis-py:
```python
import redis

def connect_and_push_redis(host, port):
    try:
        r = redis.Redis(host=host, port=port,  username='', password='', ssl=True)
        r.set('your_key', 'your_value')
        print(f"Pushed 'your_value' to 'your_key'")

    except redis.ConnectionError as e:
        print(f"Error connecting to Valkey: {e}")

# Provide your Valkey server details
host       = YOUR_ENDPOINT
port       = YOUR_PORT
user       = YOUR_USER
password   = YOUR_PASSWORD

# Connect and attempt to push
connect_and_push_redis(host, port, user, password)
```

[Deploy Valkey for free now:material-arrow-right:](https://app.ivee.cloud){.md-button }
