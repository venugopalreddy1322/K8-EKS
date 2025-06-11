## Demo
$ k get po
NAME      READY   STATUS    RESTARTS   AGE
mongo-0   1/1     Running   0          17m
mongo-1   1/1     Running   0          14m
mongo-2   1/1     Running   0          16m

$ k exec -it mongo-0 -- mongosh
