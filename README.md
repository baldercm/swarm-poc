swarm-poc
=========
Vagrant based cluster for Docker Swarm PoC.

# Basic Usage

`cluster-id: 6eb3ca8ee7c8dfe29d6988f51d316930`

1. Start up the Swarm agent VM (`192.168.100.101`):
  ```
  $ cd /path/to/swarm-poc/agent
  $ vagrant up
  ```

2. Start up the Swarm manager VM (`192.168.100.100`):
  ```
  $ cd /path/to/swarm-poc/manager
  $ vagrant up
  ```

3. Check everything is OK:
  ```
  $ docker -H tcp://192.168.100.100:4243 info
  Containers: 1
  Strategy: spread
  Filters: affinity, health, constraint, port, dependency
  Nodes: 1
   swarm-agent: 192.168.100.101:2375
    └ Containers: 1
    └ Reserved CPUs: 0 / 1
    └ Reserved Memory: 0 B / 514.5 MiB

  $ docker -H tcp://192.168.100.100:4243 run -p 80:80 -d nginx
  <some-container-id>

  $ curl -Il 192.168.100.101
  HTTP/1.1 200 OK
  Server: nginx/1.9.0
  Date: Mon, 18 May 2015 23:58:18 GMT
  Content-Type: text/html
  Content-Length: 612
  Last-Modified: Tue, 28 Apr 2015 16:15:59 GMT
  Connection: keep-alive
  ETag: "553fb23f-264"
  Accept-Ranges: bytes
  ```
