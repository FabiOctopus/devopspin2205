## Proyecto Integrador Devops
## Fecha de Presentación
- 9 de Agosto de 2023

## Intro

El proyecto tiene como principal objetivo poner en práctica los conocimientos adquiridos a travéz de toda la cursada, realizando una integración de diversas herramientas y tecnologías vistas en clase. 

La infraestructura que utilice como punto de partida para realizar todas las tareas necesarias es Cloud. Procedi con el despliegue de la infraestructura utilizando Terraform, lo que hice fue desplegar un cluster de EKS, ademas configure el backend para almacenar el estado del despliegue en un bucket S3, seguido a la creación de una VPC para la comunicación del clúster y los nodos. 

Una vez finalizado el deploy de la infraestructura, se ejecuta un script para instalar y configurar el loadbalancer que apunta al clúster que se creo anteriormente. 

Luego continuamos con el pipeline donde utilice Jenkins, el cual estará compuesto por un Jenkinsfile de 3 stages, los cuales se detallan a continuación: 

1. La contrucción de las imagenes (CI)
2. El docker push (CI)
3. La creación de la infraestructura (CD)

En el stage de CD vamos a utilizar un agent Docker de Jenkins donde use una imagen (ubuntu_ioc) de Ubuntu que ya esta lista con todo lo necesario. Esto es con motivo de asegurar que no habrá cambio de versiones que puedan perjudicar el despliegue del pipeline. Dentro de dicha imagen se crea unas variables de entorno y se setean las credenciales de la cuenta de AWS. 

- AWS_ACCESS_KEY_ID
- AWS_SECRET_ACCESS_KEY
- AWS_REGION

Luego de hacer un despliegue exitoso del pipeline, se realiza una prueba modificando el código html de la app vote donde se realiza el versionado y se vuelve a ejecutar, mostrando en pantalla las modificaciones realizadas exitosamente. 

Al finalizar, los dashboards de Grafana y las reglas de Prometheus se combinaron con esta documentación y scripts para proporcionar un monitoreo del clúster de Kubernetes en AWS de extremo a extremo. 

Se adjunta repositorio de Prometheus y Grafana para su documentación

Repositorio Prometheus | Grafana → https://github.com/prometheus-operator/kube-prometheus
