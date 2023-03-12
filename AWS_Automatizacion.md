![AUTOMATIZACIÓNCloudFormation](https://user-images.githubusercontent.com/126183973/224106728-fae51680-5785-4138-816c-f14313781eba.png)

# Automatización con CloudFormation

### Vamos a definir una plantilla en CloudFormation para tener un servidor web Nginx, que incluirá:
  -**VPC** con 2 **SUBNETS** en diferentes zonas de disponibilidad (AZ).
  
  -**AG** Autoscaling Group que despliegue entre 2 y 4 instanacias EC2 con AMI Amazon Linux 2 (EC2 tamaño t3.micro).
  
  -**EC2** instancias tendrán instalado servidor web Nginx (Userdata) con IP pública asignada.
  
  -**SG** Security Group que solo permita el acceso por el puerto 80 desde cualquier IP.
  
**> Definimos el template de CloudFormation en código yaml** (añadiendo comentarios para facilitar la comprensión):

![template1](https://user-images.githubusercontent.com/126183973/224559743-30b56d3a-29b0-450c-88cb-f408f443e0e8.png)

:pager: **CAPTURAS DE PANTALLA**

_Stacks: creamos un nuevo stack en CloudFormation a partir del template (plantilla) en formato yaml guardada anteriormente_
![aws-caso6-ccalvo-p_1-](https://user-images.githubusercontent.com/126183973/224560266-3d06c4e8-266c-4540-a32a-e6292319d131.jpg)

_Resources: podemos observar todos los recursos desplegados_
![aws-caso6-ccalvo-p_2-](https://user-images.githubusercontent.com/126183973/224560278-ef887ace-d831-4f1f-bfa6-0418ad334468.jpg)

_Para comprobar que el despliegue funciona, copiamos la IP pública de la instancia_
![aws-caso6-ccalvo-p_3-](https://user-images.githubusercontent.com/126183973/224560286-c450eea8-da7a-4751-a739-6175544e6d7d.jpg)

_Pegamos la IP en un navegador y observamos que el servidor Nginx funciona correctamente_
![aws-caso6-ccalvo-p_4](https://user-images.githubusercontent.com/126183973/224560294-71746857-db89-4c9c-a0fe-c66469efcc38.jpg)
