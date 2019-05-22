1) Install kubectl on local machine using directions from https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-macos
2) Stand up GKE Cluster or Minikube Cluster
	a) Install `gcloud sdk` https://cloud.google.com/sdk/install
	b) If using GKE make sure to set the context for kubectl to your GKE Cluster by going to your gke cluster and clicking `Connect to Cluster`
	c) Copy and paste the command line access
3) Install the CRD and the operator with `kubectl apply -f https://download.elastic.co/downloads/eck/0.8.0/all-in-one.yaml`
	a) Monitor the logs using `kubectl -n elastic-system logs -f statefulset.apps/elastic-operator`
4) Deploy our first es and kibana service by running `kubectl apply -f .` from the directory that has split-es.yml and split-kibana.yml
5) Follow steps at the bottom of the split-es.yml