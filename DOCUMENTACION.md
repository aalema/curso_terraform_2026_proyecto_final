# Documentación del proyecto

**Autor/a:** Antonio de Andrés Lema
**Opción:** AWS

## 1. Arquitectura

Describe en pocas líneas qué despliega cada entorno y en qué se diferencian. Puedes incluir un diagrama (imagen o texto).

| | dev | pro |
| --- | --- | --- |
| Zonas | ___ | ___ |
| Servidores | ___ | ___ |
| Bucket de logs | ___ | ___ |
| Estado | ___ | ___ |

## 2. Cómo se ha organizado el código

Explica los módulos, los directorios de entorno y los bucles que usas.

## 3. Decisiones de seguridad

| Medida | Dónde | Por qué |
| --- | --- | --- |
| ___ | ___ | ___ |

### Hallazgos de Trivy aceptados

| Regla | Severidad | Justificación |
| --- | --- | --- |
| AWS-0104 | CRITICAL | Las instancias EC2 deben tener conexión a Internet para aplicar actualizaciones e instalar paquetes |
| AWS-0164 | HIGH | Las instancias EC2 deben tener direcciones IP públicas ya que no configuramos un balanceador de carga |
| AWS-0132 | HIGH | Ciframos el bucket con una llave gestionada por el usuario ya que en un entorno de prácticas no es necesario KMS |

## 4. CI/CD

Explica qué hace cada workflow y cuándo se ejecuta. Si no has usado GitHub, indica que has ejecutado los scripts en local.

## 5. Cómo desplegar

Pasos para desplegar y destruir tu proyecto.

## 6. Mejoras posibles

¿Qué cambiarías con más tiempo?
