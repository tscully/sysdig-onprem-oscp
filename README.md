# sysdig-onprem
Deploy Sysdig On Prem in Openshift


1- openssl req -new -newkey rsa:2048 -days 3650 -nodes -x509 -subj "/C=US/ST=CA/L=SanFrancisco/O=ICT/CN=onprem.sysdigcloud.com" -keyout server.key -out server.crt

2- oc create secret tls sysdigcloud-ssl-secret --cert=server.crt --key=server.key

3- Create Persistent Volumes for:
    - MySQL
    - Elasticsearch
    - Cassandra

4- Add Service Accounts to anyuid and privileged SCC
