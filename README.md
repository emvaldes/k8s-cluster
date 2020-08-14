# Kubernetes @ Elastic Compute Cloud (Amazon EC2)

```console
$ k8s-cluster --help

Use:  k8s-cluster
      --access-pubkey=''
      --cluster-name='emvaldes'
      --create-cluster
      --delete-cluster
      --deploy-cluster
      --deploy-dashboard
      --deploy-prometheus
      --deploy-prototype
      --describe-cluster
      --domain-name
      --enable-cloudwatch
      --help-create
      --help-delete
      --interactive
      --kubeconfig='/Users/emvaldes/.kube/config'
      --profile='kubernetes'
      --region='us-east-1'
      --target-cluster='emvaldes.'
      --zones='us-east-1a,us-east-1b,us-east-1c'
      --verbose

Goodbye!
```

```console
$ k8s-cluster \
  --create-cluster=prototype.emvaldes.name \
  --deploy-cloudwatch \
  --deploy-prometheus \
  --deploy-dashboard \
  --deploy-prototype \
  --describe-cluster \
  --verbose \
  ;
```

or

```console
$ k8s-cluster \
  --create-cluster=prototype.emvaldes.name \
  --verbose \
  ;
```

```console
Account: 123456789012

Validating IAM Group: kubernetes
```

```json
{
    "AttachedPolicies": [
        {
            "PolicyName": "AdministratorAccess",
            "PolicyArn": "arn:aws:iam::aws:policy/AdministratorAccess"
        }
    ]
}
```

```console
Validating IAM User: kubernetes
```

```json
{
    "Users": [
        {
            "Path": "/",
            "UserName": "kubernetes",
            "UserId": "AIDA2XV4BKOYCPXHQKTVU",
            "Arn": "arn:aws:iam::123456789012:user/kubernetes",
            "CreateDate": "2020-04-03T03:29:23+00:00"
        }
    ],
    "Group": {
        "Path": "/",
        "GroupName": "kubernetes",
        "GroupId": "AGPA2XV4BKOYH67DC5EXH",
        "Arn": "arn:aws:iam::123456789012:group/kubernetes",
        "CreateDate": "2020-04-03T03:27:48+00:00"
    }
}
```

```json
{
    "Groups": [
        {
            "Path": "/",
            "GroupName": "kubernetes",
            "GroupId": "AGPA2XV4BKOYH67DC5EXH",
            "Arn": "arn:aws:iam::123456789012:group/kubernetes",
            "CreateDate": "2020-04-03T03:27:48+00:00"
        }
    ]
}
```

```console
Exporting prototype.emvaldes.name: ...

Environment:
      SSH Public Key:      id_rsa.pub
      AWS Profile:         kubernetes
      AWS Default Profile: kubernetes
      AWS Account Number:  123456789012
      Target TLDN:         emvaldes.name
      Master-Node Size:    t3a.xlarge
      Master-Node Zones:   us-east-1a,us-east-1b,us-east-1c
      Cluster Nodes Size:  t3a.large
      Cluster Nodes Zones: us-east-1a,us-east-1b,us-east-1c
      S3 Bucket Name:      kubernetes-states--123456789012

AWS Configurations
      AWS Default Region: us-east-1
      Default Profile:    kubernetes
      Config File:        /Users/emvaldes/.aws/config
      Default Output:     json
      Default Region:     us-east-1
      SAML2 AWS Profile:  devops
      Shared Credentials: /Users/emvaldes/.aws/credentials
      Availability Zones: us-east-1a,us-east-1b,us-east-1c

KOPS Configurations
      KOPS Cluster Name:   prototype.emvaldes.name
      KOPS State Store:    s3://kubernetes-states--123456789012
      KOPS Feature Flags:  SpecOverrideFlag
      Kubernetes Provider: aws
```

```console
Inquiring emvaldes.name Name Servers:
emvaldes.name name server ns-1311.awsdns-35.org.
emvaldes.name name server ns-134.awsdns-16.com.
emvaldes.name name server ns-1638.awsdns-12.co.uk.
emvaldes.name name server ns-748.awsdns-29.net.

Inquiring emvaldes.name SOA:
emvaldes.name has SOA record ns-134.awsdns-16.com. awsdns-hostmaster.amazon.com. 1 7200 900 1209600 86400
```

```console
Creating Route53 Hosted-Zone [prototype.emvaldes.name] ( Kubernetes Cluster HostedZone ) ...

Validating Route53 Hosted-Zone [prototype.emvaldes.name] ...
```

```json
{
    "Location": "https://route53.amazonaws.com/2013-04-01/hostedzone/Z07723263T3E4SGWJ11FJ",
    "HostedZone": {
        "Id": "/hostedzone/Z07723263T3E4SGWJ11FJ",
        "Name": "prototype.emvaldes.name.",
        "CallerReference": "20200812185732",
        "Config": {
            "Comment": "Kubernetes Cluster HostedZone",
            "PrivateZone": false
        },
        "ResourceRecordSetCount": 2
    },
    "ChangeInfo": {
        "Id": "/change/C07950843T1LHGFTZ1VZ3",
        "Status": "PENDING",
        "SubmittedAt": "2020-08-13T01:57:33.336000+00:00"
    },
    "DelegationSet": {
        "NameServers": [
            "ns-1336.awsdns-39.org",
            "ns-529.awsdns-02.net",
            "ns-246.awsdns-30.com",
            "ns-1556.awsdns-02.co.uk"
        ]
    }
}
```

```console
Route53 Record Set [prototype.emvaldes.name] ...
Record Set prototype.emvaldes.name does not exist!
```

```json
{
    "ChangeInfo": {
        "Id": "/change/C09500362UAC13B9GEVSV",
        "Status": "PENDING",
        "SubmittedAt": "2020-08-13T01:58:15.855000+00:00",
        "Comment": "Creating Record-Set"
    }
}
```

```console
Inquiring prototype.emvaldes.name Name Servers:
prototype.emvaldes.name name server ns-1556.awsdns-02.co.uk.
prototype.emvaldes.name name server ns-246.awsdns-30.com.
prototype.emvaldes.name name server ns-529.awsdns-02.net.
prototype.emvaldes.name name server ns-1336.awsdns-39.org.

Inquiring prototype.emvaldes.name SOA:
prototype.emvaldes.name has SOA record ns-1336.awsdns-39.org. awsdns-hostmaster.amazon.com. 1 7200 900 1209600 86400
```

```console
Creating S3 Bucket: kubernetes-states--123456789012 ...
```

```json
{
    "Location": "/kubernetes-states--123456789012"
}
```

```console
Placing Bucket-Versioning Policy ...
Configuring Public-Access settings ...
Applying S3 Bucket Policy ...
```

```console
Creating Kubernetes Cluster: prototype.emvaldes.name ...

; <<>> DiG 9.10.6 <<>> prototype.emvaldes.name
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 46663
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;prototype.emvaldes.name.	IN	A

;; AUTHORITY SECTION:
prototype.emvaldes.name. 900	IN	SOA	ns-1336.awsdns-39.org. awsdns-hostmaster.amazon.com. 1 7200 900 1209600 86400

;; Query time: 224 msec
;; SERVER: 2001:578:3f::30#53(2001:578:3f::30)
;; WHEN: Wed Aug 12 18:59:28 MST 2020
;; MSG SIZE  rcvd: 126
```

```console
I0812 18:59:29.134000    5353 featureflag.go:154] FeatureFlag "SpecOverrideFlag"=true
I0812 18:59:29.157215    5353 create_cluster.go:1547] Using SSH public key: /Users/emvaldes/.ssh/kubernetes.pub
I0812 18:59:30.824924    5353 create_cluster.go:557] Inferred --cloud=aws from zone "us-east-1a"
I0812 18:59:31.201482    5353 subnets.go:184] Assigned CIDR 172.20.32.0/19 to subnet us-east-1a
I0812 18:59:31.201516    5353 subnets.go:184] Assigned CIDR 172.20.64.0/19 to subnet us-east-1b
I0812 18:59:31.201525    5353 subnets.go:184] Assigned CIDR 172.20.96.0/19 to subnet us-east-1c
I0812 18:59:31.499716    5353 kubelet.go:137] Cloud Provider: aws
I0812 18:59:31.500288    5353 kubelet.go:137] Cloud Provider: aws
I0812 18:59:31.500817    5353 spec_builder.go:49] options:
```

```json
{
  "channel": "stable",
  "configBase": "s3://kubernetes-states--123456789012/prototype.emvaldes.name",
  "cloudProvider": "aws",
  "containerRuntime": "docker",
  "kubernetesVersion": "1.18.6",
  "subnets": [
    {
      "name": "us-east-1a",
      "cidr": "172.20.32.0/19",
      "zone": "us-east-1a",
      "type": "Public"
    },
    {
      "name": "us-east-1b",
      "cidr": "172.20.64.0/19",
      "zone": "us-east-1b",
      "type": "Public"
    },
    {
      "name": "us-east-1c",
      "cidr": "172.20.96.0/19",
      "zone": "us-east-1c",
      "type": "Public"
    }
  ],
  "masterPublicName": "api.prototype.emvaldes.name",
  "masterInternalName": "api.internal.prototype.emvaldes.name",
  "networkCIDR": "172.20.0.0/16",
  "topology": {
    "masters": "public",
    "nodes": "public",
    "dns": {
      "type": "Public"
    }
  },
  "secretStore": "s3://kubernetes-states--123456789012/prototype.emvaldes.name/secrets",
  "keyStore": "s3://kubernetes-states--123456789012/prototype.emvaldes.name/pki",
  "configStore": "s3://kubernetes-states--123456789012/prototype.emvaldes.name",
  "dnsZone": "prototype.emvaldes.name",
  "clusterDNSDomain": "cluster.local",
  "serviceClusterIPRange": "100.64.0.0/13",
  "nonMasqueradeCIDR": "100.64.0.0/10",
  "sshAccess": [
    "0.0.0.0/0"
  ],
  "kubernetesApiAccess": [
    "0.0.0.0/0"
  ],
  "etcdClusters": [
    {
      "name": "main",
      "provider": "Manager",
      "etcdMembers": [
        {
          "name": "a",
          "instanceGroup": "master-us-east-1a"
        },
        {
          "name": "b",
          "instanceGroup": "master-us-east-1b"
        },
        {
          "name": "c",
          "instanceGroup": "master-us-east-1c"
        }
      ],
      "enableEtcdTLS": true,
      "enableTLSAuth": true,
      "version": "3.4.3",
      "backups": {
        "backupStore": "s3://kubernetes-states--123456789012/prototype.emvaldes.name/backups/etcd/main"
      },
      "manager": {},
      "memoryRequest": "100Mi",
      "cpuRequest": "200m"
    },
    {
      "name": "events",
      "provider": "Manager",
      "etcdMembers": [
        {
          "name": "a",
          "instanceGroup": "master-us-east-1a"
        },
        {
          "name": "b",
          "instanceGroup": "master-us-east-1b"
        },
        {
          "name": "c",
          "instanceGroup": "master-us-east-1c"
        }
      ],
      "enableEtcdTLS": true,
      "enableTLSAuth": true,
      "version": "3.4.3",
      "backups": {
        "backupStore": "s3://kubernetes-states--123456789012/prototype.emvaldes.name/backups/etcd/events"
      },
      "manager": {},
      "memoryRequest": "100Mi",
      "cpuRequest": "100m"
    }
  ],
  "containerd": {
    "configOverride": "disabled_plugins = [\"cri\"]\n",
    "logLevel": "info",
    "version": "1.2.13"
  },
  "docker": {
    "ipMasq": false,
    "ipTables": false,
    "logDriver": "json-file",
    "logLevel": "warn",
    "logOpt": [
      "max-size=10m",
      "max-file=5"
    ],
    "storage": "overlay2,overlay,aufs",
    "version": "19.03.11"
  },
  "kubeDNS": {
    "cacheMaxSize": 1000,
    "cacheMaxConcurrent": 150,
    "domain": "cluster.local",
    "replicas": 2,
    "serverIP": "100.64.0.10",
    "memoryRequest": "70Mi",
    "cpuRequest": "100m",
    "memoryLimit": "170Mi"
  },
  "kubeAPIServer": {
    "image": "k8s.gcr.io/kube-apiserver:v1.18.6",
    "logLevel": 2,
    "cloudProvider": "aws",
    "securePort": 443,
    "bindAddress": "0.0.0.0",
    "insecureBindAddress": "127.0.0.1",
    "enableAdmissionPlugins": [
      "NamespaceLifecycle",
      "LimitRanger",
      "ServiceAccount",
      "PersistentVolumeLabel",
      "DefaultStorageClass",
      "DefaultTolerationSeconds",
      "MutatingAdmissionWebhook",
      "ValidatingAdmissionWebhook",
      "NodeRestriction",
      "ResourceQuota"
    ],
    "serviceClusterIPRange": "100.64.0.0/13",
    "etcdServers": [
      "http://127.0.0.1:4001"
    ],
    "etcdServersOverrides": [
      "/events#http://127.0.0.1:4002"
    ],
    "allowPrivileged": true,
    "apiServerCount": 3,
    "anonymousAuth": false,
    "kubeletPreferredAddressTypes": [
      "InternalIP",
      "Hostname",
      "ExternalIP"
    ],
    "storageBackend": "etcd3",
    "authorizationMode": "RBAC",
    "requestheaderUsernameHeaders": [
      "X-Remote-User"
    ],
    "requestheaderGroupHeaders": [
      "X-Remote-Group"
    ],
    "requestheaderExtraHeaderPrefixes": [
      "X-Remote-Extra-"
    ],
    "requestheaderAllowedNames": [
      "aggregator"
    ]
  },
  "kubeControllerManager": {
    "logLevel": 2,
    "image": "k8s.gcr.io/kube-controller-manager:v1.18.6",
    "cloudProvider": "aws",
    "clusterName": "prototype.emvaldes.name",
    "clusterCIDR": "100.96.0.0/11",
    "allocateNodeCIDRs": true,
    "configureCloudRoutes": false,
    "leaderElection": {
      "leaderElect": true
    },
    "attachDetachReconcileSyncPeriod": "1m0s",
    "useServiceAccountCredentials": true
  },
  "kubeScheduler": {
    "logLevel": 2,
    "image": "k8s.gcr.io/kube-scheduler:v1.18.6",
    "leaderElection": {
      "leaderElect": true
    }
  },
  "kubeProxy": {
    "image": "k8s.gcr.io/kube-proxy:v1.18.6",
    "cpuRequest": "100m",
    "logLevel": 2,
    "clusterCIDR": "100.96.0.0/11",
    "hostnameOverride": "@aws"
  },
  "kubelet": {
    "anonymousAuth": false,
    "kubeconfigPath": "/var/lib/kubelet/kubeconfig",
    "logLevel": 2,
    "podManifestPath": "/etc/kubernetes/manifests",
    "hostnameOverride": "@aws",
    "podInfraContainerImage": "k8s.gcr.io/pause-amd64:3.2",
    "enableDebuggingHandlers": true,
    "clusterDomain": "cluster.local",
    "clusterDNS": "100.64.0.10",
    "networkPluginName": "cni",
    "cloudProvider": "aws",
    "cgroupRoot": "/",
    "nonMasqueradeCIDR": "100.64.0.0/10",
    "evictionHard": "memory.available\u003c100Mi,nodefs.available\u003c10%,nodefs.inodesFree\u003c5%,imagefs.available\u003c10%,imagefs.inodesFree\u003c5%"
  },
  "masterKubelet": {
    "anonymousAuth": false,
    "kubeconfigPath": "/var/lib/kubelet/kubeconfig",
    "logLevel": 2,
    "podManifestPath": "/etc/kubernetes/manifests",
    "hostnameOverride": "@aws",
    "podInfraContainerImage": "k8s.gcr.io/pause-amd64:3.2",
    "enableDebuggingHandlers": true,
    "clusterDomain": "cluster.local",
    "clusterDNS": "100.64.0.10",
    "networkPluginName": "cni",
    "cloudProvider": "aws",
    "cgroupRoot": "/",
    "registerSchedulable": false,
    "nonMasqueradeCIDR": "100.64.0.0/10",
    "evictionHard": "memory.available\u003c100Mi,nodefs.available\u003c10%,nodefs.inodesFree\u003c5%,imagefs.available\u003c10%,imagefs.inodesFree\u003c5%"
  },
  "networking": {
    "weave": {
      "mtu": 8912
    }
  },
  "api": {
    "dns": {}
  },
  "authorization": {
    "rbac": {}
  },
  "iam": {
    "legacy": false,
    "allowContainerRegistry": true
  }
}
```

