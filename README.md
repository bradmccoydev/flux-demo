
export GITHUB_TOKEN=

flux bootstrap github \
  --owner=bradmccoydev \
  --repository=flux-demo \
  --path=clusters/gitops \
  --personal

git clone https://github.com/bradmccoydev/flux-demo
cd flux-demo

flux create source git keptn \
  --url=https://github.com/bradmccoydev/flux-demo \
  --branch=main \
  --interval=90s \
  --export > ./clusters/gitops/podinfo-source.yaml

flux create source helm keptn --url https://charts.keptn.sh --namespace keptn

flux create helmrelease keptn --chart keptn \
  --source HelmRepository/keptn \
  --chart-version 0.15.0 \
  --namespace keptn