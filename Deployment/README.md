
## Deployment


## Build Docker image

    # Remeber to add the container registry name
    
    $ docker build -t <My-container-Registry>/my_api_app -f Deployment/Dockerfile .
    
## push Docker image 

    $ docker push <My-container-Registry>/my_api_app
    

## Deployment to MiniKube

    # Consider having Minikube running on local machine , please remember to change the container regiestry in the deployment file

    $ kubectl create -f Deployment/myapi_app_deployment.yml

    $ kubectl create -f ../Deployment/myapi_app_service.yml

