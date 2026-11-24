# Documentación del proyecto

**Autor/a:** Antonio de Andrés Lema
**Opción:** AWS

## 1. Arquitectura

| | dev | pro |
| --- | --- | --- |
| Zonas | "eu-west-1a" | "eu-west-1a", "eu-west-1b" |
| Servidores | Servidor A | Servidor A y Servidor B |
| Bucket de logs | Cifrado y con bloqueo de acceso público | Cifrado y con bloqueo de acceso público |
| Estado | Almacenado en unb bucket S3 | Almacenado en unb bucket S3 |

## 2. Cómo se ha organizado el código

El proyecto contiene tres módulos: Uno para crear el bucket S3 de logs, otro para crear el entorno de red y outro para crear los servidores web.
Hay dos directorios de entorno, uno para dev en el que se crea un servidor y otro para pro en el que se crean dos servidores.

## 3. Decisiones de seguridad

| Medida | Dónde | Por qué |
| --- | --- | --- |
| Bloqueado el acceso público | Bucket de logs | Para evitar accesos no autorizados a los logs |
| Cifrado en el lado del servidor | Bucket de logs | Para evitar accesos no autorizados a los logs |
| Cifrado del disco | Servidores web | Para evitar acceso a la información almacenada |
| Configuración de IMDSv2 | Servidores web | Para evitar accesos a los metadatos de las instancias |


### Hallazgos de Trivy aceptados

| Regla | Severidad | Justificación |
| --- | --- | --- |
| AWS-0104 | CRITICAL | Las instancias EC2 deben tener conexión a Internet para aplicar actualizaciones e instalar paquetes |
| AWS-0164 | HIGH | Las instancias EC2 deben tener direcciones IP públicas ya que no configuramos un balanceador de carga |
| AWS-0132 | HIGH | Ciframos el bucket con una llave gestionada por el usuario ya que en un entorno de prácticas no es necesario KMS |

## 4. CI/CD

Hay definidos tres workflows, el de CI que hace las comprobaciones de calidad y seguridad y se ejecuta en cada push y pull request 
(este se ha ejecutado de forma manual), el de despliegue de prueba que hace una prueba en un entorno efímero de floci y el de 
despliegue de AWS que realiza un despliegue en AWS.

## 5. Cómo desplegar

El proyecto se despliega ejecutando "terraform apply" en la carpeta del entorno correspondiente, y se destruye con
"terraform destroy".

## 6. Mejoras posibles

Se podría añadir un balanceador de carga de aplicaciones en el entorno de pro, y una distribución CloudFront para acelerar
la entrega de contenido a los clientes y protección contra ataques DoS con AWS WAF.
