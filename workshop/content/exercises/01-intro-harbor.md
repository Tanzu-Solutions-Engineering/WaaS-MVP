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
Now, enter the admin username
```terminal:input
text: admin
```

Next, enter the admin password
```terminal:input
text: {{ ENV_HARBOR_PASSWORD }}
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
Go back to your Harbor tab in the browser, and and refresh the page.  You should now see a repository entry in the table view that has the suffix "test/ticket-function."  Click on this entry in the table.

The next view shows your repository artifacts.  OCI images are uniquely identified by repository name, as well as a SHA256 value that is unique to each image version.  Additionally, images may be tagged with human readable values like "latest" to prevent having to refer to those long SHA256 values when you want to reference an image.

Validate your image SHA value by first going back to the terminal session we executed the `docker push` in.  The output should show something like the following:

![Docker output showing SHA256](/images/docker-push-output.png)

Check the first 8 characters of the SHA in the output against the value shown in Harbor for that repository artifact.  Those characters should match.