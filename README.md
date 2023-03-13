X-Road-Lab V.2

Laboratorio de ecosistema básico de X-Road

Hola!

Este repositorio contiene un laboratorio básico de X-Road 7 el cual está compuesto por tres host de Security Server y Un Central Server con las entidades de certificación.

Nota: No se debe usar en un ambiente productivo, este entorno es solo con fines educativos. 

Saludos y éxito en tu formación con X-Road. 

By César Manzanero

Requisitos previos:
Se requiere tener instalado Docker y haberlo configurado previamente. Información al respecto en el sitio oficial de Docker.com (Para entornos Windows se requiere wls2).

Una vez completado los requisitos previos se debe clonar o descargar este repositorio y situarse dentro de la misma por medio de una terminal.

Posteriormente ejecutar el archivo compose mediante el siguiente comando:

docker-compose up -d


CentralServer
 ipv4_address: 10.10.0.50
 
SecurityServer_A
 ipv4_address: 10.10.0.51
 
SecurityServer_B
 ipv4_address: 10.10.0.52
 
SecurityServer_C
 ipv4_address: 10.10.0.53

Para acceder a la terminal de los servidores se debe ejecutar el siguiente comando reemplazando [dockeid] por el id o nombre del servidor al que desea acceder

docker exec -i -t [dockeid] /bin/bash 

Para copiar los archivos de certificado se deberá ejecutar los siguientes comandos 

docker cp CentralServer:/home/ca/CA/certs/ca.cert.pem .
docker cp CentralServer:/home/ca/CA/certs/ocsp.cert.pem .
docker cp CentralServer:/home/ca/CA/certs/tsa.cert.pem .

-Certificate Profile Info-

ee.ria.xroad.common.certificateprofile.impl.FiVRKCertificateProfileInfoProvider

Add OCSP Responder 
http://10.10.0.50:8888

Add Timestamping Service
http://10.10.0.50:8899

API REST  

http://jsonplaceholder.typicode.com/posts

curl -X GET "https://{securityserver}/r1/{serviceId}/v2/pets/1124" -H "accept: application/json" -H "X-Road-Client: {client}"

curl -X GET "http://localhost:4201/r1/MXQROO/GOV/SS-01/PROVIDER/allowedMethods" -H "accept: application/json" -H "X-Road-Client: MXQROO/GOV/SS-02/CONSUMER"

