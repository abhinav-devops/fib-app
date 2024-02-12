# Fibonacci Web Server

## To deploy to local k8s cluster

1) Install kapp, kustomize on local machine
-`https://carvel.dev/kapp/docs/v0.59.x/install/`
-`https://kubectl.docs.kubernetes.io/installation/kustomize/`
2) change dir to dev overlays
 -`$ cd k8s/overlays/dev/`
3) Install app using Kapp cli
 -`kapp deploy --color --diff-changes --namespace dev  --app app --file <(kustomize build .)
4) Access the web app on the url (Add the hostname in resolv.conf for name resolution)
-`https://fib-app.sandbox.gt.com:8000/?n=10`

## To deploy on EKS

1) Uncomment the below line in .gitlab-ci/02-k8s.yml to authenticate and download the kube_config for EKS
-`aws eks --region us-east-1 update-kubeconfig --name ${CLUSTER_NAME}`
2) Execute the complete CI/CD pipeline in Gitlab.
3) Access the application on the exposed ingressurl.

### Things to-do

1. More mature pipeline with image-name being calculated from the CI pipeline.