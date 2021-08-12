# sparrow-k8-ubuntu
Declarative approach to managing k8 yamls given a specific directory space. 

##Declarative management:
	https://kubernetes.io/docs/tasks/manage-kubernetes-objects/kustomization/

Kustomize is a standalone tool to customize Kubernetes objects through a kustomization file.

Since 1.14, Kubectl also supports the management of Kubernetes objects using a kustomization file. To view Resources found in a directory containing a kustomization file, run the following command:

kubectl kustomize <kustomization_directory>
To apply those Resources, run kubectl apply with --kustomize or -k flag:

kubectl apply -k <kustomization_directory>

##Our approach in dev, test, etc dirs

Create an alias for simplicity
`$ alias k="kubectl"`

Move to the dev dir
`$ cd ./dev/`

The generated ConfigMap can be examined with the following command:
`$ kubectl kustomize ./`

Use the -k flag to specify the directory (by default k8 will look for a kustomization.yml file)
`$ k apply -k ./`

Verify it worked by checking the namespaces and running pods 
`$ k get pods --namespace=backend`

Delete the deployment
`$ k delete -k ./`


