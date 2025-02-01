# Skills Evaluation Test

The goal of this process is evaluate candidates overall skills on:

1. General RESTful service architecture
2. Coding and debugging
3. Usage of operation tools

Those abilities will be evaluated based on a series of problems that need to be solved
based on a RESTful service skeleton intentionally incomplete to create a scenario
where the candidate may be able to complete the service.

Those challenges give to the candidate the opportunity to explore solutions on his/her own,
not necessarily tied to a predetermined answer.

## Evaluation

First of all, thank you for your time and your interested in joining our team. We tried to elaborate
a process of technical evaluation that gives you freedom of thinking at the same time that
allows us to understand better your technical skills.

Before you begin, please ensure you read over the following guidelines:

1. You received versions of the same service in different programming languages. Choose ONE!
Preferably the one that you are more comfortable with.
2. Create a public repo in Github and upload the source code with the version you chose.
3. For each task, try to put everything together in one single Pull Request. This will make it easier for us
to review what you have done.

**Remember!**

* There are no expectations that you will complete ALL of them.
* The idea here gauge your knowledge with the tools we use on a regular basis.
* Try to complete tasks that you are more comfortable first. Leave the ones you are less familiar with.

Qlik's Culture and Talent team will contact you to setup a virtual meeting
where you will be required to share your screen and participate in a code review of your PRs with
members of Qlik's team. As with any code review, we will be inquiring about design choices,
coding styles, challenges and potential enhancements. Be prepared to demo a running version of the service.

## The scenario

We have this very simple RESTful service. It is used internally by the team to create
a library of Palindromes. Someone used to have fun writing those once in a while and it
kind of became a tradition. Unfortunately, whoever started this project never finished it
completely.

The project has 5 endpoints:

| METHOD | Endpoint              | Description                            |
|--------|-----------------------|----------------------------------------|
| GET    | /api/v1/messages      | Returns all messages                   |
| GET    | /api/v1/messages/[ID] | Returns a specific record              |
| POST   | /api/v1/messages      | Creates a new record                   |
| DELETE | /api/v1/messages/[ID] | Deletes an existing record             |
| GET    | /api/v1/health        | Get health                             |

## Tasks

The following tasks have been assigned to you to complete on this project:

1. **Where is the palindrome?:** This service is NOT doing what is supposed to. It records several
messages but it doesn't validate if they are Palindromes. Add a boolean flag to the Message
models where it says whether or not it IS a palindrome. Hint: create a method that validate if the
word IS a palindrome before it is saved.
2. **Dockerize it:** Package the service in a docker file and make sure the service is accessible locally.
3. **Github Workflow:** Create a github workflow to build the docker image and push it to a registry of your choice.
4. **Orchestration:** If you completed task #4, it is time to make this service
cloud available. Implement this using Kubernetes.
   1. Add a `health` endpoint to the service to reflect the status of the service.
   2. Run 1 instance of the service in a k8s cluster
   3. (optional) Wrap your kubernetes resource in a helm chart.

**BONUS TASK**
For additional visibility we want a `/metrics` endpoint implemented exposing metrics than be scraped by a
Prometheus server. You have to use [prometheus libraries](https://prometheus.io/docs/instrumenting/clientlibs/)
