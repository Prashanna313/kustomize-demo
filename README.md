## Kustomize Demo
Kustomize is a powerful configuration management tool designed to streamline the process of customizing Kubernetes resource configurations. Unlike traditional templating solutions, Kustomize leverages a pure YAML approach, allowing you to manage and deploy Kubernetes resources with ease and flexibility.

### Key Features
- Layered Configuration Management: Organize your configurations into a series of overlays, enabling you to customize and manage variations across different environments effortlessly.
- Declarative Syntax: Define your configurations in YAML, ensuring your deployments are consistent, repeatable, and easy to understand.
- No Templating Language: Avoid the complexity of traditional templating systems. With Kustomize, you work directly with YAML, enhancing readability and maintainability.
- Built-in Transformers and Generators: Use a rich set of built-in functions to modify and generate resource configurations, ensuring your manifests are always up-to-date and relevant.
- Extensibility: Easily extend Kustomize with plugins and custom transformers to meet your specific needs.
### Check your version of kubectl
```
kubectl version
```
*If you have 1.21 or above of kubectl you will have access to kubectl kustomize which is the recommended method. If you aren't on version 1.21 or above, upgrade kubectl.

*You could also download/use the 'kutomize' binary seperatly but the cmds are different.


### Viewing Kustomize Configs - (Using kubectl kustomize integration)
```
kubectl kustomize src/overlays/dev/
kubectl kustomize src/overlays/prod/
```

### Applying Kustomize Configs - (Using kubectl kustomize integration)
```
kubectl apply -k overlays/dev/
kubectl apply -k overlays/prod/
```
Note: if you get field is immutable error, check your configuration and try deleting the resources then applying again.


### Creating Namespaces if you dont have them already
```
kubectl create namespace dev; 
kubectl create namespace test;
kubectl create namespace prod;
```


### Accessing the application
```
minikube service kustom-mywebapp-v1
minikube service kustom-mywebapp-v1 -n dev
minikube service kustom-mywebapp-v1 -n test
minikube service kustom-mywebapp-v1 -n prod
```

### References:
https://github.com/kubernetes-sigs/kustomize/blob/master/README.md
https://kubectl.docs.kubernetes.io/guides/config_management/offtheshelf/
