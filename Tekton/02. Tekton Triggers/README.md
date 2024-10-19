# Tekton trigger

## description,
  running the pipeline based on the external even trigger. Running a pipeline manually has limited uses. in this project we will create a tekton trigger to cause a pipeline run from external events like changes made to the github repo

  ## Objective
  * create an __Event Listener__, __Trigger Binding__, __Trigger Template__ 
  * state how to trigger a deployment when changes are made to github

## pre-requisite
- Event Listener
- Trigger Binding 
- Trigger Template 

## steps,
  * create the tasks
    ```bash
      kubectl apply -f tasks.yaml
    ```     
  * list the tekton tasks
    ```bash
      tkn task ls
    ```
  * create the tekton pipeline
    ```bash
      kubectl apply -f pipeline.yaml
    ```
  * list the created tekton pipeline
    ```bash
      tkn pipeline list
    ```
  * create Eventlistener
    ```bash
       kubectl apply -f eventlistener.yaml
    ```
  * list the eventlister
    ```bash
      tkn eventlistener list
    ```
  * create the Trigger binding
    ```bash
      kubectl apply -f triggerbinding.yaml
    ```
  * list the created Trigger binding
    ```bash
       tkn triggerbinding list
    ```