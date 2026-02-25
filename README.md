1) Démarrer Minikube avec Docker:
	-> minikube start --driver=docker

2) Create a kubernetes deployment from a Docker image
	-> kubectl get nodes
	-> kubectl create deployment myservice --image=efrei/myservice:1

3) Check the pod:
	-> kubectl get pods -o wide
	
4) Expose HTTP and HTTPS route using NodePort
	-> kubectl expose deployment myservice --type=NodePort --port=8080
	
   Retrieve the service address:
	-> minikube service myservice --url 
5) Scaling and load balancing
   * Check if the myservice deployment is running:
	-> kubectl get deployments
   * How many instance are actually running:
	-> kubectl get pods
   * Start a second instance:
        -> kubectl scale --replicas=2 deployment/myservice
        -> kubectl get deployments
     and
        -> kubectl get pods
6) Creating a Service of type LoadBalancer
   * Check if the myservice deployment is running:
   	-> kubectl get deployments
   * If a service is running in front of the deployment you must delete this service first in ordre to create a new one of kind LoadBalancer. So retreive the service using:
	-> kubectl get services
   * And delete it:
	-> kubectl delete service serviceName
	-> kubectl expose deployment myservice --type=LoadBalancer --port=8080
	-> minikube service myservice --url
   * Test in your web browser
   
   
minikube service myservice2 --url
# puis teste l’URL affichée avec curl .../
http://192.168.49.2:31281
