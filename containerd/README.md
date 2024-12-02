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

- Image Pull
<details><summary>ctr images pull docker.io/library/redis:alpine</summary>

```diff
~ > sudo ctr images pull docker.io/library/redis:alpine                                                     08:14:55 AM
docker.io/library/redis:alpine:                                                   resolved       |++++++++++++++++++++++++++++++++++++++|
index-sha256:c1e88455c85225310bbea54816e9c3f4b5295815e6dbf80c34d40afc6df28275:    done           |++++++++++++++++++++++++++++++++++++++|
manifest-sha256:395033a36458e5312f5bce401452efe6606705fc8b9a574611af6436ac3ff632: done           |++++++++++++++++++++++++++++++++++++++|
config-sha256:87b460005bd3a6621dabf2855ec42bf96b1b6d044b6109bd9736128ab178ddec:   done           |++++++++++++++++++++++++++++++++++++++|
layer-sha256:37d63ae71d3552a8a9e6ec86a6949e062494ae742d63385e6d1aadc692e45b4a:    done           |++++++++++++++++++++++++++++++++++++++|
layer-sha256:b3d150cb1b6c3813e2b064652da3c74f35793602e44c9e7b386f93197a11207e:    done           |++++++++++++++++++++++++++++++++++++++|
layer-sha256:da9db072f522755cbeb85be2b3f84059b70571b229512f1571d9217b77e1087f:    done           |++++++++++++++++++++++++++++++++++++++|
layer-sha256:369ad5b9119b92446b3dfc671a05c25335f177e1faae9e14cd07e9ecc1528033:    done           |++++++++++++++++++++++++++++++++++++++|
layer-sha256:be83d0fd33a347ae91aa8ccf911f55c0780a11fc29408bc1eb3d5c0ccd695612:    done           |++++++++++++++++++++++++++++++++++++++|
layer-sha256:4f4fb700ef54461cfa02571ae0db9a0dc1e0cdb5577484a6d75e68dc38e8acc1:    done           |++++++++++++++++++++++++++++++++++++++|
layer-sha256:dd8d46bd4047234ff762742c1fe4f1c7607586fec1219836a52843d119f8133d:    done           |++++++++++++++++++++++++++++++++++++++|
layer-sha256:5057e26f1a86ccf8d3a0ae8a1de72d36ac1dce772741e3f000d89ff7a33dec3d:    done           |++++++++++++++++++++++++++++++++++++++|
elapsed: 12.2s                                                                    total:  17.6 M (1.4 MiB/s)

unpacking linux/amd64 sha256:c1e88455c85225310bbea54816e9c3f4b5295815e6dbf80c34d40afc6df28275...
done: 1.190561761s
```
</details>


- Image Run
<details><summary>ctr run docker.io/redis:apline</summary>

```diff
~ > sudo ctr run docker.io/library/redis:alpine redis                                                   13s 08:15:14 AM
1:C 02 Dec 2024 02:45:31.283 # WARNING Memory overcommit must be enabled! Without it, a background save or replication may fail under low memory condition. Being disabled, it can also cause failures without low memory condition, see https://github.com/jemalloc/jemalloc/issues/1328. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:C 02 Dec 2024 02:45:31.283 * oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 02 Dec 2024 02:45:31.283 * Redis version=7.4.1, bits=64, commit=00000000, modified=0, pid=1, just started
1:C 02 Dec 2024 02:45:31.283 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
1:M 02 Dec 2024 02:45:31.284 # You requested maxclients of 10000 requiring at least 10032 max file descriptors.
1:M 02 Dec 2024 02:45:31.284 # Server can't set maximum open files to 10032 because of OS error: Operation not permitted.
1:M 02 Dec 2024 02:45:31.284 # Current maximum open files is 1024. maxclients has been reduced to 992 to compensate for low ulimit. If you need higher maxclients increase 'ulimit -n'.
1:M 02 Dec 2024 02:45:31.284 * monotonic clock: POSIX clock_gettime
1:M 02 Dec 2024 02:45:31.285 * Running mode=standalone, port=6379.
1:M 02 Dec 2024 02:45:31.286 * Server initialized
1:M 02 Dec 2024 02:45:31.287 * Ready to accept connections tcp
```
</details>




