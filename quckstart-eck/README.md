1) Install kubectl on local machine using directions from https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-macos
2) Stand up GKE Cluster or Minikube Cluster
	a) Install `gcloud sdk` https://cloud.google.com/sdk/install
	b) If using GKE make sure to set the context for kubectl to your GKE Cluster by going to your gke cluster and clicking `Connect to Cluster`
	c) Copy and paste the command line access
3) Install the CRD and the operator with `kubectl apply -f https://download.elastic.co/downloads/eck/0.8.0/all-in-one.yaml`
	a) Monitor the logs using `kubectl -n elastic-system logs -f statefulset.apps/elastic-operator`
4) Deploy our first es and kibana service by running `kubectl apply -f .` from the directory that has spec-elaticsearch.yml and spec-kibana.yml
5) Follow steps at the bottom of the spec-elasticsearch.yml

***Worth noting that if you're trying to configure beats external to the kubernetesd cluster, the user either needs to get the self signed certs from the elasticsearch pods or add `ssl.verification_mode: none` to the `output.elasticsearch` section of the beat.


**Helpful Commands
//Show k8 Contexts
`kubectl config get-contexts`

//List Elasticsearch Clusters and Kibana
`kubectl get elasticsearch`
`kubectl get kibana`

// Get the Username and Password for Cluster
`echo $(kubectl get secret quickstart-elastic-user -o=jsonpath='{.data.elastic}' | base64 --decode)`

//Delete Elastic Stack
`kubectl delete kibana.kibana.k8s.elastic.co/quickstart`
`kubectl delete elasticsearch.elasticsearch.k8s.elastic.co/quickstart`

// Get Pod Yaml
`kubectl get pod quickstart-es-2jngp9q5xw -o yaml --export`

// List Services
`kubectl get services`