This file describes a test to integrate different tools to establish an open source metadata catalog with lineage.

# Environmnent
This test is carried out on an Ubuntu 18.04 personal laptop. It should be replicable on most Linux servers.

# Install

## Install Git (if not already available)
...
## Install Docker (if not already available)
...
Create a Docker folder: `mkdir Docker`
Move to the Docker folder: `cd Docker`  

## Install Amundsen (bundled with Neo4J)
Clone Amundsen master branch from Github: `git clone --recursive https://github.com/lyft/amundsen.git`
Populate the database with dummy data (4 fake tables included in Amundsen repo)  
`cd amundsen`  
`cd amundsendatabuilder`  
`python3 -m venv venv`  
`pip3 install -r requirements.txt`  
`python3 setup.py install`  
`python3 example/scripts/sample_data_loader.py`  

Go back to ~/Docker/Amundsen: `cd ..`
Launch Amundsen: `docker-compose -f docker-amundsen.yml up`  

>Troubleshooting: if the former ends with an error, extend the virtual memory available to Elasticsearch (cf. https://github.com/lyft/amundsen/issues/77): `sudo sysctl -w vm.max_map_count=262144`  

Connect to the interface with your web browser to check that it dispays something: http://localhost:5000  
A Neo4J instance was installed along with Amundsen. Launch the Neo4J web interface: http://localhost:7474/ 

## Install ArcadeAnalytics and connect it to Neo4J 
Go back to ~/Docker if you were still in ~/Docker/Amundsen: `cd ..`  
Clone Amundsen 'recipies' branch from Github:   `git clone https://github.com/ArcadeData/arcadeanalytics-recipes`  
Get into the folder: `cd arcadeanalytics-recipes`  
Launch the app: `docker-compose -f recipes/arcade-standalone.yml up`  
Ouvrir l'url: http://localhost:8080/  
Login with the defalut user : login as *user* with password *user*  
*Add here the procedure to change admin login and create users*   
Click on the 'Datasources' tab and add a new datasource and fill-in:   
- Name: neo4j-amundsen (or another name you like)
- Description: Accessing Amundsen data (or another description you prefer)
- Type: Neo4J
- Server: your local IP (get it with `ifconfig` command)
- Port: 7687
- Database: neo4j (n'importe mais doit comporter quelque chose)
- codes : admin, admin
- Workspace: user default

# Run

## Neo4J


# Backup
