# panoptica-kubernetes-integration

![Version: 1.2.3-beta5](https://img.shields.io/badge/Version-1.2.3--beta5-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Kubernetes integration with Panoptica. It will install the required components according the features chosen in the values.

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| oci://public.ecr.aws/ciscoeti/panoptica/charts | kubernetes-integration-deployment-controller(kubernetes-integration-deployment-controller) | 0.5.0-beta3 |
| oci://registry.outshift.com/panoptica/cdr/helm-charts | cdr-controller(panoptica-cdr) | 1.0.22 |
| oci://us-docker.pkg.dev/eticloud/panoptica-public-registry/apisec | apisec-controllers(apisec-controllers) | 0.3.8 |
| oci://us-docker.pkg.dev/eticloud/panoptica-registry/panoptica | k8sec-controller(panoptica) | 1.221.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| apisec-controllers.apisec-controller.image.repository | string | `"panoptica/apisec/apisec-controller/controller"` | Overrides the controller image registry |
| apisec-controllers.fuzzer-controller.image.repository | string | `"panoptica/apisec/fuzzer-controller/controller"` | Overrides the controller image registry |
| global.accessKey | string | `""` | Access key used by API Security. |
| global.affinity | object | `{}` | Configures Node affinity for Panoptica pods. |
| global.deploymentHooks.annotations | object | `{}` | Annotations to add to the deployment hooks |
| global.deploymentHooks.enabled | bool | `false` | Indicates whether deployment hooks should be used to report deployment status (e.g ArgoCD sync hooks). |
| global.extraLabels | object | `{}` | Allow labelling resources with custom key/value pairs. |
| global.httpProxy | string | `""` | Proxy address to use for HTTP request if needed. |
| global.httpsProxy | string | `""` | Proxy address to use for HTTPs request if needed. In most cases, this is the same as `httpProxy`. |
| global.isOpenShift | bool | `false` | Indicates whether installed in an OpenShift environment. |
| global.k8sCisBenchmarkEnabled | bool | `true` | Indicates whether K8s CIS benchmark is enabled. |
| global.kubeVersionOverride | string | `""` | Override detected cluster version. |
| global.mgmtHostname | string | `""` | Panoptica SaaS URL. Used to override default URL for local testing. |
| global.panopticaCDR.clusterID | string | `""` | Cluster ID used by CDR. |
| global.panopticaCDR.initialToken | string | `""` | Token used to register a new CDR instance. The token can be used once. |
| global.panopticaIntegration.apiSecurity.enabled | bool | `true` | Indicates whether API Security is enabled. |
| global.panopticaIntegration.cdr.enabled | bool | `false` | Indicates whether Realtime CDR is enabled. |
| global.panopticaIntegration.id | string | `""` | [Required] Integration ID. |
| global.panopticaIntegration.kspm.enabled | bool | `true` | Indicates whether KSPM is enabled. Always true; this value cannot be changed. |
| global.productNameOverride | string | `"panoptica"` | Override product name. Defaults to chart name. |
| global.registry | string | `"registry.outshift.com"` | Registry for the Panoptica images. If replaced with a local registry need to make sure all images are pulled into the local registry. |
| global.sendTelemetriesIntervalSec | int | `30` | Configures telemetry frequency (in seconds) for reporting duration. |
| global.sharedSecret | string | `""` | Shared secret used by API Security. |
| global.tolerations | list | `[]` | Configures tolerations for scheduling Panoptica pods. |
| k8sec-controller.busybox.image.repository | string | `"panoptica/kspm/curlimages/curl"` | Overrides the busybox image registry |
| k8sec-controller.controller.image.repository | string | `"panoptica/kspm/k8s_agent"` | Overrides the controller image registry |
| k8sec-controller.imageAnalysis.cisDockerBenchmark.image.repository | string | `"panoptica/kspm/cis-docker-benchmark"` | Overrides the cis-docker-benchmark image registry |
| k8sec-controller.imageAnalysis.sbom.image.repository | string | `"panoptica/kspm/image-analyzer"` | Overrides the image-analyzer image registry |
| k8sec-controller.k8sCISBenchmark.image.repository | string | `"panoptica/kspm/k8s-cis-benchmark"` | Overrides the k8s-cis-benchmark image registry |
| kubernetes-integration-deployment-controller.api.url | string | `""` | [Required] Panoptica SaaS URL. |
| kubernetes-integration-deployment-controller.image.registry | string | `"registry.outshift.com"` | Overrides the controller image registry |
| kubernetes-integration-deployment-controller.secret.token | string | `""` | Token used by the deployment controller to communicate with the SaaS. |
| kubernetes-integration-deployment-controller.syncIntegrationJob.api.url | string | `""` | [Required] Panoptica SaaS URL. |
| kubernetes-integration-deployment-controller.syncIntegrationJob.image.registry | string | `"registry.outshift.com"` | Overrides the job image registry |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
