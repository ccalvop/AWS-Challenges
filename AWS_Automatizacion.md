![AUTOMATIZACIÓNCloudFormation](https://user-images.githubusercontent.com/126183973/224106728-fae51680-5785-4138-816c-f14313781eba.png)

# Automatización con CloudFormation

### Plantilla CloudFormation que incluya:
  -**VPC** con 2 **SUBNETS** en diferentes zonas de disponibilidad (AZ).
  
  -**AG** Autoscaling Group que despliegue entre 2 y 4 instanacias EC2 con AMI Amazon Linux 2 (EC2 tamaño t3.micro).
  
  -**EC2** instancias tendrán instalado servidor web Nginx (Userdata) con IP pública asignada.
  
  -**SG** Security Group que solo permita el acceso por el puerto 80 desde cualquier IP.
  
Definimos en código yaml el template de CloudFormation, añadiendo comentarios para facilitar la comprensión:

![template1](https://user-images.githubusercontent.com/126183973/224559743-30b56d3a-29b0-450c-88cb-f408f443e0e8.png)


