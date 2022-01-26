This exercise will verify your local Harbor is working and get you familiar with it.  

Open the Harbor UI to your project by clicking the link below.
```dashboard:open-url
url: https://harbor.{{ ingress_domain }}/harbor/projects/{{ harbor_project_id }}/repositories
```

If you need to login, use the following credentials:
UN: `admin`
PW: `{{ ENV_HARBOR_PASSWORD }}`

##



## In Harbor create a project named test 🔧

Go to Projects and click the + New Project button.

Set Project Name to `test`.

Set Access Level to Public (unless you intend to make it private and require login).

Leave Storage Quota at the default -1 GB.



## Login to your local Harbor with Docker 🔧
```
docker login core.harbor.domain
```


Pull down a test image for this project 
```
docker pull cmccarth/ticket-function
```



Tag an image for this project 
```
docker tag cmccarth/ticket-function core.harbor.domain/test/ticket-function
```


Push an image to this project 
```
docker push core.harbor.domain/test/ticket-function
```


## Verify the image is in Harbor by viewing the repositories for the test project 🔧

Go to Projects and select the test project > then the ticket-function repository.

You should now see your image present.
