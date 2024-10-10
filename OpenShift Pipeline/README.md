# Creating the Openshift CICD Pipeline Abstraction of Tekton

## Description,

## Objective,
* Create a CICD Workflow using the Openshift Pipeline
* Add Parameters to task created using Openshift Pipelines
* Add a Workspace and persistent volume claim in the Openshift UI
* Add Task that clone the Github Repository 
* Lint the Source Code
* run unit test 
* and deploy application to the openshift cluster

## Environment Setup
* Ensure you're connected to the Openshift Cluster
```bash
   oc config current-context
```
