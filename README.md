Greetings!

Thank you for checking out the new config and repository I have created. 

The goal of this prohect was to create an application that was configurable with google managed sidecars to export prometheus metrics into Cloud operations.
This method is the managed version of querying in prom QL without the overhead of managing and provisioning a prometheus deployment.

I did this in responce to a call from a recuiter and in inerview prepation for a firm reliant on cloud run applications in need of pipelines. 

Currently the unwrapped docker image in the repo is designed for deployment with monitoring through cloud run, Thought this image is capable of deploying on kubernetes.
In My next iteration I will adjust the go file for this to deploy in kubernetes with compatibility with a standard prometheus instance. 

I will also be constructing a cloud run pipleing for the image in this configuration.

---


Sample Commands to build and push and deploy the image are below, as are the helm commands if you have a kuberenetes cluster:

---
Cloud build Construction and Deployment:


>
docker build -t europe-central2-docker.pkg.dev/lizzos-project/run-gmp/lizzo .
>
docker push europe-central2-docker.pkg.dev/lizzos-project/run-gmp/lizzo
>
>->"Download the Yaml for the sidecar and navigate to it's working directory. configure the image to the name of your image"
>
gcloud run services replace run-service-simple.yaml --region=europe-central2
>->"Tear Down"
>
gcloud run services delete my-cloud-run-service --region=europe-central2
>>>

---

Kuberenetes Helm Deployment -> "If you want to adjust my preconfigured paramiters; copy the values.yaml and helm install pointing to a local copy with your configured settings.":


>
helm repo add demon https://storage.googleapis.com/berons-helm/
>
helm repo update
>
helm install demon demon/baldhead-chart --version 1.0.0
>->"Teardown"
>
helm uninstall demon
>>>

