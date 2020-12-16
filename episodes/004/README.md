# 004

- Hosted by @bells17
- Recording date: 2020-12-11
- Video:
- Guest: @inductor

## Contents

### @chago


### @bells17

#### [Amazon Managed Service for Prometheus features](https://aws.amazon.com/jp/grafana/)

- https://techfeed.io/comments/5fd978d220b65e5c6b97c5d5
- Grafanaのマネージドサービスも合わせて出ているよう
  - https://techfeed.io/comments/5fd9798320b65e5c6b97c5f1

#### [ローカルマシンでDocker を動かさないためにBlimp を採用する](https://y-ohgi.blog/entry/2020/12/15/%E3%83%AD%E3%83%BC%E3%82%AB%E3%83%AB%E3%83%9E%E3%82%B7%E3%83%B3%E3%81%A7Docker_%E3%82%92%E5%8B%95%E3%81%8B%E3%81%95%E3%81%AA%E3%81%84%E3%81%9F%E3%82%81%E3%81%ABBlimp_%E3%82%92%E6%8E%A1%E7%94%A8%E3%81%99%E3%82%8B)

### @ryojsb

#### Efficient Multi-Zone Networking with Topology Aware Routing

- kubeweekly(12/12)
- [Google OSS Blog](https://opensource.googleblog.com/2020/11/kubernetes-efficient-multi-zone.html)
- [Service Topology](https://kubernetes.io/docs/concepts/services-networking/service-topology/)
  - [チェシャ猫さん資料](https://speakerdeck.com/ytaka23/jaws-container-sig-16th)

Topology Aware Routing of Services： `topologyKeys`を用いてトラフィックを細かく分割する方法
  
- Kubernetes v1.17 alpha機能であり、影響範囲はPod-Pod間の通信
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
- [volume-expander-operator](https://github.com/redhat-cop/volume-expander-operator)

Persistent Volumeを用いる際は、PrometheusにこのAlertを入れたほうがいい。

```
    - alert: "Storage Saturation"
      labels:
        severity: critical
      annotations:
        summary: Storage usage over 75%
        persistentvolumeclaim: 
        namespace: 
      expr: kubelet_volume_stats_used_bytes / kubelet_volume_stats_capacity_bytes > 0.75
      for: 1m
 ```

という前置きの元、PVの拡張を自動化するソリューションとして、volume-expander-operatorに関する紹介が始まる。

- 監視したいPVCのannotationに`volume-expander-operator.redhat-cop.io/autoexpand: “true”`を設定が必要。
  - Once enabled, the volume-expander-operator will start polling the platform Prometheus instance that is part of OpenShift Monitoringとあり、OpenShift
- `kubelet_volume_stats_used_bytes`と`kubelet_volume_stats_capacity_bytes`の2つのメトリックより判断。
- その他設定するannotaionは以下
  - volume-expander-operator.redhat-c​​op.io/expand-threshold-percent: ボリュームの拡張をトリガーする閾値
  - volume-expander-operator.redhat-c​​op.io/expand-by-percent: 拡張される既存ボリュームのサイズに基づくパーセンテージ
  - volume-expander-operator.redhat-c​​op.io/expand-up-to: ボリュームの上限
  - volume-expander-operator.redhat-c​​op.io/polling-frequency：　ポーリングする頻度

参考manifest

```
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  annotations:
    volume-expander-operator.redhat-cop.io/autoexpand: 'true'
    volume-expander-operator.redhat-cop.io/expand-threshold-percent: "85"
    volume-expander-operator.redhat-cop.io/expand-by-percent: "20"
    volume-expander-operator.redhat-cop.io/polling-frequency: "1m"
    volume-expander-operator.redhat-cop.io/expand-up-to: "20Gi"
  name: to-be-expanded
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: "1Gi"
```