```console
I0812 18:59:33.846262    5353 kubelet.go:137] Cloud Provider: aws
I0812 18:59:33.846907    5353 kubelet.go:137] Cloud Provider: aws
I0812 18:59:33.847423    5353 spec_builder.go:49] options:
```

```json
{
  "channel": "stable",
  "configBase": "s3://kubernetes-states--123456789012/prototype.emvaldes.name",
  "cloudProvider": "aws",
  "containerRuntime": "docker",
  "kubernetesVersion": "1.18.6",
  "subnets": [
    {
      "name": "us-east-1a",
      "cidr": "172.20.32.0/19",
      "zone": "us-east-1a",
      "type": "Public"
    },
    {
      "name": "us-east-1b",
      "cidr": "172.20.64.0/19",
      "zone": "us-east-1b",
      "type": "Public"
    },
    {
      "name": "us-east-1c",
      "cidr": "172.20.96.0/19",
      "zone": "us-east-1c",
      "type": "Public"
    }
  ],
  "masterPublicName": "api.prototype.emvaldes.name",
  "masterInternalName": "api.internal.prototype.emvaldes.name",
  "networkCIDR": "172.20.0.0/16",
  "topology": {
    "masters": "public",
    "nodes": "public",
    "dns": {
      "type": "Public"
    }
  },
  "secretStore": "s3://kubernetes-states--123456789012/prototype.emvaldes.name/secrets",
  "keyStore": "s3://kubernetes-states--123456789012/prototype.emvaldes.name/pki",
  "configStore": "s3://kubernetes-states--123456789012/prototype.emvaldes.name",
  "dnsZone": "prototype.emvaldes.name",
  "clusterDNSDomain": "cluster.local",
  "serviceClusterIPRange": "100.64.0.0/13",
  "nonMasqueradeCIDR": "100.64.0.0/10",
  "sshAccess": [
    "0.0.0.0/0"
  ],
  "kubernetesApiAccess": [
    "0.0.0.0/0"
  ],
  "etcdClusters": [
    {
      "name": "main",
      "provider": "Manager",
      "etcdMembers": [
        {
          "name": "a",
          "instanceGroup": "master-us-east-1a"
        },
        {
          "name": "b",
          "instanceGroup": "master-us-east-1b"
        },
        {
          "name": "c",
          "instanceGroup": "master-us-east-1c"
        }
      ],
      "enableEtcdTLS": true,
      "enableTLSAuth": true,
      "version": "3.4.3",
      "backups": {
        "backupStore": "s3://kubernetes-states--123456789012/prototype.emvaldes.name/backups/etcd/main"
      },
      "manager": {},
      "memoryRequest": "100Mi",
      "cpuRequest": "200m"
    },
    {
      "name": "events",
      "provider": "Manager",
      "etcdMembers": [
        {
          "name": "a",
          "instanceGroup": "master-us-east-1a"
        },
        {
          "name": "b",
          "instanceGroup": "master-us-east-1b"
        },
        {
          "name": "c",
          "instanceGroup": "master-us-east-1c"
        }
      ],
      "enableEtcdTLS": true,
      "enableTLSAuth": true,
      "version": "3.4.3",
      "backups": {
        "backupStore": "s3://kubernetes-states--123456789012/prototype.emvaldes.name/backups/etcd/events"
      },
      "manager": {},
      "memoryRequest": "100Mi",
      "cpuRequest": "100m"
    }
  ],
  "containerd": {
    "configOverride": "disabled_plugins = [\"cri\"]\n",
    "logLevel": "info",
    "version": "1.2.13"
  },
  "docker": {
    "ipMasq": false,
    "ipTables": false,
    "logDriver": "json-file",
    "logLevel": "warn",
    "logOpt": [
      "max-size=10m",
      "max-file=5"
    ],
    "storage": "overlay2,overlay,aufs",
    "version": "19.03.11"
  },
  "kubeDNS": {
    "cacheMaxSize": 1000,
    "cacheMaxConcurrent": 150,
    "domain": "cluster.local",
    "replicas": 2,
    "serverIP": "100.64.0.10",
    "memoryRequest": "70Mi",
    "cpuRequest": "100m",
    "memoryLimit": "170Mi"
  },
  "kubeAPIServer": {
    "image": "k8s.gcr.io/kube-apiserver:v1.18.6",
    "logLevel": 2,
    "cloudProvider": "aws",
    "securePort": 443,
    "bindAddress": "0.0.0.0",
    "insecureBindAddress": "127.0.0.1",
    "enableAdmissionPlugins": [
      "NamespaceLifecycle",
      "LimitRanger",
      "ServiceAccount",
      "PersistentVolumeLabel",
      "DefaultStorageClass",
      "DefaultTolerationSeconds",
      "MutatingAdmissionWebhook",
      "ValidatingAdmissionWebhook",
      "NodeRestriction",
      "ResourceQuota"
    ],
    "serviceClusterIPRange": "100.64.0.0/13",
    "etcdServers": [
      "http://127.0.0.1:4001"
    ],
    "etcdServersOverrides": [
      "/events#http://127.0.0.1:4002"
    ],
    "allowPrivileged": true,
    "apiServerCount": 3,
    "anonymousAuth": false,
    "kubeletPreferredAddressTypes": [
      "InternalIP",
      "Hostname",
      "ExternalIP"
    ],
    "storageBackend": "etcd3",
    "authorizationMode": "RBAC",
    "requestheaderUsernameHeaders": [
      "X-Remote-User"
    ],
    "requestheaderGroupHeaders": [
      "X-Remote-Group"
    ],
    "requestheaderExtraHeaderPrefixes": [
      "X-Remote-Extra-"
    ],
    "requestheaderAllowedNames": [
      "aggregator"
    ]
  },
  "kubeControllerManager": {
    "logLevel": 2,
    "image": "k8s.gcr.io/kube-controller-manager:v1.18.6",
    "cloudProvider": "aws",
    "clusterName": "prototype.emvaldes.name",
    "clusterCIDR": "100.96.0.0/11",
    "allocateNodeCIDRs": true,
    "configureCloudRoutes": false,
    "leaderElection": {
      "leaderElect": true
    },
    "attachDetachReconcileSyncPeriod": "1m0s",
    "useServiceAccountCredentials": true
  },
  "kubeScheduler": {
    "logLevel": 2,
    "image": "k8s.gcr.io/kube-scheduler:v1.18.6",
    "leaderElection": {
      "leaderElect": true
    }
  },
  "kubeProxy": {
    "image": "k8s.gcr.io/kube-proxy:v1.18.6",
    "cpuRequest": "100m",
    "logLevel": 2,
    "clusterCIDR": "100.96.0.0/11",
    "hostnameOverride": "@aws"
  },
  "kubelet": {
    "anonymousAuth": false,
    "kubeconfigPath": "/var/lib/kubelet/kubeconfig",
    "logLevel": 2,
    "podManifestPath": "/etc/kubernetes/manifests",
    "hostnameOverride": "@aws",
    "podInfraContainerImage": "k8s.gcr.io/pause-amd64:3.2",
    "enableDebuggingHandlers": true,
    "clusterDomain": "cluster.local",
    "clusterDNS": "100.64.0.10",
    "networkPluginName": "cni",
    "cloudProvider": "aws",
    "cgroupRoot": "/",
    "nonMasqueradeCIDR": "100.64.0.0/10",
    "evictionHard": "memory.available\u003c100Mi,nodefs.available\u003c10%,nodefs.inodesFree\u003c5%,imagefs.available\u003c10%,imagefs.inodesFree\u003c5%"
  },
  "masterKubelet": {
    "anonymousAuth": false,
    "kubeconfigPath": "/var/lib/kubelet/kubeconfig",
    "logLevel": 2,
    "podManifestPath": "/etc/kubernetes/manifests",
    "hostnameOverride": "@aws",
    "podInfraContainerImage": "k8s.gcr.io/pause-amd64:3.2",
    "enableDebuggingHandlers": true,
    "clusterDomain": "cluster.local",
    "clusterDNS": "100.64.0.10",
    "networkPluginName": "cni",
    "cloudProvider": "aws",
    "cgroupRoot": "/",
    "registerSchedulable": false,
    "nonMasqueradeCIDR": "100.64.0.0/10",
    "evictionHard": "memory.available\u003c100Mi,nodefs.available\u003c10%,nodefs.inodesFree\u003c5%,imagefs.available\u003c10%,imagefs.inodesFree\u003c5%"
  },
  "networking": {
    "weave": {
      "mtu": 8912
    }
  },
  "api": {
    "dns": {}
  },
  "authorization": {
    "rbac": {}
  },
  "iam": {
    "legacy": false,
    "allowContainerRegistry": true
  }
}
```

```console
I0812 18:59:37.723920    5353 executor.go:103] Tasks: 0 done / 101 total; 49 can run
I0812 18:59:38.420570    5353 vfs_castore.go:590] Issuing new certificate: "etcd-manager-ca-main"
I0812 18:59:38.421981    5353 vfs_castore.go:590] Issuing new certificate: "etcd-clients-ca"
I0812 18:59:38.455900    5353 vfs_castore.go:590] Issuing new certificate: "ca"
I0812 18:59:38.488722    5353 vfs_castore.go:590] Issuing new certificate: "etcd-peers-ca-main"
I0812 18:59:38.531500    5353 vfs_castore.go:590] Issuing new certificate: "apiserver-aggregator-ca"
I0812 18:59:38.679162    5353 vfs_castore.go:590] Issuing new certificate: "etcd-manager-ca-events"
I0812 18:59:38.866309    5353 vfs_castore.go:590] Issuing new certificate: "etcd-peers-ca-events"
I0812 18:59:40.224270    5353 executor.go:103] Tasks: 49 done / 101 total; 28 can run
I0812 18:59:40.791816    5353 vfs_castore.go:590] Issuing new certificate: "kube-proxy"
I0812 18:59:40.793969    5353 vfs_castore.go:590] Issuing new certificate: "apiserver-aggregator"
I0812 18:59:40.803255    5353 vfs_castore.go:590] Issuing new certificate: "kops"
I0812 18:59:40.805939    5353 vfs_castore.go:590] Issuing new certificate: "kubelet-api"
I0812 18:59:40.837280    5353 vfs_castore.go:590] Issuing new certificate: "apiserver-proxy-client"
I0812 18:59:40.851924    5353 vfs_castore.go:590] Issuing new certificate: "kube-controller-manager"
I0812 18:59:40.870319    5353 vfs_castore.go:590] Issuing new certificate: "master"
I0812 18:59:40.893956    5353 vfs_castore.go:590] Issuing new certificate: "kubelet"
I0812 18:59:40.924598    5353 vfs_castore.go:590] Issuing new certificate: "kube-scheduler"
I0812 18:59:40.942974    5353 vfs_castore.go:590] Issuing new certificate: "kubecfg"
I0812 18:59:42.371767    5353 executor.go:103] Tasks: 77 done / 101 total; 20 can run
I0812 18:59:43.403123    5353 launchconfiguration.go:375] waiting for IAM instance profile "masters.prototype.emvaldes.name" to be ready
I0812 18:59:43.420708    5353 launchconfiguration.go:375] waiting for IAM instance profile "masters.prototype.emvaldes.name" to be ready
I0812 18:59:43.621538    5353 launchconfiguration.go:375] waiting for IAM instance profile "nodes.prototype.emvaldes.name" to be ready
I0812 18:59:43.672523    5353 launchconfiguration.go:375] waiting for IAM instance profile "masters.prototype.emvaldes.name" to be ready
I0812 18:59:54.643925    5353 executor.go:103] Tasks: 97 done / 101 total; 4 can run
I0812 18:59:55.618335    5353 executor.go:103] Tasks: 101 done / 101 total; 0 can run
I0812 18:59:55.618378    5353 dns.go:156] Pre-creating DNS records
I0812 18:59:57.142182    5353 update_cluster.go:308] Exporting kubecfg for cluster
kops has set your kubectl context to prototype.emvaldes.name

Cluster is starting.  It should be ready in a few minutes.

Suggestions:
 * validate cluster: kops validate cluster --wait 10m
 * list nodes: kubectl get nodes --show-labels
 * ssh to the master: ssh -i ~/.ssh/id_rsa ubuntu@api.prototype.emvaldes.name
 * the ubuntu user is specific to Ubuntu. If not using Ubuntu please use the appropriate user based on your OS.
 * read about installing addons at: https://kops.sigs.k8s.io/operations/addons.
```

```console
; <<>> DiG 9.10.6 <<>> api.prototype.emvaldes.name
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 31155
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;api.prototype.emvaldes.name.	IN	A

;; AUTHORITY SECTION:
prototype.emvaldes.name. 900	IN	SOA	ns-1336.awsdns-39.org. awsdns-hostmaster.amazon.com. 1 7200 900 1209600 86400

;; Query time: 8745 msec
;; SERVER: 2001:578:3f::30#53(2001:578:3f::30)
;; WHEN: Wed Aug 12 19:00:06 MST 2020
;; MSG SIZE  rcvd: 130

; <<>> DiG 9.10.6 <<>> api.internal.prototype.emvaldes.name
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47482
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;api.internal.prototype.emvaldes.name. IN A

;; ANSWER SECTION:
api.internal.prototype.emvaldes.name. 10 IN A	203.0.113.123

;; Query time: 27 msec
;; SERVER: 68.105.28.11#53(68.105.28.11)
;; WHEN: Wed Aug 12 19:00:08 MST 2020
;; MSG SIZE  rcvd: 70

done! [ 18 mins. ]
```

```console
Switched to context "prototype.emvaldes.name".
clusterrole.rbac.authorization.k8s.io/system:aggregated-metrics-reader created
clusterrolebinding.rbac.authorization.k8s.io/metrics-server:system:auth-delegator created
rolebinding.rbac.authorization.k8s.io/metrics-server-auth-reader created
apiservice.apiregistration.k8s.io/v1beta1.metrics.k8s.io created
serviceaccount/metrics-server created
deployment.apps/metrics-server created
service/metrics-server created
clusterrole.rbac.authorization.k8s.io/system:metrics-server created
clusterrolebinding.rbac.authorization.k8s.io/system:metrics-server created
namespace/amazon-cloudwatch created
namespace/amazon-cloudwatch unchanged
serviceaccount/cloudwatch-agent created
clusterrole.rbac.authorization.k8s.io/cloudwatch-agent-role created
clusterrolebinding.rbac.authorization.k8s.io/cloudwatch-agent-role-binding created
configmap/cwagentconfig created
daemonset.apps/cloudwatch-agent created
configmap/cluster-info created
serviceaccount/fluentd created
clusterrole.rbac.authorization.k8s.io/fluentd-role created
clusterrolebinding.rbac.authorization.k8s.io/fluentd-role-binding created
configmap/fluentd-config created
daemonset.apps/fluentd-cloudwatch created
```

```console
NAME                       READY   STATUS              RESTARTS   AGE   IP       NODE                             NOMINATED NODE   READINESS GATES
cloudwatch-agent-g88vz     0/1     ContainerCreating   0          2s    <none>   ip-172-20-63-5.ec2.internal      <none>           <none>
fluentd-cloudwatch-d6rsq   0/1     Init:0/2            0          1s    <none>   ip-172-20-63-5.ec2.internal      <none>           <none>
cloudwatch-agent-78ssb     0/1     ContainerCreating   0          2s    <none>   ip-172-20-80-214.ec2.internal    <none>           <none>
fluentd-cloudwatch-fmrpl   0/1     Init:0/2            0          1s    <none>   ip-172-20-80-214.ec2.internal    <none>           <none>
cloudwatch-agent-gqft5     0/1     ContainerCreating   0          2s    <none>   ip-172-20-120-109.ec2.internal   <none>           <none>
fluentd-cloudwatch-4ngws   0/1     Init:0/2            0          1s    <none>   ip-172-20-120-109.ec2.internal   <none>           <none>
```

