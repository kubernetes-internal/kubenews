# 004

- Hosted by @bells17
- Recording date: 2020-12-11
- Video:
- Guest: @inductor

## Contents

### @chago

#### [Integrating Kubebuilder and Operator SDK](https://github.com/kubernetes-sigs/kubebuilder/blob/master/designs/integrating-kubebuilder-and-osdk.md)

- https://twitter.com/y_taka_23/status/1339484757155987456
- https://twitter.com/ttsubo/status/1339527347616157696?s=20


### @bells17

#### [Amazon Managed Service for Prometheus features](https://aws.amazon.com/jp/grafana/)

- https://techfeed.io/comments/5fd978d220b65e5c6b97c5d5
- Grafanaのマネージドサービスも合わせて出ているよう
  - https://techfeed.io/comments/5fd9798320b65e5c6b97c5f1

#### [Rancher Harvesterでk8sから仮想マシンを管理する](https://note.com/ryoma_0923/n/n5dc18f50545a)

- https://techfeed.io/comments/5fdb4ea195e7b2ea3e072a56

#### [今さら聞けないLivenessProbeとCrashLoopBackOffの挙動](https://qiita.com/shmurata/items/01109ae1a5a949e7b8e7)

- https://techfeed.io/comments/5fdafd5bdbe8347e7643c2b2

#### [Cluster API v0.3.12](https://github.com/kubernetes-sigs/cluster-api/releases/tag/v0.3.12)

- https://techfeed.io/comments/5fdaff1be83f354d34ef6096

#### [Cloud Native 読書会第二回](https://docs.google.com/document/d/1beh1cRxaU-Qnu_SS574ANH7-q1aH9gFx3YKs3deND18/edit#)

- https://techfeed.io/comments/5fdae3f7dbe8347e7643bfd6

#### [Kubernetes Internal #4](https://k8sinternal.connpass.com/event/199410)


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

```yaml
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

```yaml
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
  - Once enabled, the volume-expander-operator will start polling the platform Prometheus instance that is part of OpenShift Monitoringとあり、OpenShiftでしかできなそう？？
- `kubelet_volume_stats_used_bytes`と`kubelet_volume_stats_capacity_bytes`の2つのメトリックより判断。
- その他設定するannotaionは以下
  - volume-expander-operator.redhat-c​​op.io/expand-threshold-percent: ボリュームの拡張をトリガーする閾値
  - volume-expander-operator.redhat-c​​op.io/expand-by-percent: 拡張される既存ボリュームのサイズに基づくパーセンテージ
  - volume-expander-operator.redhat-c​​op.io/expand-up-to: ボリュームの上限
  - volume-expander-operator.redhat-c​​op.io/polling-frequency：　ポーリングする頻度

参考manifest

```yaml
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

### @inductor

- [Kubernetes 1.20: SIG-API Machineryの変更内容](https://qiita.com/Ladicle/items/85d0ae2ddd4893ac4ca6) by Ladicle
- [AWS・GCPとKubernetesの権限まわりの用語を具体例から理解する](https://tech.jxpress.net/entry/terms-and-concepts-of-iam-for-aws-and-gcp-and-k8s) by JX Press
  - 開発者向けにAWSとGCPのIAMリソースの考え方の違いをわかりやすく解説
  - EKS/GKEに関する例まで踏み込んで解説されている
- [【Go言語】自作コンテナ沼。スクラッチでミニDockerを作ろう](https://kaminashi-developer.hatenablog.jp/entry/dive-into-swamp-container-scratch) by Kaminashi
  - Liz Riceが作ったGo言語製の https://github.com/lizrice/containers-from-scratch をベースに、手を動かしながらコンテナを自前で作ってしまう話
- [Kubernetes Podcast Episode #132: Akri, with Kate Goldenring](https://kubernetespodcast.com/episode/132-akri/)
  - MSのSWEかつAkriのメンテナを務める[Kate Goldenring](https://twitter.com/KateGoldenring)をゲストとして、エッジデバイスを管理するための[Akri](https://github.com/deislabs/akri)に関するあれこれ話している
    - Akriにおける「エッジデバイスの管理」はクラスターで完結している点が特徴
    - デバイス側では何も設定する必要がない。以下のいずれかを満たしているデバイスが自動的に検出される
    - ワーカーノードにUSBなどで接続された周辺機器
    - ワーカーノードの所属するネットワークに接続されたネットワーク越しのデバイス(ネットワークカメラなど)
      - 内部的には[RTSP](https://en.wikipedia.org/wiki/Real_Time_Streaming_Protocol)を用いて接続を試行することによってディスカバリを行っているようだ
    - まだ現状はAlphaで、今後はプロトコルの拡張性を高めたり、ディスカバリ周りの改善などを行っていくといった旨が語られている
      - Device Pluginを使った開発の面白さ
      - Rustを使って開発している点
![](https://github.com/deislabs/akri/blob/main/docs/media/akri-architecture.svg)
