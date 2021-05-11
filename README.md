# Linux_Embarque

## TP Linux Embarqué

Dans ce git vous retrouverez les deux tp effectué en cours:

  - Le premier est la création d'une image Docker avec un Dockerfile
  
  On Effectue un docker build en lui disent que le dockerfile ce situe dans le fichier actuel, on lui donne un nom d'image avec le -t et on lui donne en argument avec le --build-arg le Kernel de notre rpi3
  
    docker build . -t "nom_images" --build-arg "Kernel"
  
   ![docker_build](https://user-images.githubusercontent.com/70941138/117815688-037f1300-b266-11eb-9640-c334d526dd7c.PNG)