```console
serviceaccount/cloudwatch-agent unchanged
clusterrole.rbac.authorization.k8s.io/cloudwatch-agent-role unchanged
clusterrolebinding.rbac.authorization.k8s.io/cloudwatch-agent-role-binding unchanged
configmap/cwagentconfig configured
daemonset.apps/cloudwatch-agent unchanged
```

```console
Describing Pod: cloudwatch-agent-78ssb
```

```yaml
Name:         cloudwatch-agent-78ssb
Namespace:    amazon-cloudwatch
Priority:     0
Node:         ip-172-20-80-214.ec2.internal/172.20.80.214
Start Time:   Wed, 12 Aug 2020 19:18:27 -0700
Labels:       controller-revision-hash=ccd5c6c8b
              name=cloudwatch-agent
              pod-template-generation=1
Annotations:  <none>
Status:       Running
IP:           100.100.0.2
IPs:
  IP:           100.100.0.2
Controlled By:  DaemonSet/cloudwatch-agent
Containers:
  cloudwatch-agent:
    Container ID:   docker://358c4315b88548f5a994c5c3d786b3b949bfe2bd9c681b892033c6e0f82528f9
    Image:          amazon/cloudwatch-agent:1.230621.0
    Image ID:       docker-pullable://amazon/cloudwatch-agent@sha256:877106acbc56e747ebe373548c88cd37274f666ca11b5c782211db4c5c7fb64b
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Wed, 12 Aug 2020 19:18:31 -0700
    Ready:          True
    Restart Count:  0
    Limits:
      cpu:     200m
      memory:  200Mi
    Requests:
      cpu:     200m
      memory:  200Mi
    Environment:
      HOST_IP:         (v1:status.hostIP)
      HOST_NAME:       (v1:spec.nodeName)
      K8S_NAMESPACE:  amazon-cloudwatch (v1:metadata.namespace)
      CI_VERSION:     k8s/1.0.1
    Mounts:
      /dev/disk from devdisk (ro)
      /etc/cwagentconfig from cwagentconfig (rw)
      /rootfs from rootfs (ro)
      /sys from sys (ro)
      /var/lib/docker from varlibdocker (ro)
      /var/run/docker.sock from dockersock (ro)
      /var/run/secrets/kubernetes.io/serviceaccount from cloudwatch-agent-token-n2nr6 (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             True
  ContainersReady   True
  PodScheduled      True
Volumes:
  cwagentconfig:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name:      cwagentconfig
    Optional:  false
  rootfs:
    Type:          HostPath (bare host directory volume)
    Path:          /
    HostPathType:
  dockersock:
    Type:          HostPath (bare host directory volume)
    Path:          /var/run/docker.sock
    HostPathType:
  varlibdocker:
    Type:          HostPath (bare host directory volume)
    Path:          /var/lib/docker
    HostPathType:
  sys:
    Type:          HostPath (bare host directory volume)
    Path:          /sys
    HostPathType:
  devdisk:
    Type:          HostPath (bare host directory volume)
    Path:          /dev/disk/
    HostPathType:
  cloudwatch-agent-token-n2nr6:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  cloudwatch-agent-token-n2nr6
    Optional:    false
QoS Class:       Guaranteed
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/disk-pressure:NoSchedule
                 node.kubernetes.io/memory-pressure:NoSchedule
                 node.kubernetes.io/not-ready:NoExecute
                 node.kubernetes.io/pid-pressure:NoSchedule
                 node.kubernetes.io/unreachable:NoExecute
                 node.kubernetes.io/unschedulable:NoSchedule
Events:
  Type    Reason     Age   From                                    Message
  ----    ------     ----  ----                                    -------
  Normal  Scheduled  12s   default-scheduler                       Successfully assigned amazon-cloudwatch/cloudwatch-agent-78ssb to ip-172-20-80-214.ec2.internal
  Normal  Pulling    12s   kubelet, ip-172-20-80-214.ec2.internal  Pulling image "amazon/cloudwatch-agent:1.230621.0"
  Normal  Pulled     9s    kubelet, ip-172-20-80-214.ec2.internal  Successfully pulled image "amazon/cloudwatch-agent:1.230621.0"
  Normal  Created    8s    kubelet, ip-172-20-80-214.ec2.internal  Created container cloudwatch-agent
  Normal  Started    8s    kubelet, ip-172-20-80-214.ec2.internal  Started container cloudwatch-agent
Countdown: 5
```

```console
Displaying Pod's Log: cloudwatch-agent-78ssb

2020/08/13 02:18:31 I! I! Detected the instance is EC2
2020/08/13 02:18:31 Reading json config file path: /opt/aws/amazon-cloudwatch-agent/bin/default_linux_config.json ...
/opt/aws/amazon-cloudwatch-agent/bin/default_linux_config.json does not exist or cannot read. Skipping it.
2020/08/13 02:18:31 Reading json config file path: /etc/cwagentconfig/..2020_08_13_02_18_27.214964752/cwagentconfig.json ...
2020/08/13 02:18:31 Find symbolic link /etc/cwagentconfig/..data
2020/08/13 02:18:31 Find symbolic link /etc/cwagentconfig/cwagentconfig.json
2020/08/13 02:18:31 Reading json config file path: /etc/cwagentconfig/cwagentconfig.json ...
Valid Json input schema.
No csm configuration found.
No metric configuration found.
```

```console
Configuration validation first phase succeeded

2020/08/13 02:18:31 I! Config has been translated into TOML /opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.toml
2020/08/13 02:18:31 I! AmazonCloudWatchAgent Version 1.230621.0.
2020-08-13T02:18:31Z I! Starting AmazonCloudWatchAgent (version 1.230621.0)
2020-08-13T02:18:31Z I! Loaded outputs: cloudwatchlogs
2020-08-13T02:18:31Z I! Loaded inputs: cadvisor k8sapiserver
2020-08-13T02:18:31Z I! Tags enabled:
2020-08-13T02:18:31Z I! Agent Config: Interval:1m0s, Quiet:false, Hostname:"ip-172-20-80-214.ec2.internal", Flush Interval:1s
2020-08-13T02:18:33Z E! refresh EC2 Instance Tags failed: UnauthorizedOperation: You are not authorized to perform this operation.
	status code: 403, request id: 6d2a1763-b04d-47c0-9d45-e28b28751e7c, metrics will be dropped until it got fixed
namespace/prometheus created
```

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: tiller
  namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: tiller
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
  - kind: ServiceAccount
    name: tiller
    namespace: kube-system
```

```console
serviceaccount/tiller created
clusterrolebinding.rbac.authorization.k8s.io/tiller created
$HELM_HOME has been configured at /Users/emvaldes/.helm.

Tiller (the Helm server-side component) has been installed into your Kubernetes Cluster.

Please note: by default, Tiller is deployed with an insecure 'allow unauthenticated users' policy.
To prevent this, run `helm init` with the --tiller-tls-verify flag.
For more information on securing your installation see: https://v2.helm.sh/docs/securing_installation/

Countdown: 15
NAME            READY   UP-TO-DATE   AVAILABLE   AGE
tiller-deploy   1/1     1            1           61s
```

```yaml
Name:                   tiller-deploy
Namespace:              kube-system
CreationTimestamp:      Wed, 12 Aug 2020 19:18:58 -0700
Labels:                 app=helm
                        name=tiller
Annotations:            deployment.kubernetes.io/revision: 1
Selector:               app=helm,name=tiller
Replicas:               1 desired | 1 updated | 1 total | 1 available | 0 unavailable
StrategyType:           RollingUpdate
MinReadySeconds:        0
RollingUpdateStrategy:  25% max unavailable, 25% max surge
Pod Template:
  Labels:           app=helm
                    name=tiller
  Service Account:  tiller
  Containers:
   tiller:
    Image:       gcr.io/kubernetes-helm/tiller:v2.16.9
    Ports:       44134/TCP, 44135/TCP
    Host Ports:  0/TCP, 0/TCP
    Liveness:    http-get http://:44135/liveness delay=1s timeout=1s period=10s #success=1 #failure=3
    Readiness:   http-get http://:44135/readiness delay=1s timeout=1s period=10s #success=1 #failure=3
    Environment:
      TILLER_NAMESPACE:    kube-system
      TILLER_HISTORY_MAX:  300
    Mounts:                <none>
  Volumes:                 <none>
Conditions:
  Type           Status  Reason
  ----           ------  ------
  Available      True    MinimumReplicasAvailable
  Progressing    True    NewReplicaSetAvailable
OldReplicaSets:  <none>
NewReplicaSet:   tiller-deploy-5c8959c79b (1/1 replicas created)
Events:
  Type    Reason             Age   From                   Message
  ----    ------             ----  ----                   -------
  Normal  ScalingReplicaSet  62s   deployment-controller  Scaled up replica set tiller-deploy-5c8959c79b to 1
NAME:   prometheus
LAST DEPLOYED: Wed Aug 12 19:20:03 2020
NAMESPACE: prometheus
STATUS: DEPLOYED

RESOURCES:
```

```console
==> v1/Alertmanager
NAME                                     AGE
prometheus-prometheus-oper-alertmanager  37s
```

```console
==> v1/ClusterRole
NAME                                       CREATED AT
prometheus-grafana-clusterrole             2020-08-13T02:21:09Z
prometheus-prometheus-oper-operator        2020-08-13T02:21:09Z
prometheus-prometheus-oper-operator-psp    2020-08-13T02:21:09Z
prometheus-prometheus-oper-prometheus      2020-08-13T02:21:09Z
prometheus-prometheus-oper-prometheus-psp  2020-08-13T02:21:09Z
psp-prometheus-kube-state-metrics          2020-08-13T02:21:09Z
psp-prometheus-prometheus-node-exporter    2020-08-13T02:21:09Z
```

```console
==> v1/ClusterRoleBinding
NAME                                       ROLE                                                   AGE
prometheus-grafana-clusterrolebinding      ClusterRole/prometheus-grafana-clusterrole             37s
prometheus-prometheus-oper-operator        ClusterRole/prometheus-prometheus-oper-operator        37s
prometheus-prometheus-oper-operator-psp    ClusterRole/prometheus-prometheus-oper-operator-psp    37s
prometheus-prometheus-oper-prometheus      ClusterRole/prometheus-prometheus-oper-prometheus      37s
prometheus-prometheus-oper-prometheus-psp  ClusterRole/prometheus-prometheus-oper-prometheus-psp  37s
psp-prometheus-kube-state-metrics          ClusterRole/psp-prometheus-kube-state-metrics          37s
psp-prometheus-prometheus-node-exporter    ClusterRole/psp-prometheus-prometheus-node-exporter    37s
```

```console
==> v1/ConfigMap
NAME                                                          DATA  AGE
prometheus-grafana                                            1     36s
prometheus-grafana-config-dashboards                          1     36s
prometheus-grafana-test                                       1     36s
prometheus-prometheus-oper-apiserver                          1     36s
prometheus-prometheus-oper-cluster-total                      1     36s
prometheus-prometheus-oper-controller-manager                 1     36s
prometheus-prometheus-oper-etcd                               1     36s
prometheus-prometheus-oper-grafana-datasource                 1     36s
prometheus-prometheus-oper-k8s-coredns                        1     36s
prometheus-prometheus-oper-k8s-resources-cluster              1     36s
prometheus-prometheus-oper-k8s-resources-namespace            1     36s
prometheus-prometheus-oper-k8s-resources-node                 1     36s
prometheus-prometheus-oper-k8s-resources-pod                  1     36s
prometheus-prometheus-oper-k8s-resources-workload             1     36s
prometheus-prometheus-oper-k8s-resources-workloads-namespace  1     36s
prometheus-prometheus-oper-kubelet                            1     36s
prometheus-prometheus-oper-namespace-by-pod                   1     37s
prometheus-prometheus-oper-namespace-by-workload              1     37s
prometheus-prometheus-oper-node-cluster-rsrc-use              1     37s
prometheus-prometheus-oper-node-rsrc-use                      1     37s
prometheus-prometheus-oper-nodes                              1     37s
prometheus-prometheus-oper-persistentvolumesusage             1     37s
prometheus-prometheus-oper-pod-total                          1     37s
prometheus-prometheus-oper-pods                               1     37s
prometheus-prometheus-oper-prometheus                         1     37s
prometheus-prometheus-oper-proxy                              1     37s
prometheus-prometheus-oper-scheduler                          1     37s
prometheus-prometheus-oper-statefulset                        1     37s
prometheus-prometheus-oper-workload-total                     1     36s
```

```console
==> v1/DaemonSet
NAME                                 DESIRED  CURRENT  READY  UP-TO-DATE  AVAILABLE  NODE SELECTOR  AGE
prometheus-prometheus-node-exporter  6        6        6      6           6          <none>         37s
```

```console
==> v1/Deployment
NAME                                 READY  UP-TO-DATE  AVAILABLE  AGE
prometheus-grafana                   1/1    1           1          37s
prometheus-kube-state-metrics        1/1    1           1          37s
prometheus-prometheus-oper-operator  1/1    1           1          37s
```

```console
==> v1/Pod(related)
NAME                                                  READY  STATUS   RESTARTS  AGE
prometheus-grafana-86c695c58f-cgq5v                   2/2    Running  0         38s
prometheus-kube-state-metrics-7b69c4fc7-8pmg2         1/1    Running  0         38s
prometheus-prometheus-node-exporter-2lj2g             1/1    Running  0         38s
prometheus-prometheus-node-exporter-6d5rx             1/1    Running  0         38s
prometheus-prometheus-node-exporter-7mq8w             1/1    Running  0         38s
prometheus-prometheus-node-exporter-8qvxm             1/1    Running  0         38s
prometheus-prometheus-node-exporter-gwc62             1/1    Running  0         38s
prometheus-prometheus-node-exporter-rn7k5             1/1    Running  0         38s
prometheus-prometheus-oper-operator-666b58fc6c-9n6ln  2/2    Running  0         38s
```

```console
==> v1/Prometheus
NAME                                   AGE
prometheus-prometheus-oper-prometheus  37s
```

```console
==> v1/PrometheusRule
NAME                                                             AGE
prometheus-prometheus-oper-alertmanager.rules                    36s
prometheus-prometheus-oper-etcd                                  36s
prometheus-prometheus-oper-general.rules                         36s
prometheus-prometheus-oper-k8s.rules                             36s
prometheus-prometheus-oper-kube-apiserver-error                  36s
prometheus-prometheus-oper-kube-apiserver.rules                  36s
prometheus-prometheus-oper-kube-prometheus-node-recording.rules  36s
prometheus-prometheus-oper-kube-scheduler.rules                  36s
prometheus-prometheus-oper-kubernetes-absent                     36s
prometheus-prometheus-oper-kubernetes-apps                       36s
prometheus-prometheus-oper-kubernetes-resources                  36s
prometheus-prometheus-oper-kubernetes-storage                    36s
prometheus-prometheus-oper-kubernetes-system                     36s
prometheus-prometheus-oper-kubernetes-system-apiserver           36s
prometheus-prometheus-oper-kubernetes-system-controller-manager  36s
prometheus-prometheus-oper-kubernetes-system-kubelet             36s
prometheus-prometheus-oper-kubernetes-system-scheduler           36s
prometheus-prometheus-oper-node-exporter                         36s
prometheus-prometheus-oper-node-exporter.rules                   36s
prometheus-prometheus-oper-node-network                          36s
prometheus-prometheus-oper-node-time                             36s
prometheus-prometheus-oper-node.rules                            36s
prometheus-prometheus-oper-prometheus                            36s
prometheus-prometheus-oper-prometheus-operator                   36s
```

```console
==> v1/Role
NAME                                     CREATED AT
prometheus-grafana-test                  2020-08-13T02:21:09Z
prometheus-prometheus-oper-alertmanager  2020-08-13T02:21:09Z
```

```console
==> v1/RoleBinding
NAME                                     ROLE                                          AGE
prometheus-grafana-test                  Role/prometheus-grafana-test                  37s
prometheus-prometheus-oper-alertmanager  Role/prometheus-prometheus-oper-alertmanager  37s
```

```console
==> v1/Secret
NAME                                                  TYPE    DATA  AGE
alertmanager-prometheus-prometheus-oper-alertmanager  Opaque  1     36s
prometheus-grafana                                    Opaque  3     36s
```

```console
==> v1/Service
NAME                                                TYPE       CLUSTER-IP      EXTERNAL-IP  PORT(S)           AGE
prometheus-grafana                                  ClusterIP  100.64.109.252  <none>       80/TCP            37s
prometheus-kube-state-metrics                       ClusterIP  100.64.44.24    <none>       8080/TCP          37s
prometheus-prometheus-node-exporter                 ClusterIP  100.67.252.203  <none>       9100/TCP          37s
prometheus-prometheus-oper-alertmanager             ClusterIP  100.69.182.61   <none>       9093/TCP          37s
prometheus-prometheus-oper-coredns                  ClusterIP  None            <none>       9153/TCP          37s
prometheus-prometheus-oper-kube-controller-manager  ClusterIP  None            <none>       10252/TCP         37s
prometheus-prometheus-oper-kube-etcd                ClusterIP  None            <none>       2379/TCP          37s
prometheus-prometheus-oper-kube-proxy               ClusterIP  None            <none>       10249/TCP         37s
prometheus-prometheus-oper-kube-scheduler           ClusterIP  None            <none>       10251/TCP         37s
prometheus-prometheus-oper-operator                 ClusterIP  100.65.247.213  <none>       8080/TCP,443/TCP  37s
prometheus-prometheus-oper-prometheus               ClusterIP  100.67.39.105   <none>       9090/TCP          37s
```

```console
==> v1/ServiceAccount
NAME                                     SECRETS  AGE
prometheus-grafana                       1        37s
prometheus-grafana-test                  1        37s
prometheus-kube-state-metrics            1        37s
prometheus-prometheus-node-exporter      1        37s
prometheus-prometheus-oper-alertmanager  1        37s
prometheus-prometheus-oper-operator      1        37s
prometheus-prometheus-oper-prometheus    1        37s
```

```console
==> v1/ServiceMonitor
NAME                                                AGE
prometheus-prometheus-oper-alertmanager             36s
prometheus-prometheus-oper-apiserver                36s
prometheus-prometheus-oper-coredns                  36s
prometheus-prometheus-oper-grafana                  36s
prometheus-prometheus-oper-kube-controller-manager  36s
prometheus-prometheus-oper-kube-etcd                36s
prometheus-prometheus-oper-kube-proxy               36s
prometheus-prometheus-oper-kube-scheduler           36s
prometheus-prometheus-oper-kube-state-metrics       36s
prometheus-prometheus-oper-kubelet                  36s
prometheus-prometheus-oper-node-exporter            36s
prometheus-prometheus-oper-operator                 36s
prometheus-prometheus-oper-prometheus               36s
```

```console
==> v1beta1/ClusterRole
NAME                           CREATED AT
prometheus-kube-state-metrics  2020-08-13T02:21:09Z
```

```console
==> v1beta1/ClusterRoleBinding
NAME                           ROLE                                       AGE
prometheus-kube-state-metrics  ClusterRole/prometheus-kube-state-metrics  37s
```

```console
==> v1beta1/MutatingWebhookConfiguration
NAME                                  WEBHOOKS  AGE
prometheus-prometheus-oper-admission  1         37s
```

```console
==> v1beta1/PodSecurityPolicy
NAME                                     PRIV   CAPS      SELINUX           RUNASUSER  FSGROUP    SUPGROUP  READONLYROOTFS  VOLUMES
prometheus-grafana                       false  RunAsAny  RunAsAny          RunAsAny   RunAsAny   false     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim
prometheus-grafana-test                  false  RunAsAny  RunAsAny          RunAsAny   RunAsAny   false     configMap,downwardAPI,emptyDir,projected,secret
prometheus-kube-state-metrics            false  RunAsAny  MustRunAsNonRoot  MustRunAs  MustRunAs  false     secret
prometheus-prometheus-node-exporter      false  RunAsAny  RunAsAny          MustRunAs  MustRunAs  false     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim,hostPath
prometheus-prometheus-oper-alertmanager  false  RunAsAny  RunAsAny          MustRunAs  MustRunAs  false     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim
prometheus-prometheus-oper-operator      false  RunAsAny  RunAsAny          MustRunAs  MustRunAs  false     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim
prometheus-prometheus-oper-prometheus    false  RunAsAny  RunAsAny          MustRunAs  MustRunAs  false     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim
```

```console
==> v1beta1/Role
NAME                CREATED AT
prometheus-grafana  2020-08-13T02:21:09Z
```

```console
==> v1beta1/RoleBinding
NAME                ROLE                     AGE
prometheus-grafana  Role/prometheus-grafana  37s
```

```console
==> v1beta1/ValidatingWebhookConfiguration
NAME                                  WEBHOOKS  AGE
prometheus-prometheus-oper-admission  1         36s
```

```console
NOTES:
The Prometheus Operator has been installed. Check its status by running:
  kubectl --namespace prometheus get pods -l "release=prometheus"

