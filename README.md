#Udacity Refactoring Monolith to Microservices
Steps:
1. Run `npm i` in udacity-c3-frontend, udacity-c3-restapi-feed and udacity-c3-restapi-user
2.Head over to udacity-c3-deployment/docker and run:
    i. Build the images: `docker-compose -f docker-compose-build.yaml build --parallel`
    ii. Push the images: `docker-compose -f docker-compose-build.yaml push`
    iii. Run the container: `docker-compose up`
3. Head over to `localhost:8100` to test the application.

##To deploy on kubernetes:
1.Head over to udacity-c3-deployment/k8s and run the following commands:
    i. `kubectl apply -f env-configmap.yaml`
    ii. `kubectl apply -f env-secret.yaml`
    iii. `kubectl apply -f aws-secret.yaml`
    iv. `kubectl apply -f backend-feed-deployment.yaml`
    v. `kubectl apply -f backend-feed-service.yaml`
    vi. `kubectl apply -f backend-user-deployment.yaml`
    vii. `kubectl apply -f backend-user-service.yaml`
    viii.`kubectl apply -f frontend-deployment.yaml`
    ix. `kubectl apply -f frontend-service.yaml`
    x. `kubectl apply -f reverseproxy-deployment.yaml`
    xi. `kubectl apply -f reverseproxy-service.yaml`
2.to apply proxy forwarding run the following command:
    `kubectl port-forward service/frontend 8100:8100 & kubectl port-forward service/reverseproxy 8080:8080 &`
3.Head over to `localhost:8100` to test the application.
