# x-road-lab
Laboratorio de ecosistema basico de X-Road

Hola!

Este repositorio contiene un laboratorio basico de X-Road 7 el cual compuesto por tres host de Security Server y Un Central Server con las entidades de certificacion.

Nota: No se debe usar en un ambiente productivo, este entorno es solo con fines educativos. 

Saludos y exito en tu formacion con X-Road. 

By Cesar Manzanero


CentralServer
 ipv4_address: 10.10.0.50
 
SecurityServer_A
 ipv4_address: 10.10.0.51
 
SecurityServer_B
 ipv4_address: 10.10.0.52
 
SecurityServer_C
 ipv4_address: 10.10.0.53

docker exec -i -t [dockeid] /bin/bash 

docker cp [dockeid]:/home/ca/CA/certs/ca.cert.pem .
docker cp [dockeid]:/home/ca/CA/certs/ocsp.cert.pem .
docker cp [dockeid]:/home/ca/CA/certs/tsa.cert.pem .

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
