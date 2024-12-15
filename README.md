# Desafio 1 Modulo 5

Este repositorio fue realizado para completar el Desafio 1 del Modulo 5 del curso de DevOps de Desafio Latam

## Desafio

El Objetivo del desafio es crear una instacia EC2 de AWS utilizando Github Acctions para automatizar el proceso de creación y configuración de la instancia

### Requerimientos

1. Creación y gestión de instancias EC2
    - Crear una instancia EC2 en AWS usando Github Actions
    - Se debe incluir la creacion de la instancia, configuracion de los parametros básicos y su inicio
2. Tipos de instancia y casos de uso
    - Definir el tipo de instancia que se utilizará y justificar la eleción según el caso propuesto
3.  Seguridad y Acceso
    - Configurar un gurpo de seguridad para la instancia EC2, asegurando que se pertmita el acceso SSH mediante clave privada
    - Asegurarse que la clase SSH sea correctamente generada y gestionada en el flujo de trabajo de Github Accions
4. Configuración de redes y VPC
    - Aegurarse de que la instancia EC2 esté lanzada dentro de una VPC adecuada y de que la configuracion de subredes y rutas sea correcta
5. Uso de AMIs presonalizadas
    - Crear una imagen de una maquina de Amazon (AMI) personalizada basada en una Instancia EC2 creada, asegurando que pueda ser tulizada para lanzar instancias con configuraciones similates en el futuro
  
### Desarrollo del Ejericio

1- Se comienza el ejercicio creando un repositorio local, y configurando el directorio .github/workflows para que github reconozca la accion, dentro de este se crea el archivo pipeline.yml que contendrá el codigo de la action automatizada  
2. Se configura la acción que correra en la version latest de ubuntu, se configuran 3 trabajos, el primero que revisa el repositorio, el segundo que configura las credenciales de AWS, y uno que lanza la instancia automaticamente  
3. Para que la accion de configurar las credenciales de AWS se debe previamente configurar los siguientes secretos de repositorios, AWS_ACCESS_KEY_ID y AWS_SECRET_ACCESS_KEY, además de la variable AWS_REGION, para que la accion funcione correctamente  
4. Previo a generar la acción se configura un grupo de seguridad para la instancia que permita la conexion SSH por el puerto 22 y HTTP por el puerto 80  
5. También se configura una VPC con 2 subredes una publica y una privada, para este trabajo se debe conectar la instancia a la Subred publica  
6. Se configuran las variables con las cuales se generará la instancia, en variables se incluye AWS_AMI_ID, la cual contiene un ID de una AMI personalizada, el tipo de instancias AWS_TIPO_INSTANCIA, y en los secretos se agregan AWS_KEY_NAME con el nombre de la clave de pares, AWS_SECURITY_GROUP_ID con el id de grupo de seguridad, AWS_SUBNET_ID  
7. En las tag-especificaciones se agregaa el nombre para diferenciar la instancia creada mediante github 

