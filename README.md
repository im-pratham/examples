# Examples website for Stream Processing with Apache Flink
---
Download Flink binary from - [Official Site]()

Make sure you have required software installed
- OC client
```shell script
choco install openshift-cli -y
```

Start Red hat developer sandbox - [Site](https://developers.redhat.com/developer-sandbox/get-started)

Copy Login command, and login 
```shell script
oc login --token= --server=https://api.sandbox.xx.xx.openshiftapps.com:xx
```

Create a image pull secret using 
```
oc create secret docker-registry docker --docker-server=docker.io --docker-username=<username> --docker-password=<password> --docker-email=<email>
```

Now deploy and port forword
```shell script
oc apply -f kubernetes/flink-all.yaml

## check pod is up
oc get po

## port forward to that pod
$flink=oc get po -l app=flink -o jsonpath="{.items[0].metadata.name}"
oc port-forward $flink 8081:8081

## Visit localhost:8081
```

Submit Job
start class name = io.github.streamingwithflink.chapter1.AverageSensorReadings
