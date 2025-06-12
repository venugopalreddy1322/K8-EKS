## Demo
$ k get po
NAME      READY   STATUS    RESTARTS   AGE
mongo-0   1/1     Running   0          17m
mongo-1   1/1     Running   0          14m
mongo-2   1/1     Running   0          16m

Exec into mongo pod and create replica by using following commands:

$ k exec -it mongo-0 -- mongosh
test> rs.initiate(
...         {
...            _id: "rs0",
...            members: [
...                { _id: 0, host : "mongo-0.mongo-headlessvc.default.svc.cluster.local:27017" },
...                { _id: 1, host : "mongo-1.mongo-headlessvc.default.svc.cluster.local:27017" },
...                { _id: 2, host : "mongo-2.mongo-headlessvc.default.svc.cluster.local:27017" },
...           ]
...         }
... )
