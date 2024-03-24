1) build development container image for all target architectures
    kubernetes.io/os: linux
    kubernetes.io/arch: amd64

<https://tekton.dev/docs/pipelines/windows/>
<https://podman.io/blogs/2021/10/11/multiarch>
<https://github.com/containers/buildah/issues/1590#issuecomment-953652550>
<https://pipelinesascode.com/docs/guide/resolver/#tasks-or-pipelines-inside-the-repository>
<https://tekton.dev/docs/pipelines/pipelines-in-pipelines/>
<https://tekton.dev/docs/pipelines/pipelines/#specifying-matrix-in-pipelinetasks>
<https://tekton.dev/docs/chains/signing/>

 node selector

rwx storage
beta (or even alpha) features for tekton
heterogenous cluster (x86_64 and aarch64 workers)
permissions to add privileged scc to pipeline sa

podman build -f containers/development/Containerfile containers/development/

2) run osbuild target on specific architecture
   1) build your own app or trigger rebuild from other pipeline?
   2) cluster task for osbuild
   3) trigger other pipelines based on input (dependencies?) knative eventing

<https://tekton.dev/docs/pipelines/pipelines/#specifying-matrix-in-pipelinetasks>
sudo podman run -v ./:/src/:Z -it osbuild:latest
cd src/osbuild-manifests/
make autosd-qemu-minimal-ostree.x86_64.oci-archive+qcow2

3) virtual testing
4) jumpstarter
5) local development workflow (podman remote on ocp virt)
6) feedback loop
7) backstage?

pipeline developer container
pipeline ai/ml workload
pipeline osbuild    -> developer container
                    -> ai/ml workload
