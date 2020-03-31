This file describes a test to integrate different tools to establish an open source metadata catalog with lineage.

# Environmnent
This test is carried out on an Ubuntu 18.04 personal laptop. It should be replicable on most Linux servers.

# Install

## Install Git (if not already available)
...
## Install Docker (if not already available)
...

Create a Docker folder:
`mkdir Docker`

Move to the Docker folder
`cd Docker`

## Install Amundsen
Clone Amundsen master branch from Github :
`git clone --recursive https://github.com/lyft/amundsen.git`

Populate the database with dummy data (4 fake tables included in Amundsen repo)
`cd amundsen`  
`cd amundsendatabuilder`  
`python3 -m venv venv`  
`pip3 install -r requirements.txt`  
`python3 setup.py install`  
`python3 example/scripts/sample_data_loader.py`  

Check that Amundsen works.
`cd ..` (to get back to ~/Docker/Amundsen)
`docker-compose -f docker-amundsen.yml up` Launch Amundsen

Troubleshooting: if the former ends with an error, extend the virtual memory available to Elasticsearch cf. https://github.com/lyft/amundsen/issues/77)  
`sudo sysctl -w vm.max_map_count=262144`

Connect to the interface with your web browser to check that it dispays something  
http://localhost:5000 

# Run


# Backup
