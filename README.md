# Description
Jenkins server for continous delivery running on *docker* with a master container and two slave agents, wich will be connected to master for do job tasks.

## To Use
Firstly you must have installed [docker](https://docs.docker.com/install) on your system. Then you can build the project with 'docker-compose build' and wait to pull and build docker images. When process finish you must init and config the server from your browser on 'http://localhost:8080'. You should enter initial password wich will be in 'jenkins_home/secrets/initialAdminPassword' folder, then server prompt you for create admin account.

After that, you have to create and configurate the two agents. First you have to access to 'Manage Jenkins > Manage Nodes > New Node' and name it with 'agent1'. Then you must config the agent with:
- Remote root directory: /home/jenkins
- Launch method: Launch agent via Java Web Start
When you save the agent, you have to copy secret token for the agent. You must go inside the *agent1* row on node list and copy '--secret' value and paste into docker-compose.yml 'JENKINS_SECRET' config for the agent1. After the process you must repeat it for the 'agent2'.
~~~~
# Build project
docker-compose build

# Config master server
.....

# Run project
docker-compose up -d
~~~~

## Running slaves containers
For running slaves containers you must execute:
~~~~
# Running n slaves ('n' is the slaves you want to run)
docker-compose scale worker=n
~~~~

Remember you must above configure slaves  

## Thanks
Thanks to my jedi partners: :neckbeard: Kraken, :japanese_goblin: Garcilaso, :person_with_blond_hair: Markes, :godmode: Otto, :smirk: Ivan y :sunflower: Domator.
