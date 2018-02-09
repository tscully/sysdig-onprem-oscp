# sysdig-onprem
Deploy Sysdig On Prem in Openshift


1- openssl req -new -newkey rsa:2048 -days 3650 -nodes -x509 -subj "/C=US/ST=CA/L=SanFrancisco/O=ICT/CN=onprem.sysdigcloud.com" -keyout server.key -out server.crt

2- oc create secret tls sysdigcloud-ssl-secret --cert=server.crt --key=server.key

3- oc adm policy add-scc-to-user privileged system:serviceaccount:sysdigcloud:elastic


Pending:
=======

  ```
  Move Cassandra to StatefulSets
  Move beta Deployment objects to OCP DeploymentConfig
  Add persistent storage to every DC if required
  Move Elasticsearch to StatefulSets
  Create a SA for Elasticsearch as the Pod must run in Privilege mode (check this requirement against th EFK stack)
  Worker, Redis, API and Collector need a SA with privileges on Anyuid SCC
  Error while using parameter references inside parameter definitions
  Create a passthrough Route for the API
  ```
