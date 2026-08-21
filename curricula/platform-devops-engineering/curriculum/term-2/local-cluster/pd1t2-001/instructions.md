# Deploy the Service to a Local Kubernetes Cluster

**Task ID:** `pd1t2-001`
**Estimated effort:** 14 hours
**Module:** Local cluster

## Why this task exists

Compose proved you can run the stack on one engine. The rest of this curriculum ships through a cluster you can destroy and recreate — kind or minikube, not a paid cloud account. You need manifests that apply cleanly, a Ready pod running *your* image, and a documented path to send it a request.

This is an apprenticeship task, not a content-consumption checkbox. Kind or minikube documentation you consult should be recorded in your notes. Completion requires a Ready pod and a request that did not come from inside your laptop process except via the documented access path.

## Authoritative resources

- **Docker Get Started** (reference): https://docs.docker.com/get-started/

Docker's docs cover the engine you use to load images. For cluster create, image load and kubectl apply, use the official kind (https://kind.sigs.k8s.io) or minikube (https://minikube.sigs.k8s.io) documentation and record the pages you used.

## Work to complete

Deploy the same service image you built in Term 1. Pick **one** local cluster product — kind *or* minikube — and stick with it for later tasks.

1. Create a local cluster with a documented command. Record the product, version, and the node image if kind prints one.
2. Load *your* image into the cluster (`kind load docker-image` or `minikube image load`). Do not point the Deployment at a public sample app.
3. Write a Deployment and a Service (ClusterIP plus port-forward is enough; NodePort or Ingress is acceptable if you document it). Add a readiness probe and a liveness probe on a real path the service serves.
4. Apply the manifests. Wait until the pod is Ready. Send a request through the documented access path and capture the response.
5. Put cluster-create, image-load and apply commands in a README or script so a mentor can replay them. Do not commit kubeconfig files that contain credentials you would not publish.

## Required evidence

- Committed Kubernetes manifests for at least a Deployment and a Service
- Captured `kubectl get` output showing a Ready pod and the Service, plus the cluster product you chose (kind or minikube)
- Captured request to the service through the documented access path (port-forward, NodePort, or Ingress)
- README or script that creates the cluster, loads the apprentice's image, and applies the manifests from a clean machine
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus a commit/tag reference. Do not submit only a screenshot of a dashboard.

## Acceptance criteria

- [ ] A kind or minikube cluster is created with a documented command, and the product name is recorded in the evidence note.
- [ ] Committed manifests include at least a Deployment and a Service and apply without error.
- [ ] The running pod reaches Ready; the documented readiness or liveness probe path succeeds.
- [ ] The image on the workload is the apprentice's image from earlier tasks, loaded locally, not a public sample application.

A mentor should be able to tell, from `kubectl` output and the Deployment spec, that this is your image.

## Reflection

Answer these in your own words after doing the work:

1. What does `Ready` mean for your probe, and what failure would still leave the pod Running but not Ready?
2. Why load the image into the cluster instead of pulling `latest` from a public registry for this task?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to delete the pod and predict whether the Deployment restores it with the same image tag before they run the delete.
- Do not approve a Deployment whose image is `nginx` / `hello-world` / another sample, or a Service with no documented way to send a request.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — writing the manifests yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved a Ready pod running your image on kind or minikube. LEARN BY DOING. GROW THROUGH MENTORSHIP.
