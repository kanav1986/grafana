#### This is for information ######
The gitops SA does not have permissions to create certain objects in the group sync namespace.
Hence, policy may have to be explicitly added as below:

oc adm policy add-role-to-user admin system:serviceaccount:openshift-gitops:openshift-gitops-argocd-application-controller -n group-sync-operator
