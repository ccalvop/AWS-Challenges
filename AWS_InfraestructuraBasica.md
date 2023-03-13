![INFRAESTRUCTURA_BÁSICA(Web_console_+_CLI)](https://user-images.githubusercontent.com/126183973/224091239-79be2a85-99d9-4f3d-9916-71275b6501db.png)

# ¿Qué podriamos definir como **infraestructura básica** en AWS?
En este ejemplo vamos a desplegar una infraestructura básica en AWS que consta de los siguientes elementos:

```VPC, IG internet gateway, subredes, tablas de enrutamiento y SG security groups``` a través de **AWS Management Console**

```instancias EC2``` a través de **CLI**

:one: Crear una **VPC** _(VPC-caso2)_
![aws-caso2-ccalvo-p_1-](https://user-images.githubusercontent.com/126183973/224799344-3db53379-c9b3-4e2b-905b-f0b7dd46bfb5.jpg)

:two: Crear IG **Internet Gateway** y adjuntarlo (Attach) al VPC creado anteriormente _(VPC-caso2)_
![aws-caso2-ccalvo-p_2-](https://user-images.githubusercontent.com/126183973/224799986-2faa8d18-5175-4f2b-bb3b-33105999e7e4.jpg)
_ *Si  quisieramos que las subredes privadas tuvieran acceso a internet previniendo que desde el acceso se pudieran conectar a ellas, entonces creariamos NAT Gateway_

:three: Crear subredes (**Subnets**) con direcciones IP correctas (10.0.X.0/24) en 2 zonas de disponibilidad AZ
![aws-caso2-ccalvo-p_3-](https://user-images.githubusercontent.com/126183973/224800342-bc8e1abd-25fe-4aa8-bc8e-f27edf6991cb.jpg)

:four: Crear las tablas de enrutamiento (**Route Tables**)
![aws-caso2-ccalvo-p_4-](https://user-images.githubusercontent.com/126183973/224800704-602777ed-024b-415c-9dca-58716d3494e3.jpg)

:small_blue_diamond: Crear la **Tabla de Enrutamiento** para las subredes públicas. Asociamos esta tabla a las dos **Public subnets**. Añadimos la ruta a internet (0.0.0.0/0) por el IG (**Internet Gateway** del paso 2)
![aws-caso2-ccalvo-p_5-](https://user-images.githubusercontent.com/126183973/224801613-091624c9-e174-40a7-9526-1259f5f5e426.jpg)

:small_blue_diamond: Crear la **Tabla de Enrutamiento** para las subredes privadas. Asociamos esta tabla a las dos **Private subnets**. En este caso he creado dos tablas de enrutamiento diferente porque había dos **NAT** diferentes (1 para cada subnet privada). Y solo se puede enrutar el trafico exterior por 1 target, a cada NAT correspondiente. Si no hubiera **NAT Gateways**, dejariamos por defecto el enrutamiento, que solo es dentro de la VPC (local)
![aws-caso2-ccalvo-p_6a-](https://user-images.githubusercontent.com/126183973/224801651-7f19b19f-e000-4c8c-a5ad-e152f3a275e6.jpg)
![aws-caso2-ccalvo-p_6b-](https://user-images.githubusercontent.com/126183973/224801662-e9b2b691-330d-4e66-b482-4f394ed5decd.jpg)

