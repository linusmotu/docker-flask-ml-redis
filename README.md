Need to install docker on Raspberry Pi  
Need to push other files for backend and worker to worker nodes if deployed there  

Initial setup:  
Setup local registry:  

docker pull redis  
tag the image so it points to local registry:  
docker tag redis hostname:5000/redis:v1  

Running:  
docker-compose build  
docker-compose push  

Querying the catalog of the local registry should return:  
curl raspberrypi3-05:5000/v2/_catalog  
{"repositories":["backend","backend-demo","dashboard","flask-app","frontend","python","redis"]}  

Needs the following directories/files on the worker nodes as volumes:  
place at ~ or /home/pi:  

flask-demo-registry/  
`-- backend  
    |-- app.py  
    |-- classify_array.py  
    |-- Dockerfile  
    |-- model.pkl  
    |-- README.md  
    |-- requirements.txt  
    `-- Simple\ Iris\ Model.ipynb  

Commands:  
docker-compose up  

