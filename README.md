# Traefik With Swarm

For you to run this service you will need to have 3 nodes running, only 1 needs to be a manager

You need to start swarm and put two other machines in the node group

Run this command below to be able to check

```bash
docker node ls
```

You should expect it to return

```response
ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
nnc23sjm0nhbrc2wyznt4rz3l *   node1               Ready               Active              Leader              19.03.6
fcrpjwwjw60cpr487sc01dqr7     node2               Ready               Active                                  19.03.6
m8sudulzg66adg0qawl63206t     node4               Ready               Active                                  19.03.6
```


increase the number of replicates between the two services, you will run this command here

```bash
docker service scale whoami0=5
```

To verify that the balance is working, run this command

```bash
curl -H Host:whoami0.traefik http://IP_MACHINE
```
