kubectl run -it --image=alpine --rm --command -- bash

kubectl get pods -l <labelKey>=<labelValue>
kubectl get pods -l app=web
kubectl get pods -l 'app in (web,web123)'

###### Enter into
kubectl run -it --image=cmd.cat/bash/curl --rm --command -- bash

###### Loop requests
watch curl -s <podName>
watch curl -s web

kubectl scale --replicas=3 replicaset <replicaSetName>
kubectl scale --replicas=3 replicaset myreplicaset

###### Get env variables from the pod
kubectl exec -it env -- printenv
kubectl exec -it env -c <ContainerName> -- printenv

kubectl get pods -l <labelKey>=<labelValue> -o name | xargs -I{} kubectl exec -i  {} -- printenv
kubectl get pods -l app=db -o name | xargs -I{} kubectl exec -i  {} -- printenv

###### Get logs from the pod
kubectl get pods -l app=db -o name | xargs -I{} kubectl logs {}

###### Nginx image (without great response)
image: nicholasdille/nginx-hello