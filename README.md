
export GITHUB_TOKEN=

flux bootstrap github \
  --owner=bradmccoydev \
  --repository=flux-demo \
  --path=clusters/gitops \
  --personal

flux create source helm keptn --url https://charts.keptn.sh --namespace keptn