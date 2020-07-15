# Apache Ignite on Kubernetes

Apache Ignite is a typical Apache project: some sort of distributed storage
with a load of random other stuff jammed on top.

Read the docs: https://apacheignite.readme.io/docs/stateless-deployment

I had hoped to use this as a RESTful distributed key-value store, but the 'REST API'
is simply poor.

For example, basic `PUT` and `GET` commands are expressed as:
```
http://[host]:[port]/ignite?cmd=put&key=1&val=2018-01-01&cacheName=myCache&keyType=int&valueType=date
http://[host]:[port]/ignite?cmd=get&key=1&cacheName=myCache&keyType=int&valueType=date
```
rather than `HTTP` requests.

More `RESTful` info here: https://apacheignite.readme.io/docs/rest-api

## Usage

```
git clone https://github.com/anax32/apache-ignite-kubernetes
cd apache-ignite-kubernetes
kubectl apply -f .
sleep 5
kubectl logs -f $(kubectl get pods -l app=ignite -o name)
```
