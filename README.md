# sysdig-onprem
Deploy Sysdig On Prem in Openshift

1- Create project sysdigcloud

  ```
    oc new-project sysdigcloud --description='SysdigCloud On-Prem' --display-name='SysdigCloud On-Prem'
  ```

2- openssl req -new -newkey rsa:2048 -days 3650 -nodes -x509 -subj "/C=US/ST=CA/L=SanFrancisco/O=ICT/CN=onprem.sysdigcloud.com" -keyout /tmp/server.key -out /tmp/server.crt

3- oc create secret tls sysdigcloud-ssl-secret --cert=/tmp/server.crt --key=/tmp/server.key


4- Add Service Accounts to anyuid and privileged SCC

  ```
  oc adm policy add-scc-to-user anyuid system:serviceaccount:sysdigcloud:sysdigcloud
  oc adm policy add-scc-to-user privileged system:serviceaccount:sysdigcloud:elastic
  ```

5- Apply the existing template

  ```
  oc process -f templates/sysdig-cloud.yml | oc apply -f-
  ```
