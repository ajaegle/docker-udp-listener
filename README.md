# ajaegle/udp-listener [![](https://images.microbadger.com/badges/image/ajaegle/udp-listener.svg)](https://microbadger.com/images/ajaegle/udp-listener "Get your own image badge on microbadger.com")

Docker image that listens on a specified UDP port, outputs to container log as hex dump.

### Start it

By default, you can run it like this

    docker run -p 0.0.0.0:5005:5005 -p 0.0.0.0:5005:5005/udp --name udp-listener ajaegle/udp-listener:1.0.0

You can make it listen on another port

    docker run -p 0.0.0.0:4444:4444 -p 0.0.0.0:4444:4444/udp -e UDPPORT=4444 --name udp-listener ajaegle/udp-listener:1.0.0

#### Test it

In another terminal:

    nc -4 -u localhost 5005

And start sending data.  You should see your text reflected in the `docker run` terminal


### Docker Compose

```
udp:
  container_name: my-udp-listener
  image: ajaegle/udp-listener
  environment:
    - UDPPORT=4001
  ports:
  - "0.0.0.0:4001:4001"
  - "0.0.0.0:4001:4001/udp"

```

View its logs:

    docker logs my-udp-listener
