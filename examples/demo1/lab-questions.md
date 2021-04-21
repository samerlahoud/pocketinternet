
# Lab Questions

![IP addressing example](/docs/img/Sample_IP_addressing.png)

## Starting the Lab

Start the lab by running `docker-compose up` in the `/home/user/pocketinternet/examples/demo1#` directory. This command will not exit and will stream container logging to the terminal!

```
root@moocbox:/home/user/pocketinternet/examples/demo1# docker-compose up
Starting demo1_bird16_2_1 ... done
Starting demo1_bird16_1_1   ... done
Starting demo1_nginx16_2_1  ... done
Starting demo1_client16_2_1 ... done
Starting demo1_bird17_1_1   ... done
Starting demo1_bind16_1_1   ... done
Starting demo1_client17_1_1 ... done
```

In another window, you can confirm that the containers are running:

```
root@moocbox:/home/user# docker ps
CONTAINER ID        IMAGE                         COMMAND                  CREATED             STATUS              PORTS               NAMES
234c0e907eba        samerlahoud/client:0.2        "bash -c 'ip route d…"   2 hours ago         Up 53 seconds       22/tcp              demo1_client17_1_1
c9f09f9e9d39        samerlahoud/client:0.2        "bash -c 'ip route d…"   2 hours ago         Up 54 seconds       22/tcp              demo1_client16_2_1
2d23763a462a        samerlahoud/http-static:0.2   "bash -c 'ip route d…"   2 hours ago         Up 54 seconds       80/tcp              demo1_nginx16_2_1
32a1d0c6f63d        samerlahoud/bird:0.2          "bash -c 'sysctl net…"   2 hours ago         Up 54 seconds       179/tcp             demo1_bird17_1_1
3a1bae814624        samerlahoud/demo-dns:0.2      "bash -c 'ip route d…"   2 hours ago         Up 53 seconds       53/tcp              demo1_bind16_1_1
b3376663c16b        samerlahoud/bird:0.2          "bash -c 'sysctl net…"   2 hours ago         Up 56 seconds       179/tcp             demo1_bird16_1_1
b89f6867329c        samerlahoud/bird:0.2          "bash -c 'sysctl net…"   2 hours ago         Up 57 seconds       179/tcp             demo1_bird16_2_1

```

You can SSH directly into the client container (10.17.1.101) [user = root, password = pocket]. 
To run commands in the other containers you can start a shell using ``docker exec -it demo1_nginx16_2_1 /bin/bash``.

## Cleanup

To stop the lab, press `Ctrl+C` in the `docker-compose` window and, once it's done, run `docker-compose down` to remove all containers, networks etc.

```
Gracefully stopping... (press Ctrl+C again to force)
Stopping demo1_client17_1_1 ... done
Stopping demo1_client16_2_1 ... done
Stopping demo1_nginx16_2_1  ... done
Stopping demo1_bird17_1_1   ... done
Stopping demo1_bind16_1_1   ... done
Stopping demo1_bird16_1_1   ... done
Stopping demo1_bird16_2_1   ... done
root@moocbox:/home/user/pocketinternet/examples/demo1# docker-compose down
Removing demo1_client17_1_1 ... done
Removing demo1_client16_2_1 ... done
Removing demo1_nginx16_2_1  ... done
Removing demo1_bird17_1_1   ... done
Removing demo1_bind16_1_1   ... done
Removing demo1_bird16_1_1   ... done
Removing demo1_bird16_2_1   ... done
Removing network demo1_backbone_net
Removing network demo1_lan_net_16_1
Removing network demo1_lan_net_17_1
Removing network demo1_lan_net_16_2

```

## Routing Tables

Show the contents of the routing tables on all devices.
- `ip route` and `ip -6 route` for hosts.
- `birdc show route` and `birdc6 show route` for routers.

Analyze the results.
