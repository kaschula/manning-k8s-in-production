# Part 1 - Deliverables

1. Create the yaml models 4 the follwing four application images
    1. widgetario/products-db:21.03 (Dockerfile)
    2. widgetario/products-api:21.03 (Dockerfile)
    3. widgetario/stock-api:21.03 (Dockerfile)
    4. widgetario/web:21.03 (Dockerfile)

    ```
    ./pod-products-api.yaml
    ./pod-products-db.yaml
    ./pod-stock-api.yaml
    ./pod-widgetario-web.yaml

    ```


2. Deploy them into the cluster

```
// apply object files
kubectl apply -f pod-product-db.yaml
kubectl apply -f pod-product-api.yaml
kubectl apply -f pod-widgetario-web.yaml
kubectl apply -f pod-stock-api.yaml
```

3. Verify the pods are running the correct containers, the products-apis will fail to start because there is no networking to the DB.

```
// verify pods are running
kubectl get pods

```

4. Print the logs

```
// verify logs
kubectl logs products-db --all-containers
kubectl logs products-api --all-containers
kubectl logs stock-api --all-containers
kubectl logs products-db --all-containers
```

5. verify the pods restart by sending a kill command to the stock api, the container should exit and a new one start

```
kubectl exec -it stock-api -- /bin/bash -c "kill 1"
```