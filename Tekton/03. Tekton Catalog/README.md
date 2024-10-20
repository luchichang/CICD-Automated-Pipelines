# Tekton Catalog

## Description

## Objective, 
- use the tekton cd Catalog to install the predefined or community written tasks
- Describe the Parameters required to use the git clone task
- Use the git-clone task in a Tekton pipeline to clone your Git Repository 

## pre-requisite
- Tekton Catalog
- Tekton Workspace
     A workspace is a disk volume that can be shared across tasks. The way to bind to volumes in Kubernetes is with a Persistent Volume Claim
- Persistent Volume
- Persistent Volume Claim
- Name Spaces

![Persistent Volume](image.png)

NOTE: for creating workspace in Persistent volume claim we need to create storage class first so it can be referenced in the __storageClassName__ in the pvc 

to create the default storage class execute
```bash
  kubectl get storageclass
```

## Enviornment Setup

## steps,
* Install the task from the tekton hub 
URL: https://hub.tekton.dev/tekton/task/git-clone
via kubectl mainfiest file: kubectl apply -f https://api.hub.tekton.dev/v1/resource/tekton/task/git-clone/0.9/raw
via tkn cli: tkn hub install task git-clone


## Run the pipeline
- run the pipeline manually
```bash
  tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch="main" \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    --showlog
```