LAB - Markdown Sample
=====================

Sample workshop content using Markdown formatting for pages.

# Simple Install
If you already have the Educates operator installed and configured, to
deploy and view this sample workshop, run:

```
kubectl apply -f https://raw.githubusercontent.com/Tanzu-Solutions-Engineering/WaaS-MVP/main/resources/workshop.yaml
kubectl apply -f https://raw.githubusercontent.com/Tanzu-Solutions-Engineering/WaaS-MVP/main/resources/training-portal.yaml
```

This will deploy a training portal hosting just this workshop. To get the
URL for accessing the training portal run:

```
kubectl get trainingportal/lab-markdown-sample
```

The training portal is configured to allow anonymous access. For your own
workshop content you should consider removing anonymous access.

# Initial portal password
If you want to have attendees use an initial password before registering, you can specify that password using the following command (changing `REPLACEME` with your preferred password):
```
ytt -f kapp/overlays/training-portal.yaml -f resources --data-value password=REPLACEME | k apply -f -
```
