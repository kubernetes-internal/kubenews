# 004

- Hosted by @bells17
- Recording date: 2020-12-11
- Video:

## Contents

### @chago


### @bells17


### @ryojsb

#### Efficient Multi-Zone Networking with Topology Aware Routing

- kubeweekly(12/12)
- [Google OSS Blog](https://opensource.googleblog.com/2020/11/kubernetes-efficient-multi-zone.html)
- [Service Topology](https://kubernetes.io/docs/concepts/services-networking/service-topology/)
  - [チェシャ猫さん資料](https://speakerdeck.com/ytaka23/jaws-container-sig-16th)

Topology Aware Routing of Services： `topologyKeys`を用いてトラフィックを細かく分割する方法
  
- Kubernetes v1.17 alpha機能
- TopologyKeyにおいて、Nodeのlabelを設定することで、上から書かれている順番に応じて、優先的に指定Labelを持つNode上で動くPodに通信が流れるように設定できる。
  - 例えばマルチAZ構成において、クライアントと同一ノードまたは同一AZのようなネットワーク的に近いエンドポイントにトラフィックが優先的にルーティングされるように指定できる。
- 1Serviceに複数Endpointがひも付く構成になる。

以下のマニフェストでは、
1. `kubernetes.io/hostname`より、同一Node
2. `topology.kubernetes.io/zone`より、同一Zone
3. `topology.kubernetes.io/region`より、同一region
4. `*`より、その他全て

```
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 9376
  topologyKeys:
    - "kubernetes.io/hostname"
    - "topology.kubernetes.io/zone"
    - "topology.kubernetes.io/region"
    - "*"
```

#### OPA The Easy Way
- kubeweekly(12/12)
- [InflaCloud Blog](https://www.infracloud.io/blogs/opa-the-easy-way-featuring-styra-das/)
- [How to Use a Policy Engine to Improve Your Security Posture](https://nirmata.com/2020/12/05/how-to-use-a-policy-engine-to-improve-your-security-posture/)
  - [Presentation in Kubernetes Novice Tokyo by ry](https://speakerdeck.com/ry/policy-managershi-sitemita)
  - [Validation with kyverno](https://ryo-xjsbx.hatenablog.com/entry/kyverno)

#### Automating Volume Expansion Management
- kubeweekly(12/12)
- [Redhut Openshift blog](https://www.openshift.com/blog/automating-volume-expansion-management-an-operator-based-approach)

