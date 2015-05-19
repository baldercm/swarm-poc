swarm-poc
=========
Vagrant based cluster for Docker Swarm PoC.

# Basic Usage

`cluster-id: 6eb3ca8ee7c8dfe29d6988f51d316930`

1. Start up the Swarm agents VM (`192.168.100.101` and `192.168.100.102`):
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
  Containers: 2
  Strategy: spread
  Filters: affinity, health, constraint, port, dependency
  Nodes: 2
   swarm-agent: 192.168.100.101:2375
    └ Containers: 1
    └ Reserved CPUs: 0 / 1
    └ Reserved Memory: 0 B / 514.5 MiB
   swarm-agent: 192.168.100.102:2375
    └ Containers: 1
    └ Reserved CPUs: 0 / 1
    └ Reserved Memory: 0 B / 514.5 MiB
  ```
