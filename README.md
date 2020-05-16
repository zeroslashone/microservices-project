# Udacity Refactoring Monolith to Microservices

### Steps:
1. Run `npm i` in udacity-c3-frontend, udacity-c3-restapi-feed and udacity-c3-restapi-user
2.Head over to udacity-c3-deployment/docker and run:
    - Build the images: `docker-compose -f docker-compose-build.yaml build --parallel`
    - Push the images: `docker-compose -f docker-compose-build.yaml push`
    - Run the container: `docker-compose up`
3. Head over to `localhost:8100` to test the application.

## To deploy on kubernetes:
### Steps:
4.Head over to udacity-c3-deployment/k8s and run the following commands [in the same order]
5. kubectl apply -f env-configmap.yaml
6. kubectl apply -f env-secret.yaml
7. kubectl apply -f aws-secret.yaml
8. kubectl apply -f backend-feed-deployment.yaml
9. kubectl apply -f backend-feed-service.yaml
10. kubectl apply -f backend-user-deployment.yaml
11. kubectl apply -f backend-user-service.yaml
12. kubectl apply -f frontend-deployment.yaml
13. kubectl apply -f frontend-service.yaml
14. kubectl apply -f reverseproxy-deployment.yaml
15. kubectl apply -f reverseproxy-service.yaml
    
16.to apply proxy forwarding run the following command:
    `kubectl port-forward service/frontend 8100:8100 & kubectl port-forward service/reverseproxy 8080:8080 &`
16.Head over to `localhost:8100` to test the application.
