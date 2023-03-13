![INFRAESTRUCTURA_BÁSICA(Web_console_+_CLI)](https://user-images.githubusercontent.com/126183973/224091239-79be2a85-99d9-4f3d-9916-71275b6501db.png)

# ¿Qué podriamos definir como **infraestructura básica** en AWS?
En este ejemplo vamos a desplegar una infraestructura básica en AWS que consta de los siguientes elementos:

```VPC, IG internet gateway, subredes, tablas de enrutamiento y SG security groups``` a través de **AWS Management Console**

```instancias EC2``` a través de **CLI**

:one: Crear una VPC _(VPC-caso2)_
![aws-caso2-ccalvo-p_1-](https://user-images.githubusercontent.com/126183973/224799344-3db53379-c9b3-4e2b-905b-f0b7dd46bfb5.jpg)

:two: Crear IG Internet Gateway y adjuntarlo (Attach) al VPC creado anteriormente _(VPC-caso2)_
![aws-caso2-ccalvo-p_2-](https://user-images.githubusercontent.com/126183973/224799986-2faa8d18-5175-4f2b-bb3b-33105999e7e4.jpg)
_* Si  quisieramos que las subredes privadas tuvieran acceso a internet previniendo que desde el acceso se pudieran conectar a ellas, entonces creariamos NAT Gateway
