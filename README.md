### CloudRun release action

This action aims to simplify the deployment of a docker image in google cloud run.

Usage example:

```yaml
  jobs:
    deploy:
      steps:
      - name: Build Image
        run: docker build -t europe-west9-docker.pkg.dev/voi-sdbx-ensg-2023/cicd-registry/jlevesy/menu-server:${{ github.ref_name }} .
      - id: release
        name: Release To CloudRun
        uses: cicd-lectures/cloudrun-release@v1
        with:
          instance_name: 'super-menu-server'
          image_name: europe-west9-docker.pkg.dev/voi-sdbx-ensg-2023/cicd-registry/jlevesy/menu-server:${{ github.ref_name }}
          gcp_project: voi-sdbx-ensg-2023
          gcp_service_account: sa-wif-ensg-cd-job@voi-sdbx-ensg-2023.iam.gserviceaccount.com
          gcp_workload_identity_provider: projects/394185464198/locations/global/workloadIdentityPools/ensg-cd-github/providers/github
```
