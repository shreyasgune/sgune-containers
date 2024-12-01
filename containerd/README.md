## ContainerD
[Installation instructions](https://github.com/containerd/containerd/blob/main/docs/getting-started.md)

### What is it?
containerd is a lightweight, high-performance container runtime used to manage container lifecycle operations like pulling images, creating containers, and managing storage. It's part of the Cloud Native Computing Foundation and often used in Kubernetes environments.

### Why is it used?

- Kubernetes relies on containerd as the default container runtime.

- It's used for efficient, high-performance container management in production environments, especially for orchestrated workloads.

### Benefits over Docker:
- Lightweight: Containerd focuses solely on container runtime, without Docker’s additional features like image building or CLI tools.
- Performance: It has lower overhead, making it more efficient, especially for orchestrators like Kubernetes.
- Modular: Containerd can be used as just the runtime, while Docker includes more integrated features (e.g., Docker Compose, Swarm).
- Kubernetes-friendly: It integrates seamlessly with Kubernetes, reducing complexity compared to Docker.
- Fewer Dependencies: Less resource-heavy than Docker, making it ideal for high-performance environments.

<details>
<summary>Verify</summary>

```
~/c/sgune-containers/c/nerdctl containerd-demo !1 ?1 > sudo systemctl start containerd                                  01:31:08 PM
~/c/sgune-containers/c/nerdctl containerd-demo !1 ?1 > sudo systemctl enable containerd                                 01:31:36 PM
~/c/sgune-containers/c/nerdctl containerd-demo !1 ?1 > sudo systemctl status containerd                                 01:31:46 PM
● containerd.service - containerd container runtime
     Loaded: loaded (/lib/systemd/system/containerd.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2024-12-01 13:15:28 IST; 16min ago
       Docs: https://containerd.io
   Main PID: 7214 (containerd)
      Tasks: 12
     Memory: 20.7M
     CGroup: /system.slice/containerd.service
             └─7214 /usr/bin/containerd

Dec 01 13:15:28 DESKTOP-KBBD829 containerd[7214]: time="2024-12-01T13:15:28.801033667+05:30" level=info msg="Start subscribing cont>
Dec 01 13:15:28 DESKTOP-KBBD829 containerd[7214]: time="2024-12-01T13:15:28.801154417+05:30" level=info msg="Start recovering state"
Dec 01 13:15:28 DESKTOP-KBBD829 containerd[7214]: time="2024-12-01T13:15:28.801278703+05:30" level=info msg=serving... address=/run>
Dec 01 13:15:28 DESKTOP-KBBD829 containerd[7214]: time="2024-12-01T13:15:28.801286547+05:30" level=info msg="Start event monitor"
Dec 01 13:15:28 DESKTOP-KBBD829 containerd[7214]: time="2024-12-01T13:15:28.801352927+05:30" level=info msg="Start snapshots syncer"
Dec 01 13:15:28 DESKTOP-KBBD829 containerd[7214]: time="2024-12-01T13:15:28.801395887+05:30" level=info msg="Start cni network conf>
Dec 01 13:15:28 DESKTOP-KBBD829 containerd[7214]: time="2024-12-01T13:15:28.801427317+05:30" level=info msg="Start streaming server"
Dec 01 13:15:28 DESKTOP-KBBD829 containerd[7214]: time="2024-12-01T13:15:28.801402593+05:30" level=info msg=serving... address=/run>
Dec 01 13:15:28 DESKTOP-KBBD829 containerd[7214]: time="2024-12-01T13:15:28.801758947+05:30" level=info msg="containerd successfull>
Dec 01 13:15:28 DESKTOP-KBBD829 systemd[1]: Started containerd container runtime.
```
</details>

## checking

```
nerdctl run -it --rm alpine /bin/sh

```


