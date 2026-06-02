Use this to install grafana on openshift
Steps as below:

1. Deploy grafana operator from openshift and use the default settings for operator installtion
2. create a namespace called grafana.
3. Now we will create an instance of grafana. Go to installed operators and choose grafana. Deploy grafana instance using the grafana instance yaml file included. Specify the route here to access grafana via UI.
4. Add following roles to grafana service account
      oc adm policy add-cluster-role-to-user cluster-reader -z grafana-sa
      oc adm policy add-cluster-role-to-user cluster-monitoring-view -z grafana-sa
5. Get a bearer token for the grafana service account
         oc create token grafana-sa
6. Now lets create a DataSource for grafana. Use the yaml attached. Replace the token value with the token created from point 5. Here we are using the thanos queries as the source for getting the data.
7. lets wait to see if the newly created instance and datasource are successfully created
8. Login to grafana UI by getting the URL
          oc get route -n grafana
9. credentials are taken from file used in Pt 3.
10. Once logged in goto datasources to see if the new datasource is visible.
11. Next steps include importing dashboards.
   
