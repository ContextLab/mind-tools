# mind-tools

This is a Docker container pre-built with python tools you can use for data analysis and workshop demos during the [Methods in Neuroscience at Dartmouth](https://summer-mind.github.io/) summer school.

## Contains

[Scientific python stack](https://www.scipy.org/about.html) ([Anaconda version](https://www.continuum.io/what-is-anaconda); e.g. numpy, pandas)   
[Brain Imaging Analysis Kit](http://brainiak.org/)  
[Neurolearn Toolbox](http://neurolearn.readthedocs.io/en/latest/)  
[PyMVPA](http://www.pymvpa.org/)  
[Hypertools](http://hypertools.readthedocs.io/en/latest/index.html)  
[MNE toolbox](https://martinos.org/mne/stable/index.html)  
[Deep dish](https://github.com/uchicago-cs/deepdish)  
[Nelpy](https://github.com/eackermann/nelpy)  
[Dask](https://dask.pydata.org/en/latest/)  
[Nilearn](http://nilearn.github.io/)  



## Usage instructions  

1. Install the Docker daemon:
    - [OSX](https://docs.docker.com/docker-for-mac/install/#download-docker-for-mac)
    - [Windows](https://docs.docker.com/docker-for-windows/install/)
    - [Ubuntu](https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/)
    - [Debian](https://docs.docker.com/engine/installation/linux/docker-ce/debian/)
2. Launch the Docker daemon and adjust the preferences to allocate sufficient resources (e.g. > 4GB RAM)
3. Download the docker image from [docker hub](https://hub.docker.com/r/ejolly/mind-tools/) and build it:
    - Open a terminal and enter:
    - `docker pull ejolly/mind-tools`
4. Create a new persistent interactive container (*only required once*)
    - The command below will create a new container that will map your computer's `Desktop` to `/mnt` within the container, so that location is shared between your host OS and the container. You can change what folder you want to share by editing the path in the command below. The command will also share port `9999` with your host computer so any jupyter notebooks launched from *within* the container should not conflict with other notebooks you may already have running. Container notebooks will be accessible at `localhost:9999` in your browser
    - `docker run -it -p 9999:9999 --name MIND -v ~/Desktop:/mnt ejolly/mind-tools `
    - You should now see the `root@` prefix in your terminal, if so you've successfully created a container and are running a shell from *inside*!
5. Execute commands as desired:
    - Switch Python environment:
        - Python 3.6 is active by default; if you want to switch to
          Python 2.7, type `source activate py27`
    - Launch a jupyter notebook:
        - `jupyter notebook --port=9999 --no-browser --ip=0.0.0.0 --allow-root`
        - Navigate to `localhost:9999` in your browser to access the notebook
    - Open ipython from the command line
        - `ipython` at the command prompt
    - Run bash commands, e.g
        - `which python`
6. Close container with `ctrl + d`
7. Reopen container with (in a terminal on your own computer from any directory):
    - `docker start MIND && docker attach MIND`


## Helpful commands

- See what docker images you have downloaded and can be used to create new containers:  
	+ `docker images`  
- See running container dockers:  
	+ `docker ps`  
- See all docker containers you have created (including those not running):  
	+ `docker ps -a`
- Startup and connect to previously created container:
	+ `docker start yourContainerName`
	+ `docker attach yourContainerName`
- Delete a docker container:  
	+ `docker rm yourContainerName`  
- Delete a docker image:  
	+ `docker rmi yourImageName`  
- Stop a running container:  
	+ `docker stop yourContainerName`
- Execute a new command in an existing docker container
	+ `docker exec yourContainer command`
- Delete all containers that are no longer running:
	+ `docker rm $(docker ps -aq -f status=exited)`
- Force delete ALL containers
	+ `docker rm -f $(docker ps -aq)`

## Getting assistance

Free free to contact Eshin or Matteo regarding any issues you run into when setting up or using this container:

Eshin:  
@ejolly (Slack)  
eshin.jolly@gmail.com  

Matteo:  
@mvdoc (Slack)  
mvdoc.gr@dartmouth.edu
