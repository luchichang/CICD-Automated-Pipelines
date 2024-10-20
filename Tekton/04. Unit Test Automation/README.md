# 04 Unit Test Automation

## Description,


## Objective,
- Installing __flask8 task__ from the Tekton CD catalog
- Describe and pass the parameters required to use the __flask8 task__
- use the __flask8 task__ in the tekton pipeline to lint the code
- create a test task from the scratch and use it in the pipeline 


![parallel running Tekton Tasks](image.png)

## Pre-requisite


## Environment Setup
- follow the root readme file instructions to install and setup tekton 
- clone the repo

- Navigate to the project 
```bash
  cd CICD-AUTOMATED-PIPELINES/Tekton/04. Unit Test Automation
```
- open the folder in your preferred IDE


## Steps,
- Establish the tasks
 ```bash
   kubectl apply -f tasks.yaml
 ```
install task from the tekton catalog / tekton hub
 ```bash
   tkn hub install task git-clone
 ```

- list the created tasks
```bash
  tkn task ls
```
- create the Persistent Volume Claim(PVC)
```bash
  kubectl apply -f pvc.yaml
```

- install the __flake8__ task from tekton catlog
```bash
  tkn hub install task flake8
```

- configure the pipeline with the configured flake8 task
```bash
  kubectl apply -f pipeline.yaml
```

- creating the nosetest Task CRD to the k8s cluster
```bash
  kubectl apply -f tasks.yaml 
```

- configure the pipeline with the configured nosetest task
```bash
  kubectl apply -f pipeline.yaml
```


## Executing the pipeline
- run the Pipeline by creating the pipeline run
```bash
  tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch="main" \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    --showlog
```
- list the pipeline run
```bash
  tkn pipeline ls 
```

