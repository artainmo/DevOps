# Gitlab

## Table of contents
- [Free tutorials](#Free-tutorials)
  - [GitLab](#GitLab)
    - [GitLab CI/CD Pipeline](#gitlab-cicd-pipeline)
    - [GitLab Runner on Kubernetes](#GitLab-Runner-on-Kubernetes)
- [Resources](#Resources)

## Free tutorials
### GitLab
GitLab is a single application that covers the whole DevOps lifecycle while allowing collaboration and ease of use. At its core it is a place to store repositories with git version control, however contrary to github it holds a lot of additional features.

Here are some of the features it holds:
* Manage containers and clusters such as [docker images](https://github.com/artainmo/DevOps/tree/main/docker#Basics) or [kubernetes charts](https://github.com/artainmo/DevOps/tree/main/kubernetes#helm).
* Tools to facilitate the creation of [CI/CD pipelines](https://github.com/artainmo/DevOps#CICD-pipelines).
* It can [monitor](https://github.com/artainmo/DevOps#Monitoring) your code with Prometheus.
* Like github it also has features such as pull requests, view prior commits...
* Organize code with for example labels.
* Project management tools.
* GitLab also allows the use of third party addons (integrations), making it extensible and providing even more features.<br>

#### GitLab CI/CD Pipeline
**GitLab CI/CD** includes a subset of GitLab's features that allow DevOps practices such as [continuous integration, continuous delivery, continuous deployment](https://github.com/artainmo/DevOps#CICD-pipelines).<br>
Thus through a **GitLab pipeline** we can automatically build, test and deploy our software.<br>
A GitLab pipeline is defined inside a file named '.gitlab-ci.yml' that lives at the root directory of a gitlab project.<br>
A GitLab pipeline consists of Jobs (describes the tasks that need to be done) and Stages (defines the order in which jobs will be completed). Thus a gitlab pipeline consists of a set of instructions for a program to execute. The program that executes those instructions is called **GitLab Runner**, which can run on local host, VM or docker container.<br>
The CI/CD pipeline execution is triggered each time a commit is pushed on the associated repository. 

On GitLab project repository, see left page and go to 'CI/CD -> Editor', than create a new pipeline.<br>
Now a pipeline template has been generated you can edit. Let's look at it and understand it.
<pre>
#At top file 'stages' section is defined which defines the order of instructions (aka jobs).
stages:
  - build
  - test
  - deploy

#Subsequently in file all those jobs will be defined.

 build-job:                                     #This is the name we give to a job.
  stage: build                                  #Here we define the stage the job is associated with, namely build, which runs first.
  script:                                       #Here we can define the shell commands that the job executes.
    - echo "Compiling the code..."
    - echo "Compile complete."

unit-test-job:
  stage: test                                   #This job runs in the test stage. It only starts when the job in the build stage completes successfully.
  script:
    - echo "Running unit tests..."
    - echo "Code coverage is 90%"

lint-test-job:
  stage: test                                   #Multiple jobs can be associated with a particular stage. It can run at the same time as unit-test-job (in parallel).
  script:
    - echo "Linting code..."
    - echo "No lint issues found."

deploy-job:      
  stage: deploy                                 #This job runs in the deploy stage. It only runs when both jobs in the test stage complete successfully.
  environment: production                       #Environments describe where code is deployed. Define environments by going on project repository, see left side of page and go to 'Deployments -> Environments'.
  script:
    - echo "Deploying application..."
    - echo "Application successfully deployed."
</pre>
After committing the file, the pipeline will start running instantly. It will basically perform the jobs on the code inside the repository and notify if a job failure occurs.<br>

When files are generated inside one stage they won't be accessible by the next stages because each stage uses its own workspace environment. To resolve this issue we can define the files we would want to pass to the next stage.
```
build-job:       
  stage: build
  script:
    - echo "Compiling the code..."
    - echo "Compile complete."
  artifacts:                                    #Defines files generated in this job that should be shared with downstrean jobs. After the pipeline completes, those files can be downloaded to local machine.
    paths:
      - <pathToFile>
```

If we need specific dependencies to run our pipeline we can define an image at top of file. The workspace each stage runs in will pull that docker image. If we need python we can define at top file `image: python` for example.<br>
We can also define environment variables at top of file to be available in each stage workspace.

Apparently 'GitLab Agents' are able to synchorinize a running application with a repository. Thus they act similar as a 'deploy' job in a GitLab CI/CD pipeline.

#### GitLab Runner on Kubernetes
'GitLab runner' executes [CI/CD pipeline instructions](#gitlab-cicd-pipeline). However it is only necessary when using a 'local gitlab instance'. When using 'gitlab.com' the '.gitlab-ci.yml' is enough after validating your credit card.<br>
'[helm](https://github.com/artainmo/DevOps/tree/main/kubernetes#helm)' is a package manager for kubernetes that in this case allows us to install a GitLab runner made for Kubernetes.<br>
The GitLab runner is made for kubernetes because it uses the 'Kubernetes Executor', which allows each CI/CD pipeline instruction (job) to be run in its own pod, inside chosen namespace, those jobs will be able to use kubectl commands.

```
helm repo add gitlab https://charts.gitlab.io
helm install --namespace <KUBERNETES_NAMESPACE_NAME> gitlab-runner -f <CONFIG_VALUES_FILE> gitlab/gitlab-runner
```
The <CONFIG_VALUES_FILE> should equal the path towards your 'values.yaml' configuration file. This file contains values that will be passed to the created chart.<br>
Here we have as required config value 'gitlabUrl'. This value can simply equal 'gitlab.com' if you are not running a private GitLab server.<br>
Second as required config value we have 'runnerRegistrationToken'. This value can be found in the gitlab repository you want to associate with a GitLab CI/CD pipeline. When on repo, go to (Settings -> CI/CD -> Runners), under 'Specific runners' you can find 'Register the runner with this URL: \<gitlabUrl\>. And this registration token: \<runnerRegistrationToken\>.'.<br>
Instead of using a 'values.yaml' file you can start the gitlab-runner like this.
```
helm install --namespace <KUBERNETES_NAMESPACE_NAME> gitlab-runner \
      --set gitlabUrl=<URL>,runnerRegistrationToken=<TOKEN> \
      gitlab/gitlab-runner
```
After the GitLab runner has been created you can visualize it like this.
```
helm status gitlab-runner
kubectl describe pods gitlab-runner --namespace=<KUBERNETES_NAMESPACE>
```
On gitlab.com associated project repo see (Settings -> CI/CD -> Runners -> Specific runners -> Available specific runners).

Now that the runner is registered, it should execute the associated repository's [CI/CD pipeline instructions](#gitlab-cicd-pipeline).

## Resources
[GitLab - What is GitLab?](https://www.youtube.com/watch?v=MqL6BMOySIQ)<br>
[LevelUpTuts - What Is GitLab?](https://www.youtube.com/watch?v=gbJUasioKiI)<br>
[GitLab CI CD Pipeline Tutorial | Introduction | 2022](https://www.youtube.com/watch?v=mnYbOrj-hLY)<br>
[GitLab CI CD | Install and Configure GitLab Runner on Kubernetes with Helm](https://www.youtube.com/watch?v=0Fes86qtBSc)
