# sysdig-onprem
Deploy Sysdig On Prem in Openshift


MySQL
Redis
Cassandra
Elasticsearch


oc create serviceaccount elasticsearch
oc adm policy add-scc-to-user anyuid system:serviceaccount:sysdig:elasticsearch
oc create serviceaccount cassandra
oc adm policy add-scc-to-user anyuid system:serviceaccount:sysdig:cassandra
oc create serviceaccount sysdig
oc adm policy add-scc-to-user anyuid system:serviceaccount:sysdig:sysdig
