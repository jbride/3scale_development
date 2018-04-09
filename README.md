# 3scale_development course

See [Table of content](toc.adoc)


== Coolstore

. Deploy
+
-----
$ oc process -f ~/lab/3scale_development_labs/templates/coolstore-services.yml \
  -p INVENTORY_DB_USERNAME=jboss \
  -p INVENTORY_DB_PASSWORD=jboss \
  -p INVENTORY_DB_NAME=inventorydb \
  | oc create -f -

$ oc rollout resume dc/inventory
-----

. Test
+
-----
$ curl  -X GET "http://`oc get route inventory -o template --template='{{.spec.host}}'`/health"
-----

. Deletion
+
-----
$ oc delete all --all
$ oc delete pvc/inventory-psql-pv
$ oc delete configmap/inventory-config
-----


== Versions
1.0 - Feb 28, 2018 - Initial Release
