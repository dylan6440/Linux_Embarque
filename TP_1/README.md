 # Le premier TP est la création d'une image Docker avec un Dockerfile
 
 ## Une fois le Dockerfile fini on effectue une suite de commande pour la création et exécution de notre image
 
  
On effectue un docker build en lui disant que le dockerfile se situe dans le fichier actuel, on lui donne un nom d'image avec le -t et on lui donne en argument avec le --build-arg le Kernel de notre rpi3


      docker build . -t "nom_images" --build-arg "Kernel"


![docker_build](https://user-images.githubusercontent.com/70941138/117815688-037f1300-b266-11eb-9640-c334d526dd7c.PNG)


Une fois le build fini, on retrouve notre image créée 
    
    
        docker images
        
        
![docker images](https://user-images.githubusercontent.com/70941138/117817258-b4d27880-b267-11eb-997d-47a5fea33e30.PNG)


On lance l'image que l'on a créée
    
    
        docker run -it "nom_images"
        
        
![docker_run](https://user-images.githubusercontent.com/70941138/117817433-e3e8ea00-b267-11eb-82b5-ad6f5a93eda0.PNG)


Pour finir on vérifie que l'image est bien lancée avec la commande suivante dans un nouveau terminal
    
    
        docker ps
        
        
![docker ps](https://user-images.githubusercontent.com/70941138/117817559-02e77c00-b268-11eb-93b3-3594ef71732b.PNG)
    
    
L'image est bien lancée
