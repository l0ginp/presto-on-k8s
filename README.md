# how to deploy presto on kubernetes

## 1. add presto connector
### re-build container
1.1 go to /docker folder
1.2 add new connetor file on /docker/etc/catalog
connector type : https://prestosql.io/docs/current/connector.html
1.3 build new container
`docker build -t {name:version} .`

## 2. deploy helm (local)
1. go to /helm-repo folder
2. deploy helm local
`helm install presto . --namespace "presto" --values ./values.yaml`

** remark
 - helm clone from stable/presto version 0.1.1
https://hub.kubeapps.com/charts/stable/presto
 - change deployment file `apiVersion: apps/v1`
 - add configmap for support new connection from container
    `node.properties`
    `add catalog.config-dir={connector path}`


## 3. how to use presto cli 
### install presto cli
`brew install presto`

### connect presto server
`presto --server 10.100.31.116:8080`

### cli example
`SHOW CATALOGS;`
`SHOW SCHEMAS FROM system;`
`SELECT * FROM catalog_name.schema.table`

ref. https://prestosql.io/docs/current/installation/cli.html

### Run a query to see the nodes in the cluster:
SELECT * FROM system.runtime.nodes;

