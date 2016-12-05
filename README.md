# kairx-resident-analysis
Integrating Qualtrics and Optimizely data to help provide insight into the various studies underway

![mail](images/logo.png)

## About
The purpose of this repo is to provide initial insights into the data captured as part of the KaiRx studies. **Note: all patient related data in this repository is simulated and does not represent any actual individual.**

## Environment
We will use one environement (JupyterLab) for development of notebooks and another environment (Jupyter) for deployment of our notebooks.

#### Deploy environment
All work will be conducted using [Jupyter's Data Science Notebook Docker Stack](https://github.com/jupyter/docker-stacks/tree/master/datascience-notebook). Once our repo is cloned and `pwd` is pointed toward this repositories parent directory, the following command can be used to bring up our environment:
>`docker run --restart always -d -p 8877:8888 -v $(pwd)/jupyter:/home/jovyan/work jupyter/datascience-notebook`

We will use this environment locally (http://127.0.0.1:8877) for development and will stand up a hosting server for our collaborators to view and interact with the results (http://colab-sbx-97.oit.duke.edu:8877).

#### Develop Environment
```
docker build -t jupyterlab/kairx ./docker/.
```

To instantiate the environment:
```
docker run --name kairx -d -v $(pwd)/jupyter:/home/newuser -p 8000:8000 jupyterlab/kairx
docker exec -it kairx bash
passwd newuser
```
An interactive prompt will now open, choose a passwd for the newuser. After entering the password and confirming, you can exit the interactive session:

```
exit
```

kairx development is now available for use at: http://localhost:8000.
