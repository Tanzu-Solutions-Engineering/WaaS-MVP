This exercise will verify your local Harbor is working and get you familiar with it.  

Open the Harbor UI to your project by clicking the link below.
```dashboard:open-url
url: https://harbor.{{ ingress_domain }}/harbor/projects/{{ harbor_project_id }}/repositories
```

If you need to login, use the following credentials:
UN: `admin`
PW: `{{ ENV_HARBOR_PASSWORD }}`

## Login to your local Harbor with Docker 🔧
```terminal:execute
command: docker login harbor.{{ ingress_domain }}
```

Pull down a test image for this project 
```terminal:execute
command: docker pull cmccarth/ticket-function
```

Tag an image for this project 
```terminal:execute
command: docker tag cmccarth/ticket-function harbor.{{ ingress_domain }}/{{session_namespace}}/test/ticket-function
```

Push an image to this project 
```terminal:execute
command: docker push harbor.{{ ingress_domain }}/{{session_namespace}}/test/ticket-function
```

## Verify the image is in Harbor by viewing the repositories for the test project 🔧

Go to Projects and select the test project > then the ticket-function repository.

You should now see your image present.
