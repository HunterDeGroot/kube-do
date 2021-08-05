install doctl (digital ocean cli)
https://docs.digitalocean.com/reference/doctl/how-to/install/
doctl auth init
doctl kubernetes cluster kubeconfig save clustername --access-token token

helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install quickstart ingress-nginx/ingress-nginx

https://kenanbek.github.io/kubernetes-https-nginx-ingress-cert-manager-digitalocean
kubectl create namespace cert-manager
kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v0.12.0/cert-manager.yaml

kubectl delete -f .\prod_issuer.yaml
kubectl apply -f prod_issuer.yaml 

kubectl delete -f .\ingress.yaml
kubectl apply -f .\ingress.yaml 

kompose convert --out kompose.yaml
kubectl delete -f .\kompose.yaml
kubectl apply -f .\kompose.yaml
