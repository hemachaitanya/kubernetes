
kubectl apply -f <filename>

kubectl get po

kubectl api-resources

kubectl delete pods <pod name1> <pod2> <pod3>

kubectl scale replicas=3 rs/< rs pods name>

kubectl scale replicas=1 rs/<rs pods name>

* always we go with manifest not using above manival commands by use scalling urpose

(scalling up & down):

(scalling out&in):increase and decreasing

kubectl get rs

(login into a specific container)

kubectl get po --show-labels

kubectl run n1 --image=<labels>

kubectl  get po --selector "app in(nginx,web)" --show-labels

kubectl get nodes --show-labels

kubectl taint nodes <node-name> poc=true:NoSchedule

kubectl taint nodes ip-10-0-1-119.us-east-2.compute.internal poc=true:NoSchedule

for other nodes

kubectl taint nodes ip-10-0-1-199.us-east-2.compute.internal poc=false:NoSchedule

kubectl taint nodes ip-10-0-3-230.us-east-2.compute.internal poc=false:NoSchedule

kubectl get nodes --show-labels

kubectl label nodes <your-node-name> disktype=ssd

kubectl run nginx --image=nginx --restart=Never



