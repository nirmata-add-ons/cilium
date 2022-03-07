# cilium

Using Cilium as CNI for Nirmata

Cilium CNI provides one of the most efficient and fast routing for Kubernetes clusters with pollcy management and observability. A few uniques aspects of Cilium include - 

At the foundation of Cilium is a new Linux kernel technology called eBPF, which enables the dynamic insertion of powerful security visibility and control logic within Linux itself. Because eBPF runs inside the Linux kernel, Cilium security policies can be applied and updated without any changes to the application code or container configuration.
Cilium assigns a security identity to groups of application containers which share identical security policies. The identity is then associated with all network packets emitted by the application containers, allowing to validate the identity at the receiving node. Security identity management is performed using a key-value store.
Label based security is the tool of choice for cluster internal access control. In order to secure access to and from external services, traditional CIDR based security policies for both ingress and egress are supported. This allows to limit access to and from application containers to particular IP ranges.
It supports two routing modes - 
Overlay - Encapsulation-based virtual network spanning all hosts.
Native routing - Here pods use the regular routing table of the Linux host. The network is required to be capable of routing the IP addresses of the application containers.
Cilium implements distributed load balancing for traffic between application containers and to external services and is able to fully replace components such as kube-proxy. The load balancing is implemented in eBPF using efficient hashtables allowing for almost unlimited scale.
Bandwidth management - Cilium implements bandwidth management through efficient EDT-based (Earliest Departure Time) rate-limiting with eBPF for container traffic that is egressing a node. 
Monitoring and troubleshooting - Cilium can provide an in-depth view of traffic and also includes a hubble, observability UI tool.

Using Cilium with Nirmata

Cilium manipulates the /etc/cni directory and needs RW permission to the directory. This needs to be tweaked in kubelet volume configuration in Nirmata. The cilium CNI YAML is available here - 