Visit https://github.com/coreos/prometheus-operator for instructions on how
to create & configure Alertmanager and Prometheus instances using the Operator.
```

```console
NAME                                                   READY   STATUS    RESTARTS   AGE
prometheus-grafana-86c695c58f-cgq5v                    2/2     Running   0          2m40s
prometheus-prometheus-node-exporter-2lj2g              1/1     Running   0          2m40s
prometheus-prometheus-node-exporter-6d5rx              1/1     Running   0          2m40s
prometheus-prometheus-node-exporter-7mq8w              1/1     Running   0          2m40s
prometheus-prometheus-node-exporter-8qvxm              1/1     Running   0          2m40s
prometheus-prometheus-node-exporter-gwc62              1/1     Running   0          2m40s
prometheus-prometheus-node-exporter-rn7k5              1/1     Running   0          2m40s
prometheus-prometheus-oper-operator-666b58fc6c-9n6ln   2/2     Running   0          2m40s
```

```json
{
    "apiVersion": "v1",
    "items": [
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2020-08-13T02:21:16Z",
                "labels": {
                    "operated-alertmanager": "true"
                },
                "managedFields": [
                    {
                        "apiVersion": "v1",
                        "fieldsType": "FieldsV1",
                        "fieldsV1": {
                            "f:metadata": {
                                "f:labels": {
                                    ".": {},
                                    "f:operated-alertmanager": {}
                                },
                                "f:ownerReferences": {
                                    ".": {},
                                    "k:{\"uid\":\"291993ac-09b8-45d3-8997-a2bc641c7c55\"}": {
                                        ".": {},
                                        "f:apiVersion": {},
                                        "f:kind": {},
                                        "f:name": {},
                                        "f:uid": {}
                                    }
                                }
                            },
                            "f:spec": {
                                "f:clusterIP": {},
                                "f:ports": {
                                    ".": {},
                                    "k:{\"port\":9093,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    },
                                    "k:{\"port\":9094,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    },
                                    "k:{\"port\":9094,\"protocol\":\"UDP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    }
                                },
                                "f:selector": {
                                    ".": {},
                                    "f:app": {}
                                },
                                "f:sessionAffinity": {},
                                "f:type": {}
                            }
                        },
                        "manager": "operator",
                        "operation": "Update",
                        "time": "2020-08-13T02:21:16Z"
                    }
                ],
                "name": "alertmanager-operated",
                "namespace": "prometheus",
                "ownerReferences": [
                    {
                        "apiVersion": "monitoring.coreos.com/v1",
                        "kind": "Alertmanager",
                        "name": "prometheus-prometheus-oper-alertmanager",
                        "uid": "291993ac-09b8-45d3-8997-a2bc641c7c55"
                    }
                ],
                "resourceVersion": "4543",
                "selfLink": "/api/v1/namespaces/prometheus/services/alertmanager-operated",
                "uid": "ee96ca24-b8c6-4d51-ae3b-88ba3c4c2582"
            },
            "spec": {
                "clusterIP": "None",
                "ports": [
                    {
                        "name": "web",
                        "port": 9093,
                        "protocol": "TCP",
                        "targetPort": 9093
                    },
                    {
                        "name": "mesh-tcp",
                        "port": 9094,
                        "protocol": "TCP",
                        "targetPort": 9094
                    },
                    {
                        "name": "mesh-udp",
                        "port": 9094,
                        "protocol": "UDP",
                        "targetPort": 9094
                    }
                ],
                "selector": {
                    "app": "alertmanager"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2020-08-13T02:21:09Z",
                "labels": {
                    "app": "grafana",
                    "chart": "grafana-4.3.2",
                    "heritage": "Tiller",
                    "release": "prometheus"
                },
                "managedFields": [
                    {
                        "apiVersion": "v1",
                        "fieldsType": "FieldsV1",
                        "fieldsV1": {
                            "f:metadata": {
                                "f:labels": {
                                    ".": {},
                                    "f:app": {},
                                    "f:chart": {},
                                    "f:heritage": {},
                                    "f:release": {}
                                }
                            },
                            "f:spec": {
                                "f:ports": {
                                    ".": {},
                                    "k:{\"port\":80,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    }
                                },
                                "f:selector": {
                                    ".": {},
                                    "f:app": {},
                                    "f:release": {}
                                },
                                "f:sessionAffinity": {},
                                "f:type": {}
                            }
                        },
                        "manager": "Go-http-client",
                        "operation": "Update",
                        "time": "2020-08-13T02:21:09Z"
                    }
                ],
                "name": "prometheus-grafana",
                "namespace": "prometheus",
                "resourceVersion": "4372",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-grafana",
                "uid": "7c8018d4-14ca-4d7f-8c83-e0797542b84f"
            },
            "spec": {
                "clusterIP": "100.64.109.252",
                "ports": [
                    {
                        "name": "service",
                        "port": 80,
                        "protocol": "TCP",
                        "targetPort": 3000
                    }
                ],
                "selector": {
                    "app": "grafana",
                    "release": "prometheus"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "annotations": {
                    "prometheus.io/scrape": "true"
                },
                "creationTimestamp": "2020-08-13T02:21:09Z",
                "labels": {
                    "app.kubernetes.io/instance": "prometheus",
                    "app.kubernetes.io/managed-by": "Tiller",
                    "app.kubernetes.io/name": "kube-state-metrics",
                    "helm.sh/chart": "kube-state-metrics-2.6.2"
                },
                "managedFields": [
                    {
                        "apiVersion": "v1",
                        "fieldsType": "FieldsV1",
                        "fieldsV1": {
                            "f:metadata": {
                                "f:annotations": {
                                    ".": {},
                                    "f:prometheus.io/scrape": {}
                                },
                                "f:labels": {
                                    ".": {},
                                    "f:app.kubernetes.io/instance": {},
                                    "f:app.kubernetes.io/managed-by": {},
                                    "f:app.kubernetes.io/name": {},
                                    "f:helm.sh/chart": {}
                                }
                            },
                            "f:spec": {
                                "f:ports": {
                                    ".": {},
                                    "k:{\"port\":8080,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    }
                                },
                                "f:selector": {
                                    ".": {},
                                    "f:app.kubernetes.io/instance": {},
                                    "f:app.kubernetes.io/name": {}
                                },
                                "f:sessionAffinity": {},
                                "f:type": {}
                            }
                        },
                        "manager": "Go-http-client",
                        "operation": "Update",
                        "time": "2020-08-13T02:21:09Z"
                    }
                ],
                "name": "prometheus-kube-state-metrics",
                "namespace": "prometheus",
                "resourceVersion": "4375",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-kube-state-metrics",
                "uid": "78d8c21d-9273-43bf-b8cc-8b2bdec621f6"
            },
            "spec": {
                "clusterIP": "100.64.44.24",
                "ports": [
                    {
                        "name": "http",
                        "port": 8080,
                        "protocol": "TCP",
                        "targetPort": 8080
                    }
                ],
                "selector": {
                    "app.kubernetes.io/instance": "prometheus",
                    "app.kubernetes.io/name": "kube-state-metrics"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2020-08-13T02:21:27Z",
                "labels": {
                    "operated-prometheus": "true"
                },
                "managedFields": [
                    {
                        "apiVersion": "v1",
                        "fieldsType": "FieldsV1",
                        "fieldsV1": {
                            "f:metadata": {
                                "f:labels": {
                                    ".": {},
                                    "f:operated-prometheus": {}
                                },
                                "f:ownerReferences": {
                                    ".": {},
                                    "k:{\"uid\":\"30fc7599-c07d-44ee-951f-aedf692c191a\"}": {
                                        ".": {},
                                        "f:apiVersion": {},
                                        "f:kind": {},
                                        "f:name": {},
                                        "f:uid": {}
                                    }
                                }
                            },
                            "f:spec": {
                                "f:clusterIP": {},
                                "f:ports": {
                                    ".": {},
                                    "k:{\"port\":9090,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    }
                                },
                                "f:selector": {
                                    ".": {},
                                    "f:app": {}
                                },
                                "f:sessionAffinity": {},
                                "f:type": {}
                            }
                        },
                        "manager": "operator",
                        "operation": "Update",
                        "time": "2020-08-13T02:21:27Z"
                    }
                ],
                "name": "prometheus-operated",
                "namespace": "prometheus",
                "ownerReferences": [
                    {
                        "apiVersion": "monitoring.coreos.com/v1",
                        "kind": "Prometheus",
                        "name": "prometheus-prometheus-oper-prometheus",
                        "uid": "30fc7599-c07d-44ee-951f-aedf692c191a"
                    }
                ],
                "resourceVersion": "4658",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-operated",
                "uid": "849e38f8-e8ee-48fd-b06a-897a5dd53bc8"
            },
            "spec": {
                "clusterIP": "None",
                "ports": [
                    {
                        "name": "web",
                        "port": 9090,
                        "protocol": "TCP",
                        "targetPort": "web"
                    }
                ],
                "selector": {
                    "app": "prometheus"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "annotations": {
                    "prometheus.io/scrape": "true"
                },
                "creationTimestamp": "2020-08-13T02:21:09Z",
                "labels": {
                    "app": "prometheus-node-exporter",
                    "chart": "prometheus-node-exporter-1.8.1",
                    "heritage": "Tiller",
                    "jobLabel": "node-exporter",
                    "release": "prometheus"
                },
                "managedFields": [
                    {
                        "apiVersion": "v1",
                        "fieldsType": "FieldsV1",
                        "fieldsV1": {
                            "f:metadata": {
                                "f:annotations": {
                                    ".": {},
                                    "f:prometheus.io/scrape": {}
                                },
                                "f:labels": {
                                    ".": {},
                                    "f:app": {},
                                    "f:chart": {},
                                    "f:heritage": {},
                                    "f:jobLabel": {},
                                    "f:release": {}
                                }
                            },
                            "f:spec": {
                                "f:ports": {
                                    ".": {},
                                    "k:{\"port\":9100,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    }
                                },
                                "f:selector": {
                                    ".": {},
                                    "f:app": {},
                                    "f:release": {}
                                },
                                "f:sessionAffinity": {},
                                "f:type": {}
                            }
                        },
                        "manager": "Go-http-client",
                        "operation": "Update",
                        "time": "2020-08-13T02:21:09Z"
                    }
                ],
                "name": "prometheus-prometheus-node-exporter",
                "namespace": "prometheus",
                "resourceVersion": "4382",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-prometheus-node-exporter",
                "uid": "eba10fe5-8e70-420b-aefa-86f95dd32372"
            },
            "spec": {
                "clusterIP": "100.67.252.203",
                "ports": [
                    {
                        "name": "metrics",
                        "port": 9100,
                        "protocol": "TCP",
                        "targetPort": 9100
                    }
                ],
                "selector": {
                    "app": "prometheus-node-exporter",
                    "release": "prometheus"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2020-08-13T02:21:09Z",
                "labels": {
                    "app": "prometheus-operator-alertmanager",
                    "chart": "prometheus-operator-8.5.14",
                    "heritage": "Tiller",
                    "release": "prometheus"
                },
                "managedFields": [
                    {
                        "apiVersion": "v1",
                        "fieldsType": "FieldsV1",
                        "fieldsV1": {
                            "f:metadata": {
                                "f:labels": {
                                    ".": {},
                                    "f:app": {},
                                    "f:chart": {},
                                    "f:heritage": {},
                                    "f:release": {}
                                }
                            },
                            "f:spec": {
                                "f:ports": {
                                    ".": {},
                                    "k:{\"port\":9093,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    }
                                },
                                "f:selector": {
                                    ".": {},
                                    "f:alertmanager": {},
                                    "f:app": {}
                                },
                                "f:sessionAffinity": {},
                                "f:type": {}
                            }
                        },
                        "manager": "Go-http-client",
                        "operation": "Update",
                        "time": "2020-08-13T02:21:09Z"
                    }
                ],
                "name": "prometheus-prometheus-oper-alertmanager",
                "namespace": "prometheus",
                "resourceVersion": "4386",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-prometheus-oper-alertmanager",
                "uid": "7ec3c530-108b-41af-9287-7eb418aeb00f"
            },
            "spec": {
                "clusterIP": "100.69.182.61",
                "ports": [
                    {
                        "name": "web",
                        "port": 9093,
                        "protocol": "TCP",
                        "targetPort": 9093
                    }
                ],
                "selector": {
                    "alertmanager": "prometheus-prometheus-oper-alertmanager",
                    "app": "alertmanager"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2020-08-13T02:21:09Z",
                "labels": {
                    "app": "prometheus-operator-operator",
                    "chart": "prometheus-operator-8.5.14",
                    "heritage": "Tiller",
                    "release": "prometheus"
                },
                "managedFields": [
                    {
                        "apiVersion": "v1",
                        "fieldsType": "FieldsV1",
                        "fieldsV1": {
                            "f:metadata": {
                                "f:labels": {
                                    ".": {},
                                    "f:app": {},
                                    "f:chart": {},
                                    "f:heritage": {},
                                    "f:release": {}
                                }
                            },
                            "f:spec": {
                                "f:ports": {
                                    ".": {},
                                    "k:{\"port\":443,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    },
                                    "k:{\"port\":8080,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    }
                                },
                                "f:selector": {
                                    ".": {},
                                    "f:app": {},
                                    "f:release": {}
                                },
                                "f:sessionAffinity": {},
                                "f:type": {}
                            }
                        },
                        "manager": "Go-http-client",
                        "operation": "Update",
                        "time": "2020-08-13T02:21:09Z"
                    }
                ],
                "name": "prometheus-prometheus-oper-operator",
                "namespace": "prometheus",
                "resourceVersion": "4391",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-prometheus-oper-operator",
                "uid": "29a229fa-d0a7-4226-a5ad-b02944e436db"
            },
            "spec": {
                "clusterIP": "100.65.247.213",
                "ports": [
                    {
                        "name": "http",
                        "port": 8080,
                        "protocol": "TCP",
                        "targetPort": "http"
                    },
                    {
                        "name": "https",
                        "port": 443,
                        "protocol": "TCP",
                        "targetPort": "https"
                    }
                ],
                "selector": {
                    "app": "prometheus-operator-operator",
                    "release": "prometheus"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2020-08-13T02:21:09Z",
                "labels": {
                    "app": "prometheus-operator-prometheus",
                    "chart": "prometheus-operator-8.5.14",
                    "heritage": "Tiller",
                    "release": "prometheus",
                    "self-monitor": "true"
                },
                "managedFields": [
                    {
                        "apiVersion": "v1",
                        "fieldsType": "FieldsV1",
                        "fieldsV1": {
                            "f:metadata": {
                                "f:labels": {
                                    ".": {},
                                    "f:app": {},
                                    "f:chart": {},
                                    "f:heritage": {},
                                    "f:release": {},
                                    "f:self-monitor": {}
                                }
                            },
                            "f:spec": {
                                "f:ports": {
                                    ".": {},
                                    "k:{\"port\":9090,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:name": {},
                                        "f:port": {},
                                        "f:protocol": {},
                                        "f:targetPort": {}
                                    }
                                },
                                "f:selector": {
                                    ".": {},
                                    "f:app": {},
                                    "f:prometheus": {}
                                },
                                "f:sessionAffinity": {},
                                "f:type": {}
                            }
                        },
                        "manager": "Go-http-client",
                        "operation": "Update",
                        "time": "2020-08-13T02:21:09Z"
                    }
                ],
                "name": "prometheus-prometheus-oper-prometheus",
                "namespace": "prometheus",
                "resourceVersion": "4365",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-prometheus-oper-prometheus",
                "uid": "c37b947c-b35d-4c8b-8d2a-fa6662b5be72"
            },
            "spec": {
                "clusterIP": "100.67.39.105",
                "ports": [
                    {
                        "name": "web",
                        "port": 9090,
                        "protocol": "TCP",
                        "targetPort": 9090
                    }
                ],
                "selector": {
                    "app": "prometheus",
                    "prometheus": "prometheus-prometheus-oper-prometheus"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        }
    ],
    "kind": "List",
    "metadata": {
        "resourceVersion": "",
        "selfLink": ""
    }
}
```

```console
NAME                                                     READY   STATUS    RESTARTS   AGE     IP               NODE                             NOMINATED NODE   READINESS GATES
prometheus-prometheus-node-exporter-8qvxm                1/1     Running   0          2m42s   172.20.60.215    ip-172-20-60-215.ec2.internal    <none>           <none>
prometheus-grafana-86c695c58f-cgq5v                      2/2     Running   0          2m42s   100.116.0.4      ip-172-20-63-5.ec2.internal      <none>           <none>
prometheus-kube-state-metrics-7b69c4fc7-8pmg2            1/1     Running   0          2m42s   100.116.0.5      ip-172-20-63-5.ec2.internal      <none>           <none>
prometheus-prometheus-node-exporter-2lj2g                1/1     Running   0          2m42s   172.20.63.5      ip-172-20-63-5.ec2.internal      <none>           <none>
prometheus-prometheus-prometheus-oper-prometheus-0       3/3     Running   1          2m24s   100.116.0.7      ip-172-20-63-5.ec2.internal      <none>           <none>
alertmanager-prometheus-prometheus-oper-alertmanager-0   2/2     Running   0          2m34s   100.100.0.5      ip-172-20-80-214.ec2.internal    <none>           <none>
prometheus-prometheus-node-exporter-gwc62                1/1     Running   0          2m42s   172.20.80.214    ip-172-20-80-214.ec2.internal    <none>           <none>
prometheus-prometheus-oper-operator-666b58fc6c-9n6ln     2/2     Running   0          2m42s   100.100.0.4      ip-172-20-80-214.ec2.internal    <none>           <none>
prometheus-prometheus-node-exporter-rn7k5                1/1     Running   0          2m42s   172.20.82.200    ip-172-20-82-200.ec2.internal    <none>           <none>
prometheus-prometheus-node-exporter-6d5rx                1/1     Running   0          2m42s   172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
prometheus-prometheus-node-exporter-7mq8w                1/1     Running   0          2m42s   172.20.120.109   ip-172-20-120-109.ec2.internal   <none>           <none>
```

```console
Creating Kubernetes Dashboard ...

secret/kubernetes-dashboard-certs created
serviceaccount/kubernetes-dashboard created
role.rbac.authorization.k8s.io/kubernetes-dashboard-minimal created
rolebinding.rbac.authorization.k8s.io/kubernetes-dashboard-minimal created
deployment.apps/kubernetes-dashboard created
service/kubernetes-dashboard created
```

```console
Generating console-user and credentials ...

serviceaccount/admin-user created
clusterrolebinding.rbac.authorization.k8s.io/admin-user created
```

```console
Displaying console-user configuration ...

Name:         admin-user-token-l5chq
Namespace:    kube-system
Labels:       <none>
Annotations:  kubernetes.io/service-account.name: admin-user
              kubernetes.io/service-account.uid: 2b23211d-cbb0-4d83-9c68-bf3c8ec708b7

Type:  kubernetes.io/service-account-token
```

```console
Data
====
ca.crt:     1042 bytes
namespace:  11 bytes
token:      eyJhbGciOiJSUzI1NiIsImtpZCI6IjhwT1JlZEVvY29tV25JNW9GeEwzeWR0WV9Tby1hdE1zc19Va3FXamVFdUkifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJrdWJlLXN5c3RlbSIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VjcmV0Lm5hbWUiOiJhZG1pbi11c2VyLXRva2VuLWw1Y2hxIiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZXJ2aWNlLWFjY291bnQubmFtZSI6ImFkbWluLXVzZXIiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiIyYjIzMjExZC1jYmIwLTRkODMtOWM2OC1iZjNjOGVjNzA4YjciLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6a3ViZS1zeXN0ZW06YWRtaW4tdXNlciJ9.ssFUWn6GG1vwd7zHrLOBpK3sJ8lAfQ6oXU5ryR1cgC9TPT4eaAN4iIQVzZommHMhTfpCd1kfv9JACFKja9UbXTq5kTBsX72agjb5AKp5uPvXeMnB1vot9aN7XtuSNMSrYzjBMeAycKGmd2BLYM3gXu12OyW_-3mV5IU790SLuRih0mOBQVgHesmLU6z4fSALYpxhM_LlByN2M3h9WCAWswHDzhs2H3wIIUvpS13LgLVYNrqHKOY16go4qRgpSFMwxP_oe3CgsTd7CMD8fWUZCNR5eB5_FDfLSBw-tPTgjgj4wk1YvUCIjQDes0s5nfO3_xSGEP5NBEIVo13X5PYssA
```

```console
Dashboard Console-Admin = https://api.prototype.emvaldes.name

Dashboard User-Credentials:
Dashboard Web-Console = https://api.prototype.emvaldes.name/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/login
```

```console
Console User-Token:
eyJhbGciOiJSUzI1NiIsImtpZCI6IjhwT1JlZEVvY29tV25JNW9GeEwzeWR0WV9Tby1hdE1zc19Va3FXamVFdUkifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJrdWJlLXN5c3RlbSIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VjcmV0Lm5hbWUiOiJhZG1pbi11c2VyLXRva2VuLWw1Y2hxIiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZXJ2aWNlLWFjY291bnQubmFtZSI6ImFkbWluLXVzZXIiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiIyYjIzMjExZC1jYmIwLTRkODMtOWM2OC1iZjNjOGVjNzA4YjciLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6a3ViZS1zeXN0ZW06YWRtaW4tdXNlciJ9.ssFUWn6GG1vwd7zHrLOBpK3sJ8lAfQ6oXU5ryR1cgC9TPT4eaAN4iIQVzZommHMhTfpCd1kfv9JACFKja9UbXTq5kTBsX72agjb5AKp5uPvXeMnB1vot9aN7XtuSNMSrYzjBMeAycKGmd2BLYM3gXu12OyW_-3mV5IU790SLuRih0mOBQVgHesmLU6z4fSALYpxhM_LlByN2M3h9WCAWswHDzhs2H3wIIUvpS13LgLVYNrqHKOY16go4qRgpSFMwxP_oe3CgsTd7CMD8fWUZCNR5eB5_FDfLSBw-tPTgjgj4wk1YvUCIjQDes0s5nfO3_xSGEP5NBEIVo13X5PYssA
```

```console
Generating Application Container (Pod: helloworld) ...
Creating AWS ECR 'helloworld' ...
```

```json
{
    "repository": {
        "repositoryArn": "arn:aws:ecr:us-east-1:123456789012:repository/helloworld",
        "registryId": "123456789012",
        "repositoryName": "helloworld",
        "repositoryUri": "123456789012.dkr.ecr.us-east-1.amazonaws.com/helloworld",
        "createdAt": "2020-08-12T19:24:04-07:00",
        "imageTagMutability": "MUTABLE",
        "imageScanningConfiguration": {
            "scanOnPush": false
        }
    }
}
```

```console
Login Succeeded
/Users/emvaldes/etc/configs/docker/Dockerfile -> /tmp/clusters/k8s-cluster/docker/emvaldes.name/prototype/Dockerfile
```

```console
REPOSITORY                           TAG                                              IMAGE ID            CREATED             SIZE
ubuntu                               18.04                                            2eb2d388e1a2        2 weeks ago         64.2MB
docker/desktop-storage-provisioner   v1.1                                             e704287ce753        4 months ago        41.8MB
docker/desktop-vpnkit-controller     v1.0                                             79da37e5a3aa        5 months ago        36.6MB
docker/desktop-kubernetes            kubernetes-v1.16.5-cni-v0.7.5-critools-v1.15.0   a86647f0b376        6 months ago        279MB
k8s.gcr.io/kube-controller-manager   v1.16.5                                          441835dd2301        7 months ago        151MB
k8s.gcr.io/kube-apiserver            v1.16.5                                          fc838b21afbb        7 months ago        159MB
k8s.gcr.io/kube-scheduler            v1.16.5                                          b4d073a9efda        7 months ago        83.5MB
k8s.gcr.io/kube-proxy                v1.16.5                                          0ee1b8a3ebe0        7 months ago        82.7MB
docker/kube-compose-controller       v0.4.25-alpha1                                   129151cdf35f        9 months ago        35.6MB
docker/kube-compose-api-server       v0.4.25-alpha1                                   989749268895        9 months ago        50.7MB
docker/kube-compose-installer        v0.4.25-alpha1                                   2a71ac5a1359        9 months ago        42.3MB
k8s.gcr.io/etcd                      3.3.15-0                                         b2756210eeab        11 months ago       247MB
k8s.gcr.io/coredns                   1.6.2                                            bf261d157914        12 months ago       44.1MB
k8s.gcr.io/pause                     3.1                                              da86e6ba6ca1        2 years ago         742kB
```

```console
Sending build context to Docker daemon   2.56kB
Step 1/11 : FROM ubuntu:18.04
 ---> 2eb2d388e1a2
Step 2/11 : ARG TERM=xterm
 ---> Running in 7781dd1776a4
Removing intermediate container 7781dd1776a4
 ---> f53baad7ecb9
Step 3/11 : ARG LC_ALL=C.UTF-8
 ---> Running in 78d7b6e85bf4
Removing intermediate container 78d7b6e85bf4
 ---> 1d231df0a783
Step 4/11 : ARG DEBIAN_FRONTEND=noninteractive
 ---> Running in e831bfb357a2
Removing intermediate container e831bfb357a2
 ---> 0e7cc1b135df
Step 5/11 : RUN apt-get update -y &&     apt-get install -y --no-install-recommends apt-utils
 ---> Running in 4c18a639d592
Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
...
Get:18 http://archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [8432 B]
Fetched 18.3 MB in 4s (4509 kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
The following additional packages will be installed:
  libapt-inst2.0
The following NEW packages will be installed:
  apt-utils libapt-inst2.0
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 261 kB of archives.
After this operation, 1271 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libapt-inst2.0 amd64 1.6.12ubuntu0.1 [54.4 kB]
Get:2 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 apt-utils amd64 1.6.12ubuntu0.1 [207 kB]
debconf: delaying package configuration, since apt-utils is not installed
Fetched 261 kB in 1s (239 kB/s)
Selecting previously unselected package libapt-inst2.0:amd64.
(Reading database ... 4046 files and directories currently installed.)
Preparing to unpack .../libapt-inst2.0_1.6.12ubuntu0.1_amd64.deb ...
Unpacking libapt-inst2.0:amd64 (1.6.12ubuntu0.1) ...
Selecting previously unselected package apt-utils.
Preparing to unpack .../apt-utils_1.6.12ubuntu0.1_amd64.deb ...
Unpacking apt-utils (1.6.12ubuntu0.1) ...
Setting up libapt-inst2.0:amd64 (1.6.12ubuntu0.1) ...
Setting up apt-utils (1.6.12ubuntu0.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1.2) ...
Removing intermediate container 4c18a639d592
 ---> bc5e39c08469
Step 6/11 : RUN apt-get update -y &&     apt-get upgrade -y &&     apt-get install -y lsb-release
 ---> Running in 010c2cb88887
Hit:1 http://security.ubuntu.com/ubuntu bionic-security InRelease
...
Hit:4 http://archive.ubuntu.com/ubuntu bionic-backports InRelease
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
Calculating upgrade...
The following packages will be upgraded:
  base-files libseccomp2 libsystemd0 libudev1
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 367 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 base-files amd64 10.1ubuntu2.9 [59.9 kB]
...
Get:4 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libseccomp2 amd64 2.4.3-1ubuntu3.18.04.3 [42.0 kB]
Fetched 367 kB in 1s (308 kB/s)
(Reading database ... 4133 files and directories currently installed.)
Preparing to unpack .../base-files_10.1ubuntu2.9_amd64.deb ...
Unpacking base-files (10.1ubuntu2.9) over (10.1ubuntu2.8) ...
Setting up base-files (10.1ubuntu2.9) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
(Reading database ... 4133 files and directories currently installed.)
Preparing to unpack .../libsystemd0_237-3ubuntu10.42_amd64.deb ...
Unpacking libsystemd0:amd64 (237-3ubuntu10.42) over (237-3ubuntu10.41) ...
...
Setting up libseccomp2:amd64 (2.4.3-1ubuntu3.18.04.3) ...
Processing triggers for libc-bin (2.27-3ubuntu1.2) ...
Reading package lists...
Building dependency tree...
Reading state information...
The following additional packages will be installed:
...
Suggested packages:
...
The following NEW packages will be installed:
...
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 6680 kB of archives.
After this operation, 34.1 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libssl1.1 amd64 1.1.1-1ubuntu2.1~18.04.6 [1301 kB]
...
Get:20 http://archive.ubuntu.com/ubuntu bionic/main amd64 xz-utils amd64 5.2.2-1.3 [83.8 kB]
Preconfiguring packages ...
Fetched 6680 kB in 2s (3013 kB/s)
Selecting previously unselected package libssl1.1:amd64.
(Reading database ... 4133 files and directories currently installed.)
Preparing to unpack .../libssl1.1_1.1.1-1ubuntu2.1~18.04.6_amd64.deb ...
Unpacking libssl1.1:amd64 (1.1.1-1ubuntu2.1~18.04.6) ...
...
Selecting previously unselected package python3.6-minimal.
Preparing to unpack .../python3.6-minimal_3.6.9-1~18.04ubuntu1.1_amd64.deb ...
Unpacking python3.6-minimal (3.6.9-1~18.04ubuntu1.1) ...
Setting up libssl1.1:amd64 (1.1.1-1ubuntu2.1~18.04.6) ...
Setting up libpython3.6-minimal:amd64 (3.6.9-1~18.04ubuntu1.1) ...
Setting up libexpat1:amd64 (2.2.5-3ubuntu0.2) ...
Setting up python3.6-minimal (3.6.9-1~18.04ubuntu1.1) ...
Selecting previously unselected package python3-minimal.
(Reading database ... 4390 files and directories currently installed.)
Preparing to unpack .../0-python3-minimal_3.6.7-1~18.04_amd64.deb ...
Unpacking python3-minimal (3.6.7-1~18.04) ...
...
Selecting previously unselected package libpython3-stdlib:amd64.
Preparing to unpack .../8-libpython3-stdlib_3.6.7-1~18.04_amd64.deb ...
Unpacking libpython3-stdlib:amd64 (3.6.7-1~18.04) ...
Setting up python3-minimal (3.6.7-1~18.04) ...
Selecting previously unselected package python3.
(Reading database ... 4848 files and directories currently installed.)
Preparing to unpack .../0-python3_3.6.7-1~18.04_amd64.deb ...
Unpacking python3 (3.6.7-1~18.04) ...
...
Selecting previously unselected package xz-utils.
Preparing to unpack .../6-xz-utils_5.2.2-1.3_amd64.deb ...
Unpacking xz-utils (5.2.2-1.3) ...
Setting up readline-common (7.0-3) ...
...
Setting up xz-utils (5.2.2-1.3) ...
update-alternatives: using /usr/bin/xz to provide /usr/bin/lzma (lzma) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/man1/lzma.1.gz because associated file /usr/share/man/man1/xz.1.gz (of link group lzma) doesn't exist
...
update-alternatives: warning: skip creation of /usr/share/man/man1/lzfgrep.1.gz because associated file /usr/share/man/man1/xzfgrep.1.gz (of link group lzma) doesn't exist
Setting up libsqlite3-0:amd64 (3.22.0-1ubuntu0.4) ...
...
Setting up lsb-release (9.20170808ubuntu1) ...
Processing triggers for libc-bin (2.27-3ubuntu1.2) ...
Removing intermediate container 010c2cb88887
 ---> 63866437c3fb
Step 7/11 : RUN apt-get -y install apache2
 ---> Running in 0f3961baafe1
Reading package lists...
Building dependency tree...
Reading state information...
The following additional packages will be installed:
...
Suggested packages:
...
The following NEW packages will be installed:
...
0 upgraded, 34 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.8 MB of archives.
After this operation, 87.9 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 perl-modules-5.26 all 5.26.1-6ubuntu0.3 [2763 kB]
...
Get:34 http://archive.ubuntu.com/ubuntu bionic/main amd64 ssl-cert all 1.0.39 [17.0 kB]
Preconfiguring packages ...
Fetched 18.8 MB in 3s (5610 kB/s)
Selecting previously unselected package perl-modules-5.26.
(Reading database ... 4972 files and directories currently installed.)
Preparing to unpack .../00-perl-modules-5.26_5.26.1-6ubuntu0.3_all.deb ...
Unpacking perl-modules-5.26 (5.26.1-6ubuntu0.3) ...
...
Selecting previously unselected package ssl-cert.
Preparing to unpack .../33-ssl-cert_1.0.39_all.deb ...
Unpacking ssl-cert (1.0.39) ...
Setting up libapr1:amd64 (1.6.3-2) ...
...
Setting up apache2 (2.4.29-1ubuntu4.13) ...
Enabling module mpm_event.
...
Enabling site 000-default.
invoke-rc.d: could not determine current runlevel
invoke-rc.d: policy-rc.d denied execution of start.
Processing triggers for libc-bin (2.27-3ubuntu1.2) ...
Removing intermediate container 0f3961baafe1
 ---> acb5de25ba5f
Step 8/11 : RUN echo 'Hello DevOps Engineers! (latest: 00000000000000)' > /var/www/html/index.html
 ---> Running in 74cd32d18e59
Removing intermediate container 74cd32d18e59
 ---> f909aa6e670f
Step 9/11 : RUN echo '. /etc/apache2/envvars' > /root/run_apache.sh &&  echo 'mkdir -p /var/run/apache2' >> /root/run_apache.sh &&  echo 'mkdir -p /var/lock/apache2' >> /root/run_apache.sh &&  echo '/usr/sbin/apache2 -D FOREGROUND' >> /root/run_apache.sh &&  chmod 755 /root/run_apache.sh
 ---> Running in e14ed34eea39
Removing intermediate container e14ed34eea39
 ---> d209cafe5871
Step 10/11 : EXPOSE 80
 ---> Running in 1f25713773e2
Removing intermediate container 1f25713773e2
 ---> 1576c1f4cac5
Step 11/11 : CMD /root/run_apache.sh
 ---> Running in d0468ba0ef7f
Removing intermediate container d0468ba0ef7f
 ---> aacf034e8115
Successfully built aacf034e8115
Successfully tagged helloworld:prototype.emvaldes.name
```

```console
REPOSITORY                           TAG                                              IMAGE ID            CREATED                  SIZE
helloworld                           prototype.emvaldes.name                          aacf034e8115        Less than a second ago   218MB
ubuntu                               18.04                                            2eb2d388e1a2        2 weeks ago              64.2MB
docker/desktop-storage-provisioner   v1.1                                             e704287ce753        4 months ago             41.8MB
docker/desktop-vpnkit-controller     v1.0                                             79da37e5a3aa        5 months ago             36.6MB
docker/desktop-kubernetes            kubernetes-v1.16.5-cni-v0.7.5-critools-v1.15.0   a86647f0b376        6 months ago             279MB
k8s.gcr.io/kube-proxy                v1.16.5                                          0ee1b8a3ebe0        7 months ago             82.7MB
k8s.gcr.io/kube-scheduler            v1.16.5                                          b4d073a9efda        7 months ago             83.5MB
k8s.gcr.io/kube-apiserver            v1.16.5                                          fc838b21afbb        7 months ago             159MB
k8s.gcr.io/kube-controller-manager   v1.16.5                                          441835dd2301        7 months ago             151MB
docker/kube-compose-controller       v0.4.25-alpha1                                   129151cdf35f        9 months ago             35.6MB
docker/kube-compose-api-server       v0.4.25-alpha1                                   989749268895        9 months ago             50.7MB
docker/kube-compose-installer        v0.4.25-alpha1                                   2a71ac5a1359        9 months ago             42.3MB
k8s.gcr.io/etcd                      3.3.15-0                                         b2756210eeab        11 months ago            247MB
k8s.gcr.io/coredns                   1.6.2                                            bf261d157914        12 months ago            44.1MB
k8s.gcr.io/pause                     3.1                                              da86e6ba6ca1        2 years ago              742kB
```

```console
REPOSITORY                                                TAG                                              IMAGE ID            CREATED                  SIZE
123456789012.dkr.ecr.us-east-1.amazonaws.com/helloworld   prototype.emvaldes.name                          aacf034e8115        Less than a second ago   218MB
helloworld                                                prototype.emvaldes.name                          aacf034e8115        Less than a second ago   218MB
ubuntu                                                    18.04                                            2eb2d388e1a2        2 weeks ago              64.2MB
docker/desktop-storage-provisioner                        v1.1                                             e704287ce753        4 months ago             41.8MB
docker/desktop-vpnkit-controller                          v1.0                                             79da37e5a3aa        5 months ago             36.6MB
docker/desktop-kubernetes                                 kubernetes-v1.16.5-cni-v0.7.5-critools-v1.15.0   a86647f0b376        6 months ago             279MB
k8s.gcr.io/kube-controller-manager                        v1.16.5                                          441835dd2301        7 months ago             151MB
k8s.gcr.io/kube-proxy                                     v1.16.5                                          0ee1b8a3ebe0        7 months ago             82.7MB
k8s.gcr.io/kube-apiserver                                 v1.16.5                                          fc838b21afbb        7 months ago             159MB
k8s.gcr.io/kube-scheduler                                 v1.16.5                                          b4d073a9efda        7 months ago             83.5MB
docker/kube-compose-controller                            v0.4.25-alpha1                                   129151cdf35f        9 months ago             35.6MB
docker/kube-compose-api-server                            v0.4.25-alpha1                                   989749268895        9 months ago             50.7MB
docker/kube-compose-installer                             v0.4.25-alpha1                                   2a71ac5a1359        9 months ago             42.3MB
k8s.gcr.io/etcd                                           3.3.15-0                                         b2756210eeab        11 months ago            247MB
k8s.gcr.io/coredns                                        1.6.2                                            bf261d157914        12 months ago            44.1MB
k8s.gcr.io/pause                                          3.1                                              da86e6ba6ca1        2 years ago              742kB
```

```console
Published: 0
Modifying Prototype [helloworld:prototype.emvaldes.name] ...
```

```console
REPOSITORY                                                TAG                                              IMAGE ID            CREATED             SIZE
123456789012.dkr.ecr.us-east-1.amazonaws.com/helloworld   prototype.emvaldes.name                          aacf034e8115        1 second ago        218MB
helloworld                                                prototype.emvaldes.name                          aacf034e8115        1 second ago        218MB
ubuntu                                                    18.04                                            2eb2d388e1a2        2 weeks ago         64.2MB
docker/desktop-storage-provisioner                        v1.1                                             e704287ce753        4 months ago        41.8MB
docker/desktop-vpnkit-controller                          v1.0                                             79da37e5a3aa        5 months ago        36.6MB
docker/desktop-kubernetes                                 kubernetes-v1.16.5-cni-v0.7.5-critools-v1.15.0   a86647f0b376        6 months ago        279MB
k8s.gcr.io/kube-apiserver                                 v1.16.5                                          fc838b21afbb        7 months ago        159MB
k8s.gcr.io/kube-scheduler                                 v1.16.5                                          b4d073a9efda        7 months ago        83.5MB
k8s.gcr.io/kube-proxy                                     v1.16.5                                          0ee1b8a3ebe0        7 months ago        82.7MB
k8s.gcr.io/kube-controller-manager                        v1.16.5                                          441835dd2301        7 months ago        151MB
docker/kube-compose-controller                            v0.4.25-alpha1                                   129151cdf35f        9 months ago        35.6MB
docker/kube-compose-api-server                            v0.4.25-alpha1                                   989749268895        9 months ago        50.7MB
docker/kube-compose-installer                             v0.4.25-alpha1                                   2a71ac5a1359        9 months ago        42.3MB
k8s.gcr.io/etcd                                           3.3.15-0                                         b2756210eeab        11 months ago       247MB
k8s.gcr.io/coredns                                        1.6.2                                            bf261d157914        12 months ago       44.1MB
k8s.gcr.io/pause                                          3.1                                              da86e6ba6ca1        2 years ago         742kB
Sending build context to Docker daemon   2.56kB
```

```console
Step 1/11 : FROM ubuntu:18.04
 ---> 2eb2d388e1a2
Step 2/11 : ARG TERM=xterm
 ---> Using cache
 ---> f53baad7ecb9
Step 3/11 : ARG LC_ALL=C.UTF-8
 ---> Using cache
 ---> 1d231df0a783
Step 4/11 : ARG DEBIAN_FRONTEND=noninteractive
 ---> Using cache
 ---> 0e7cc1b135df
Step 5/11 : RUN apt-get update -y &&     apt-get install -y --no-install-recommends apt-utils
 ---> Using cache
 ---> bc5e39c08469
Step 6/11 : RUN apt-get update -y &&     apt-get upgrade -y &&     apt-get install -y lsb-release
 ---> Using cache
 ---> 63866437c3fb
Step 7/11 : RUN apt-get -y install apache2
 ---> Using cache
 ---> acb5de25ba5f
Step 8/11 : RUN echo 'Hello DevOps Engineers! (k8s-cluster.prototype.emvaldes.name: 20200812192444)' > /var/www/html/index.html
 ---> Running in 646b80bc07e6
Removing intermediate container 646b80bc07e6
 ---> e3e7624384e5
Step 9/11 : RUN echo '. /etc/apache2/envvars' > /root/run_apache.sh &&  echo 'mkdir -p /var/run/apache2' >> /root/run_apache.sh &&  echo 'mkdir -p /var/lock/apache2' >> /root/run_apache.sh &&  echo '/usr/sbin/apache2 -D FOREGROUND' >> /root/run_apache.sh &&  chmod 755 /root/run_apache.sh
 ---> Running in 3d88f7b6e415
Removing intermediate container 3d88f7b6e415
 ---> d7ab8beb4f0d
Step 10/11 : EXPOSE 80
 ---> Running in 21349c8e835b
Removing intermediate container 21349c8e835b
 ---> 8f97cdfc0f54
Step 11/11 : CMD /root/run_apache.sh
 ---> Running in 36fdfe047add
Removing intermediate container 36fdfe047add
 ---> bf3f83c5c5d1
Successfully built bf3f83c5c5d1
Successfully tagged helloworld:prototype.emvaldes.name
```

```console
REPOSITORY                                                TAG                                              IMAGE ID            CREATED                  SIZE
helloworld                                                prototype.emvaldes.name                          bf3f83c5c5d1        Less than a second ago   218MB
123456789012.dkr.ecr.us-east-1.amazonaws.com/helloworld   prototype.emvaldes.name                          aacf034e8115        3 seconds ago            218MB
ubuntu                                                    18.04                                            2eb2d388e1a2        2 weeks ago              64.2MB
docker/desktop-storage-provisioner                        v1.1                                             e704287ce753        4 months ago             41.8MB
docker/desktop-vpnkit-controller                          v1.0                                             79da37e5a3aa        5 months ago             36.6MB
docker/desktop-kubernetes                                 kubernetes-v1.16.5-cni-v0.7.5-critools-v1.15.0   a86647f0b376        6 months ago             279MB
k8s.gcr.io/kube-scheduler                                 v1.16.5                                          b4d073a9efda        7 months ago             83.5MB
k8s.gcr.io/kube-proxy                                     v1.16.5                                          0ee1b8a3ebe0        7 months ago             82.7MB
k8s.gcr.io/kube-apiserver                                 v1.16.5                                          fc838b21afbb        7 months ago             159MB
k8s.gcr.io/kube-controller-manager                        v1.16.5                                          441835dd2301        7 months ago             151MB
docker/kube-compose-controller                            v0.4.25-alpha1                                   129151cdf35f        9 months ago             35.6MB
docker/kube-compose-api-server                            v0.4.25-alpha1                                   989749268895        9 months ago             50.7MB
docker/kube-compose-installer                             v0.4.25-alpha1                                   2a71ac5a1359        9 months ago             42.3MB
k8s.gcr.io/etcd                                           3.3.15-0                                         b2756210eeab        11 months ago            247MB
k8s.gcr.io/coredns                                        1.6.2                                            bf261d157914        12 months ago            44.1MB
k8s.gcr.io/pause                                          3.1                                              da86e6ba6ca1        2 years ago              742kB
```

```console
REPOSITORY                                                TAG                                              IMAGE ID            CREATED                  SIZE
123456789012.dkr.ecr.us-east-1.amazonaws.com/helloworld   prototype.emvaldes.name                          bf3f83c5c5d1        Less than a second ago   218MB
helloworld                                                prototype.emvaldes.name                          bf3f83c5c5d1        Less than a second ago   218MB
<none>                                                    <none>                                           aacf034e8115        3 seconds ago            218MB
ubuntu                                                    18.04                                            2eb2d388e1a2        2 weeks ago              64.2MB
docker/desktop-storage-provisioner                        v1.1                                             e704287ce753        4 months ago             41.8MB
docker/desktop-vpnkit-controller                          v1.0                                             79da37e5a3aa        5 months ago             36.6MB
docker/desktop-kubernetes                                 kubernetes-v1.16.5-cni-v0.7.5-critools-v1.15.0   a86647f0b376        6 months ago             279MB
k8s.gcr.io/kube-proxy                                     v1.16.5                                          0ee1b8a3ebe0        7 months ago             82.7MB
k8s.gcr.io/kube-apiserver                                 v1.16.5                                          fc838b21afbb        7 months ago             159MB
k8s.gcr.io/kube-controller-manager                        v1.16.5                                          441835dd2301        7 months ago             151MB
k8s.gcr.io/kube-scheduler                                 v1.16.5                                          b4d073a9efda        7 months ago             83.5MB
docker/kube-compose-controller                            v0.4.25-alpha1                                   129151cdf35f        9 months ago             35.6MB
docker/kube-compose-api-server                            v0.4.25-alpha1                                   989749268895        9 months ago             50.7MB
docker/kube-compose-installer                             v0.4.25-alpha1                                   2a71ac5a1359        9 months ago             42.3MB
k8s.gcr.io/etcd                                           3.3.15-0                                         b2756210eeab        11 months ago            247MB
k8s.gcr.io/coredns                                        1.6.2                                            bf261d157914        12 months ago            44.1MB
k8s.gcr.io/pause                                          3.1                                              da86e6ba6ca1        2 years ago              742kB
```

```console
The push refers to repository [123456789012.dkr.ecr.us-east-1.amazonaws.com/helloworld]
90d124b4c856: Pushed
34343a6d4193: Pushed
c89e6d9881ec: Pushed
34e14cf4e4d1: Pushed
034122565f67: Pushed
8682f9a74649: Pushed
d3a6da143c91: Pushed
83f4287e1f04: Pushed
7ef368776582: Pushed
prototype.emvaldes.name: digest: sha256:4959ab26e5c17760f7398bdb0f073d81a67c39057a140f7d454756aa2437f7f5 size: 2202
Pushed: 0
```

```json
{
    "repositories": [
        {
            "repositoryArn": "arn:aws:ecr:us-east-1:123456789012:repository/helloworld",
            "registryId": "123456789012",
            "repositoryName": "helloworld",
            "repositoryUri": "123456789012.dkr.ecr.us-east-1.amazonaws.com/helloworld",
            "createdAt": "2020-08-12T19:24:04-07:00",
            "imageTagMutability": "MUTABLE",
            "imageScanningConfiguration": {
                "scanOnPush": false
            }
        }
    ]
}
```

```console
HTTP/1.1 200 OK
Content-Type: text/plain; charset=utf-8
Date: Thu, 13 Aug 2020 02:25:31 GMT
Docker-Distribution-Api-Version: registry/2.0
Content-Length: 56
Connection: keep-alive
```

```json
{"name":"helloworld","tags":["prototype.emvaldes.name"]}
```

```yaml
apiVersion:              apps/v1
kind:                    Deployment
metadata:
  name:                  helloworld-deployment
spec:
  replicas:              3
  revisionHistoryLimit:  100
  selector:
    matchLabels:
      app:               helloworld
  template:
    metadata:
      labels:
        app:             helloworld
    spec:
      containers:
      - name:            helloworld
        image:           123456789012.dkr.ecr.us-east-1.amazonaws.com/helloworld:prototype.emvaldes.name
        ports:
        - name:          http-port
          containerPort: 80
```

```console
deployment.apps/helloworld-deployment created

Exposing Deployment Object (Load-Balancer) ...
service/helloworld-deployment exposed
```

```console
Listing Replication Sets:

NAME                               DESIRED   CURRENT   READY   AGE
helloworld-deployment-5889c975c4   3         3         0       2s
```

```console
Listing Deployment Objects [default]:

NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
helloworld-deployment   0/3     3            0           4s
Cluster Deployment: helloworld-deployment-5889c975c4-m8sln
```

```console
Describing Deployment: helloworld-deployment-5889c975c4-m8sln
```

```yaml
Name:           helloworld-deployment-5889c975c4-m8sln
Namespace:      default
Priority:       0
Node:           ip-172-20-120-109.ec2.internal/172.20.120.109
Start Time:     Wed, 12 Aug 2020 19:25:32 -0700
Labels:         app=helloworld
                pod-template-hash=5889c975c4
Annotations:    kubernetes.io/limit-ranger: LimitRanger plugin set: cpu request for container helloworld
Status:         Pending
IP:
IPs:            <none>
Controlled By:  ReplicaSet/helloworld-deployment-5889c975c4
Containers:
  helloworld:
    Container ID:
    Image:          123456789012.dkr.ecr.us-east-1.amazonaws.com/helloworld:prototype.emvaldes.name
    Image ID:
    Port:           80/TCP
    Host Port:      0/TCP
    State:          Waiting
      Reason:       ContainerCreating
    Ready:          False
    Restart Count:  0
    Requests:
      cpu:        100m
    Environment:  <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-5l94q (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             False
  ContainersReady   False
  PodScheduled      True
Volumes:
  default-token-5l94q:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-5l94q
    Optional:    false
QoS Class:       Burstable
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:
  Type    Reason     Age   From                                     Message
  ----    ------     ----  ----                                     -------
  Normal  Scheduled  6s    default-scheduler                        Successfully assigned default/helloworld-deployment-5889c975c4-m8sln to ip-172-20-120-109.ec2.internal
  Normal  Pulling    5s    kubelet, ip-172-20-120-109.ec2.internal  Pulling image "123456789012.dkr.ecr.us-east-1.amazonaws.com/helloworld:prototype.emvaldes.name"
Countdown: 5

Displaying Deployment's Log: helloworld-deployment-5889c975c4-m8sln
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 100.124.0.6. Set the 'ServerName' directive globally to suppress this message
```

```console
deployment "helloworld-deployment" successfully rolled out
deployment.apps/helloworld-deployment
```

```console
REVISION  CHANGE-CAUSE
1         kubectl create --filename=/tmp/clusters/k8s-apps/helloworld/prototype.emvaldes.name.yaml --record=true
```

```console
NAME                                     READY   STATUS    RESTARTS   AGE
helloworld-deployment-5889c975c4-m8sln   1/1     Running   0          26s
helloworld-deployment-5889c975c4-pqvr9   1/1     Running   0          26s
helloworld-deployment-5889c975c4-s6fqf   1/1     Running   0          26s
```

```console
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"><html><head><meta http-equiv="refresh" content="0;url=http://finder.cox.net/main?ParticipantID=96e687opkbv4scrood8k84drs6gw5duf&FailedURI=http%3A%2F%2Faa6f6bfc7a61044fe9b2fc05f2d81c21-576572754.us-east-1.elb.amazonaws.com%2F&FailureMode=1&Implementation=&AddInType=4&Version=pywr1.0&ClientLocation=us"/><script type="text/javascript">url="http://finder.cox.net/main?ParticipantID=96e687opkbv4scrood8k84drs6gw5duf&FailedURI=http%3A%2F%2Faa6f6bfc7a61044fe9b2fc05f2d81c21-576572754.us-east-1.elb.amazonaws.com%2F&FailureMode=1&Implementation=&AddInType=4&Version=pywr1.0&ClientLocation=us";if(top.location!=location){var w=window,d=document,e=d.documentElement,b=d.body,x=w.innerWidth||e.clientWidth||b.clientWidth,y=w.innerHeight||e.clientHeight||b.clientHeight;url+="&w="+x+"&h="+y;}window.location.replace(url);</script></head><body></body></html>
```

```console
Configuring Cluster Context (prototype.emvaldes.name) ...
Switched to context "prototype.emvaldes.name".
```

```console
Listing Cluster Contexts ...

CURRENT   NAME                      CLUSTER                   AUTHINFO                  NAMESPACE
*         prototype.emvaldes.name   prototype.emvaldes.name   prototype.emvaldes.name
```

```console
Listing Infrastructure Clusters ...

NAME
prototype.emvaldes.name
```

```console
Listing Kubernetes Configuration ...
```

```yaml
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: DATA+OMITTED
    server: https://api.prototype.emvaldes.name
  name: prototype.emvaldes.name
contexts:
- context:
    cluster: prototype.emvaldes.name
    user: prototype.emvaldes.name
  name: prototype.emvaldes.name
current-context: prototype.emvaldes.name
kind: Config
preferences: {}
users:
- name: prototype.emvaldes.name
  user:
    client-certificate-data: REDACTED
    client-key-data: REDACTED
```

```console
Validating Kubernetes Cluster: prototype.emvaldes.name ...

I0812 19:26:17.885151    6293 featureflag.go:154] FeatureFlag "SpecOverrideFlag"=true
Validating cluster prototype.emvaldes.name
```

```console
INSTANCE GROUPS
NAME			ROLE	MACHINETYPE	MIN	MAX	SUBNETS
master-us-east-1a	Master	t3a.xlarge	1	1	us-east-1a
master-us-east-1b	Master	t3a.xlarge	1	1	us-east-1b
master-us-east-1c	Master	t3a.xlarge	1	1	us-east-1c
nodes			Node	t3a.large	3	3	us-east-1a,us-east-1b,us-east-1c
```

```console
NODE STATUS
NAME				ROLE	READY
ip-172-20-110-228.ec2.internal	master	True
ip-172-20-120-109.ec2.internal	node	True
ip-172-20-60-215.ec2.internal	master	True
ip-172-20-63-5.ec2.internal	node	True
ip-172-20-80-214.ec2.internal	node	True
ip-172-20-82-200.ec2.internal	master	True
```

```console
Your cluster prototype.emvaldes.name is ready
```

```console
Listing Deployment Objects [everything]:

NAMESPACE     NAME                                  READY   UP-TO-DATE   AVAILABLE   AGE
default       helloworld-deployment                 3/3     3            3           51s
kube-system   dns-controller                        1/1     1            1           21m
kube-system   kube-dns                              2/2     2            2           21m
kube-system   kube-dns-autoscaler                   1/1     1            1           21m
kube-system   kubernetes-dashboard                  1/1     1            1           2m29s
kube-system   metrics-server                        1/1     1            1           8m1s
kube-system   tiller-deploy                         1/1     1            1           7m25s
prometheus    prometheus-grafana                    1/1     1            1           5m14s
prometheus    prometheus-kube-state-metrics         1/1     1            1           5m14s
prometheus    prometheus-prometheus-oper-operator   1/1     1            1           5m14s
```

```console
NAME                                   SERVICE                      AVAILABLE   AGE
v1.                                    Local                        True        22m
v1.admissionregistration.k8s.io        Local                        True        22m
v1.apiextensions.k8s.io                Local                        True        22m
v1.apps                                Local                        True        22m
v1.authentication.k8s.io               Local                        True        22m
v1.authorization.k8s.io                Local                        True        22m
v1.autoscaling                         Local                        True        22m
v1.batch                               Local                        True        22m
v1.coordination.k8s.io                 Local                        True        22m
v1.monitoring.coreos.com               Local                        True        6m20s
v1.networking.k8s.io                   Local                        True        22m
v1.rbac.authorization.k8s.io           Local                        True        22m
v1.scheduling.k8s.io                   Local                        True        22m
v1.storage.k8s.io                      Local                        True        22m
v1beta1.admissionregistration.k8s.io   Local                        True        22m
v1beta1.apiextensions.k8s.io           Local                        True        22m
v1beta1.authentication.k8s.io          Local                        True        22m
v1beta1.authorization.k8s.io           Local                        True        22m
v1beta1.batch                          Local                        True        22m
v1beta1.certificates.k8s.io            Local                        True        22m
v1beta1.coordination.k8s.io            Local                        True        22m
v1beta1.discovery.k8s.io               Local                        True        22m
v1beta1.events.k8s.io                  Local                        True        22m
v1beta1.extensions                     Local                        True        22m
v1beta1.metrics.k8s.io                 kube-system/metrics-server   True        8m2s
v1beta1.networking.k8s.io              Local                        True        22m
v1beta1.node.k8s.io                    Local                        True        22m
v1beta1.policy                         Local                        True        22m
v1beta1.rbac.authorization.k8s.io      Local                        True        22m
v1beta1.scheduling.k8s.io              Local                        True        22m
v1beta1.storage.k8s.io                 Local                        True        22m
v2beta1.autoscaling                    Local                        True        22m
v2beta2.autoscaling                    Local                        True        22m
```

```console
NAME                                    CREATED AT
alertmanagers.monitoring.coreos.com     2020-08-13T02:20:04Z
podmonitors.monitoring.coreos.com       2020-08-13T02:20:10Z
prometheuses.monitoring.coreos.com      2020-08-13T02:20:17Z
prometheusrules.monitoring.coreos.com   2020-08-13T02:20:23Z
servicemonitors.monitoring.coreos.com   2020-08-13T02:20:29Z
```

```console
NAME                             STATUS   ROLES    AGE   VERSION   INTERNAL-IP      EXTERNAL-IP      OS-IMAGE           KERNEL-VERSION   CONTAINER-RUNTIME
ip-172-20-110-228.ec2.internal   Ready    master   21m   v1.18.6   172.20.110.228   54.90.205.41     Ubuntu 20.04 LTS   5.4.0-1018-aws   docker://19.3.11
ip-172-20-120-109.ec2.internal   Ready    node     21m   v1.18.6   172.20.120.109   54.226.183.194   Ubuntu 20.04 LTS   5.4.0-1018-aws   docker://19.3.11
ip-172-20-60-215.ec2.internal    Ready    master   21m   v1.18.6   172.20.60.215    3.218.150.56     Ubuntu 20.04 LTS   5.4.0-1018-aws   docker://19.3.11
ip-172-20-63-5.ec2.internal      Ready    node     21m   v1.18.6   172.20.63.5      3.237.172.159    Ubuntu 20.04 LTS   5.4.0-1018-aws   docker://19.3.11
ip-172-20-80-214.ec2.internal    Ready    node     21m   v1.18.6   172.20.80.214    3.83.214.2       Ubuntu 20.04 LTS   5.4.0-1018-aws   docker://19.3.11
ip-172-20-82-200.ec2.internal    Ready    master   21m   v1.18.6   172.20.82.200    34.205.156.223   Ubuntu 20.04 LTS   5.4.0-1018-aws   docker://19.3.11
```

```console
Listing Kubernetes Nodes:

NAME                             STATUS   ROLES    AGE   VERSION   LABELS
ip-172-20-110-228.ec2.internal   Ready    master   21m   v1.18.6   beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=t3a.xlarge,beta.kubernetes.io/os=linux,failure-domain.beta.kubernetes.io/region=us-east-1,failure-domain.beta.kubernetes.io/zone=us-east-1c,kops.k8s.io/instancegroup=master-us-east-1c,kubernetes.io/arch=amd64,kubernetes.io/hostname=ip-172-20-110-228.ec2.internal,kubernetes.io/os=linux,kubernetes.io/role=master,node-role.kubernetes.io/master=,node.kubernetes.io/instance-type=t3a.xlarge,topology.kubernetes.io/region=us-east-1,topology.kubernetes.io/zone=us-east-1c
ip-172-20-120-109.ec2.internal   Ready    node     21m   v1.18.6   beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=t3a.large,beta.kubernetes.io/os=linux,failure-domain.beta.kubernetes.io/region=us-east-1,failure-domain.beta.kubernetes.io/zone=us-east-1c,kops.k8s.io/instancegroup=nodes,kubernetes.io/arch=amd64,kubernetes.io/hostname=ip-172-20-120-109.ec2.internal,kubernetes.io/os=linux,kubernetes.io/role=node,node-role.kubernetes.io/node=,node.kubernetes.io/instance-type=t3a.large,topology.kubernetes.io/region=us-east-1,topology.kubernetes.io/zone=us-east-1c
ip-172-20-60-215.ec2.internal    Ready    master   21m   v1.18.6   beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=t3a.xlarge,beta.kubernetes.io/os=linux,failure-domain.beta.kubernetes.io/region=us-east-1,failure-domain.beta.kubernetes.io/zone=us-east-1a,kops.k8s.io/instancegroup=master-us-east-1a,kubernetes.io/arch=amd64,kubernetes.io/hostname=ip-172-20-60-215.ec2.internal,kubernetes.io/os=linux,kubernetes.io/role=master,node-role.kubernetes.io/master=,node.kubernetes.io/instance-type=t3a.xlarge,topology.kubernetes.io/region=us-east-1,topology.kubernetes.io/zone=us-east-1a
ip-172-20-63-5.ec2.internal      Ready    node     21m   v1.18.6   beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=t3a.large,beta.kubernetes.io/os=linux,failure-domain.beta.kubernetes.io/region=us-east-1,failure-domain.beta.kubernetes.io/zone=us-east-1a,kops.k8s.io/instancegroup=nodes,kubernetes.io/arch=amd64,kubernetes.io/hostname=ip-172-20-63-5.ec2.internal,kubernetes.io/os=linux,kubernetes.io/role=node,node-role.kubernetes.io/node=,node.kubernetes.io/instance-type=t3a.large,topology.kubernetes.io/region=us-east-1,topology.kubernetes.io/zone=us-east-1a
ip-172-20-80-214.ec2.internal    Ready    node     21m   v1.18.6   beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=t3a.large,beta.kubernetes.io/os=linux,failure-domain.beta.kubernetes.io/region=us-east-1,failure-domain.beta.kubernetes.io/zone=us-east-1b,kops.k8s.io/instancegroup=nodes,kubernetes.io/arch=amd64,kubernetes.io/hostname=ip-172-20-80-214.ec2.internal,kubernetes.io/os=linux,kubernetes.io/role=node,node-role.kubernetes.io/node=,node.kubernetes.io/instance-type=t3a.large,topology.kubernetes.io/region=us-east-1,topology.kubernetes.io/zone=us-east-1b
ip-172-20-82-200.ec2.internal    Ready    master   21m   v1.18.6   beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=t3a.xlarge,beta.kubernetes.io/os=linux,failure-domain.beta.kubernetes.io/region=us-east-1,failure-domain.beta.kubernetes.io/zone=us-east-1b,kops.k8s.io/instancegroup=master-us-east-1b,kubernetes.io/arch=amd64,kubernetes.io/hostname=ip-172-20-82-200.ec2.internal,kubernetes.io/os=linux,kubernetes.io/role=master,node-role.kubernetes.io/master=,node.kubernetes.io/instance-type=t3a.xlarge,topology.kubernetes.io/region=us-east-1,topology.kubernetes.io/zone=us-east-1b
```

```console
NAME                                     READY   STATUS    RESTARTS   AGE   IP            NODE                             NOMINATED NODE   READINESS GATES
helloworld-deployment-5889c975c4-pqvr9   1/1     Running   0          55s   100.100.0.6   ip-172-20-80-214.ec2.internal    <none>           <none>
helloworld-deployment-5889c975c4-s6fqf   1/1     Running   0          55s   100.100.0.7   ip-172-20-80-214.ec2.internal    <none>           <none>
helloworld-deployment-5889c975c4-m8sln   1/1     Running   0          55s   100.124.0.6   ip-172-20-120-109.ec2.internal   <none>           <none>
```

```console
NAME                                                     READY   STATUS         RESTARTS   AGE     IP               NODE                             NOMINATED NODE   READINESS GATES
etcd-manager-main-ip-172-20-60-215.ec2.internal          1/1     Running        0          20m     172.20.60.215    ip-172-20-60-215.ec2.internal    <none>           <none>
kube-scheduler-ip-172-20-60-215.ec2.internal             1/1     Running        0          21m     172.20.60.215    ip-172-20-60-215.ec2.internal    <none>           <none>
kops-controller-6p8jc                                    1/1     Running        0          20m     172.20.60.215    ip-172-20-60-215.ec2.internal    <none>           <none>
kube-proxy-ip-172-20-60-215.ec2.internal                 1/1     Running        0          20m     172.20.60.215    ip-172-20-60-215.ec2.internal    <none>           <none>
weave-net-lg8zt                                          2/2     Running        0          21m     172.20.60.215    ip-172-20-60-215.ec2.internal    <none>           <none>
kube-controller-manager-ip-172-20-60-215.ec2.internal    1/1     Running        0          21m     172.20.60.215    ip-172-20-60-215.ec2.internal    <none>           <none>
kube-apiserver-ip-172-20-60-215.ec2.internal             2/2     Running        2          20m     172.20.60.215    ip-172-20-60-215.ec2.internal    <none>           <none>
etcd-manager-events-ip-172-20-60-215.ec2.internal        1/1     Running        0          20m     172.20.60.215    ip-172-20-60-215.ec2.internal    <none>           <none>
weave-net-cbg96                                          2/2     Running        1          21m     172.20.63.5      ip-172-20-63-5.ec2.internal      <none>           <none>
kube-proxy-ip-172-20-63-5.ec2.internal                   1/1     Running        0          19m     172.20.63.5      ip-172-20-63-5.ec2.internal      <none>           <none>
tiller-deploy-5c8959c79b-kqqfg                           1/1     Running        0          7m30s   100.116.0.3      ip-172-20-63-5.ec2.internal      <none>           <none>
kube-proxy-ip-172-20-80-214.ec2.internal                 1/1     Running        0          20m     172.20.80.214    ip-172-20-80-214.ec2.internal    <none>           <none>
metrics-server-d5bccf9f7-lpbrx                           1/1     Running        0          8m6s    100.100.0.1      ip-172-20-80-214.ec2.internal    <none>           <none>
weave-net-ngbvx                                          2/2     Running        1          21m     172.20.80.214    ip-172-20-80-214.ec2.internal    <none>           <none>
weave-net-zchvw                                          2/2     Running        4          21m     172.20.82.200    ip-172-20-82-200.ec2.internal    <none>           <none>
etcd-manager-main-ip-172-20-82-200.ec2.internal          1/1     Running        0          20m     172.20.82.200    ip-172-20-82-200.ec2.internal    <none>           <none>
kube-proxy-ip-172-20-82-200.ec2.internal                 1/1     Running        0          21m     172.20.82.200    ip-172-20-82-200.ec2.internal    <none>           <none>
kube-controller-manager-ip-172-20-82-200.ec2.internal    1/1     Running        0          21m     172.20.82.200    ip-172-20-82-200.ec2.internal    <none>           <none>
kubernetes-dashboard-975499656-prnft                     1/1     Running        0          2m34s   100.112.0.1      ip-172-20-82-200.ec2.internal    <none>           <none>
kube-apiserver-ip-172-20-82-200.ec2.internal             2/2     Running        2          21m     172.20.82.200    ip-172-20-82-200.ec2.internal    <none>           <none>
kube-scheduler-ip-172-20-82-200.ec2.internal             1/1     Running        0          21m     172.20.82.200    ip-172-20-82-200.ec2.internal    <none>           <none>
kops-controller-6xkht                                    1/1     Running        0          21m     172.20.82.200    ip-172-20-82-200.ec2.internal    <none>           <none>
etcd-manager-events-ip-172-20-82-200.ec2.internal        1/1     Running        0          21m     172.20.82.200    ip-172-20-82-200.ec2.internal    <none>           <none>
dns-controller-798bf8df89-vd9bf                          0/1     NodeAffinity   0          21m     <none>           ip-172-20-110-228.ec2.internal   <none>           <none>
kube-controller-manager-ip-172-20-110-228.ec2.internal   1/1     Running        0          20m     172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
dns-controller-798bf8df89-ndwxv                          0/1     NodeAffinity   0          21m     <none>           ip-172-20-110-228.ec2.internal   <none>           <none>
kube-proxy-ip-172-20-110-228.ec2.internal                1/1     Running        0          20m     172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
weave-net-9gjhr                                          2/2     Running        0          21m     172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
dns-controller-798bf8df89-hg2pf                          0/1     NodeAffinity   0          21m     <none>           ip-172-20-110-228.ec2.internal   <none>           <none>
dns-controller-798bf8df89-f7446                          0/1     NodeAffinity   0          21m     <none>           ip-172-20-110-228.ec2.internal   <none>           <none>
dns-controller-798bf8df89-w679s                          0/1     NodeAffinity   0          21m     <none>           ip-172-20-110-228.ec2.internal   <none>           <none>
kops-controller-vj2m2                                    1/1     Running        0          21m     172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
kube-scheduler-ip-172-20-110-228.ec2.internal            1/1     Running        0          21m     172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
dns-controller-798bf8df89-5pkch                          1/1     Running        0          21m     172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
etcd-manager-events-ip-172-20-110-228.ec2.internal       1/1     Running        0          20m     172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
dns-controller-798bf8df89-4k8wh                          0/1     NodeAffinity   0          21m     <none>           ip-172-20-110-228.ec2.internal   <none>           <none>
etcd-manager-main-ip-172-20-110-228.ec2.internal         1/1     Running        0          20m     172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
kube-apiserver-ip-172-20-110-228.ec2.internal            2/2     Running        2          21m     172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
dns-controller-798bf8df89-p8bmb                          0/1     NodeAffinity   0          21m     <none>           ip-172-20-110-228.ec2.internal   <none>           <none>
kube-proxy-ip-172-20-120-109.ec2.internal                1/1     Running        0          20m     172.20.120.109   ip-172-20-120-109.ec2.internal   <none>           <none>
kube-dns-autoscaler-cd7778b7b-z8tcd                      1/1     Running        0          21m     100.124.0.2      ip-172-20-120-109.ec2.internal   <none>           <none>
kube-dns-64f86fb8dd-tvx95                                3/3     Running        0          20m     100.124.0.3      ip-172-20-120-109.ec2.internal   <none>           <none>
kube-dns-64f86fb8dd-557ts                                3/3     Running        0          21m     100.124.0.1      ip-172-20-120-109.ec2.internal   <none>           <none>
weave-net-5r5l4                                          2/2     Running        0          21m     172.20.120.109   ip-172-20-120-109.ec2.internal   <none>           <none>
```

```console
NAME                                                     READY   STATUS    RESTARTS   AGE     IP               NODE                             NOMINATED NODE   READINESS GATES
prometheus-prometheus-node-exporter-8qvxm                1/1     Running   0          5m20s   172.20.60.215    ip-172-20-60-215.ec2.internal    <none>           <none>
prometheus-grafana-86c695c58f-cgq5v                      2/2     Running   0          5m20s   100.116.0.4      ip-172-20-63-5.ec2.internal      <none>           <none>
prometheus-kube-state-metrics-7b69c4fc7-8pmg2            1/1     Running   0          5m20s   100.116.0.5      ip-172-20-63-5.ec2.internal      <none>           <none>
prometheus-prometheus-node-exporter-2lj2g                1/1     Running   0          5m20s   172.20.63.5      ip-172-20-63-5.ec2.internal      <none>           <none>
prometheus-prometheus-prometheus-oper-prometheus-0       3/3     Running   1          5m2s    100.116.0.7      ip-172-20-63-5.ec2.internal      <none>           <none>
alertmanager-prometheus-prometheus-oper-alertmanager-0   2/2     Running   0          5m12s   100.100.0.5      ip-172-20-80-214.ec2.internal    <none>           <none>
prometheus-prometheus-node-exporter-gwc62                1/1     Running   0          5m20s   172.20.80.214    ip-172-20-80-214.ec2.internal    <none>           <none>
prometheus-prometheus-oper-operator-666b58fc6c-9n6ln     2/2     Running   0          5m20s   100.100.0.4      ip-172-20-80-214.ec2.internal    <none>           <none>
prometheus-prometheus-node-exporter-rn7k5                1/1     Running   0          5m20s   172.20.82.200    ip-172-20-82-200.ec2.internal    <none>           <none>
prometheus-prometheus-node-exporter-6d5rx                1/1     Running   0          5m20s   172.20.110.228   ip-172-20-110-228.ec2.internal   <none>           <none>
prometheus-prometheus-node-exporter-7mq8w                1/1     Running   0          5m20s   172.20.120.109   ip-172-20-120-109.ec2.internal   <none>           <none>
```

```console
Kubernetes master is running at https://api.prototype.emvaldes.name
KubeDNS is running at https://api.prototype.emvaldes.name/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
Metrics-server is running at https://api.prototype.emvaldes.name/api/v1/namespaces/kube-system/services/https:metrics-server:/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

```console
Identifying Deployment Status ...

deployment "helloworld-deployment" successfully rolled out
deployment.apps/helloworld-deployment
```

```console
REVISION  CHANGE-CAUSE
1         kubectl create --filename=/tmp/clusters/k8s-apps/helloworld/prototype.emvaldes.name.yaml --record=true
```

```console
Listing Kubernetes Services:

NAME                    TYPE           CLUSTER-IP       EXTERNAL-IP                                                              PORT(S)        AGE
helloworld-deployment   LoadBalancer   100.71.101.190   aa6f6bfc7a61044fe9b2fc05f2d81c21-576572754.us-east-1.elb.amazonaws.com   80:30742/TCP   60s
kubernetes              ClusterIP      100.64.0.1       <none>                                                                   443/TCP        22m
```

```console
Scanning Service Ports ...

Starting Nmap 7.80 ( https://nmap.org ) at 2020-08-12 19:26 MST
Nmap scan report for aa6f6bfc7a61044fe9b2fc05f2d81c21-576572754.us-east-1.elb.amazonaws.com (92.242.140.2)
Host is up (0.082s latency).
rDNS record for 92.242.140.2: unallocated.barefruit.co.uk
```

```console
PORT   STATE SERVICE
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 0.50 seconds
```

```console
Retrieving Service Status ...
HTTP/1.1 200 OK
Date: Thu, 13 Aug 2020 02:28:18 GMT
Server: Apache/2.4.29 (Ubuntu)
Last-Modified: Thu, 13 Aug 2020 02:24:46 GMT
ETag: "4e-5acb901ff7780"
Accept-Ranges: bytes
Content-Length: 78
Vary: Accept-Encoding
Content-Type: text/html
```

```console
Displaying Service Content ...

Hello DevOps Engineers! (k8s-cluster.prototype.emvaldes.name: 20200812192444)
```

```console
Describing Application Service ...
```

```yaml
Name:                     helloworld-deployment
Namespace:                default
Labels:                   <none>
Annotations:              <none>
Selector:                 app=helloworld
Type:                     LoadBalancer
IP:                       100.71.101.190
LoadBalancer Ingress:     aa6f6bfc7a61044fe9b2fc05f2d81c21-576572754.us-east-1.elb.amazonaws.com
Port:                     <unset>  80/TCP
TargetPort:               80/TCP
NodePort:                 <unset>  30742/TCP
Endpoints:                100.100.0.6:80,100.100.0.7:80,100.124.0.6:80
Session Affinity:         None
External Traffic Policy:  Cluster
Events:
  Type    Reason                Age    From                Message
  ----    ------                ----   ----                -------
  Normal  EnsuringLoadBalancer  2m47s  service-controller  Ensuring load balancer
  Normal  EnsuredLoadBalancer   2m44s  service-controller  Ensured load balancer

Name:              kubernetes
Namespace:         default
Labels:            component=apiserver
                   provider=kubernetes
Annotations:       <none>
Selector:          <none>
Type:              ClusterIP
IP:                100.64.0.1
Port:              https  443/TCP
TargetPort:        443/TCP
Endpoints:         172.20.110.228:443,172.20.60.215:443,172.20.82.200:443
Session Affinity:  None
Events:            <none>
```
