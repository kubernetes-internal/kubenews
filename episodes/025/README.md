# 025

- Hosted by @bells17
- Recording date: 2021-07-02
- Video: https://youtu.be/-_5Xlf00h-Q
- Guest:

## Contents

### [ry](https://twitter.com/URyo_0213)
#### [Monitoring Kyverno with Prometheus](https://nirmata.com/2021/06/18/monitoring-kyverno-with-prometheus/?utm_medium=email&_hsmi=136268628&_hsenc=p2ANqtz-8LKorO3aGxWZ3I333vWoVNs93yMD6lYS6wVzXKtyuqlzx5vm2QmMoBmImb_JCpPeVypjp7aFsYVUDzWkyefOrMylSutg&utm_content=136268628&utm_source=hs_email)

ついに、keyvernoがmonitoringされている例がでました。
keyvernoがに関しては、以下を参照ください。
- [keyverno](https://github.com/kyverno/kyverno)
- [Policy Engine on Kubernetes](https://speakerdeck.com/ry/policy-engine-on-kubernetes)

#### [cAdvisor and Kubernetes Monitoring Guide](https://www.cloudforecast.io/blog/cadvisor-and-kubernetes-monitoring-guide/?utm_medium=email&_hsmi=136268628&_hsenc=p2ANqtz-9kxHZC-21qKlC7vStJ7nZ56D0bpMNiCODTo08Ty8FqWAt05W12RedPi7ifoxxXzLOFH9WeIo4k7kJabFtiS57gMr_Vbg&utm_content=136268628&utm_source=hs_email)
`Since cAdvisor is already integrated with the kubelet binary, ~~`とあり、kubeletに統合されています。

(これを見るまで、docker用のものだと思ってました。)

この記事では、cpu, memory, diskなどの項目に関するmetric名やGrafanaから確認する方法についてが書かれているので、とても参考になる資料となっています。

#### [Avoiding Kubernetes Cluster Outages with Synthetic Monitoring](https://www.infracloud.io/blogs/avoiding-kubernetes-cluster-outages-synthetic-monitoring/?utm_medium=email&_hsmi=136268628&_hsenc=p2ANqtz-_aYVNSzzibfav2o22vVUAvukcg1dUvqw9o0EFcjlonLoltfr8Jdv51KLqd5bcrww_E8kStXOy4Q-2dIecm5dp8mhNMwA&utm_content=136268628&utm_source=hs_email)
- [Kuberhealthy](https://github.com/kuberhealthy/kuberhealthy)
  - khcheck / khjob（Kuberhealthy check / Kuberhealthy job）と呼ばれるカスタムリソースによって作成されたテストコンテナーを用いる
  - khjobが1回実行されるのに対し、khcheckは定期的に実行されることを除いて、両方のカスタムリソースの機能はほぼ同じ
  - Kuberhealthy合成チェックのユースケース
    - ネットワークの変更
      - 実行する必要のある主要なネットワーク変更がある場合は、HTTPまたはTCP khchecksを使用して重要なエンドポイントをチェック
    - IAMの変更
      - 適切なKIAM機能を検証するためのKIAMチェックがある。
    - エンドポイント接続
      - データベースやKey-Valueストアなど、クラスター外の重要な要素が稼働しているかどうかを常に確認できる。
    - AMI検証
      - AMIチェックを変更して、NTP同期、ディレクトリ構造、ユーザーアクセスなど、カスタムベイクされたAMIの重要な機能を確認できる。
    - CoreDNSチェック
    - リソースクォータチェック

#### [Run the HAProxy Kubernetes Ingress Controller Outside of Your Kubernetes Cluster](https://www.haproxy.com/blog/run-the-haproxy-kubernetes-ingress-controller-outside-of-your-kubernetes-cluster/?utm_medium=email&_hsmi=136268628&_hsenc=p2ANqtz-9HT5IOiCl6ZsXHnx30juwpMPq17EJ5U-uQkif-7d-ATXBi6mGdqlZl_doy-JexA5L3xfhHPaMb8EgmXbbwSM33FV3b0g&utm_content=136268628&utm_source=hs_email)

#### [Handling Auth in EKS Clusters: Setting Up Kubernetes User Access Using AWS IAM](https://nextlinklabs.com/insights/handling-authentication-in-EKS-clusters-kubernetes-AWS-IAM?utm_medium=email&_hsmi=136268628&_hsenc=p2ANqtz-98auBpz71i9RKXibaaCZuPssqSLvFu5XsnRJaLz_V1BgpjUtGDXhweg5wb28sgAm_Y04kVkbwc6W0jXNHSeqvhAmACEg&utm_content=136268628&utm_source=hs_email)

#### [What end-users want out of Prometheus remote storage: A comparison of M3 and Thanos](https://chronosphere.io/learn/what-end-users-want-out-of-prometheus-remote-storage-a-comparison-of-m3-and-thanos/?utm_campaign=kube-weekly&utm_medium=cncf&_hsmi=136268628&_hsenc=p2ANqtz--1ulP4sIeiU3tFwk1iw6XBnJh8bEoV_GiYDv4s-JVnYd042EyVmXAimvFPoYGOkW7cle0tzSdc4tj_1KHDH8HJdGVXxw&utm_source=newsletter)
- prometheusのリモートストレージソリューションとして、以下が人気
  - Thanos
  - M3
  - Cortex
- 以下の観点でThanosとM3を比較
  - 信頼性と可用性
    - Thanos
      - クエリアによって取得されたデータに加えてルール（アラートルールやPrometheusレコーディングルールなど）を適用できるネイティブクエリサービスがある。
      - Thanosの分散読み取りまたはクエリパスが原因で失敗率が高くなることがある。
    - M3
      - 集中ストレージを備えた最適化されたクエリエンジンを持つように構築および設計されている。
      - M3のクエリサービスは、クォーラム読み取りロジックを使用して、各データポイントの3つのコピーのうち少なくとも2つがM3DBからフェッチされ、クエリエージェント（Grafanaなど）に返される結果を一貫して計算する。
      - M3のクエリサービスはクエリ要求に優先順位を付けないため、要求（特に大規模な要求）の流入により、ボトルネックが発生し、クエリ処理全体の速度が低下する可能性がある。
  - スケーラビリティとシンプルさ
    - Thanos
      - Thanosは、PrometheusのProxyの役割としてサイドカーで構成される。
      - ???
    - M3
      - 分散時系列データベース（M3DB）、取り込みおよびダウンサンプリング層（M3コーディネーター）、およびクエリエンジン（M3クエリ）の3つのコアコンポーネントで構成されている。
      - アーキテクチャ上、M3は簡単にスケールアップまたはスケールダウンできる。 
      - M3DBは1つのユニットとして水平方向にスケールできるが、クラスター内のM3DBノードの数のサイズを変更する際、M3DBはステートフルであり、ノードメンバーシップの変更時にピアにデータをストリーミングするため、大規模な管理が困難になる可能性がある。
        - こちらは、Operatorによって自動的にスケールアップおよびスケールダウンできるようになっている。
  - 効率とスピード
    - Thanos
      - Thanosサイドカーは、2時間のブロックでオブジェクトストレージにデータをアップロードする。
      - Thanosはコンパクターコンポーネントを使用してこれらのブロックを時間の経過とともにマージし、クエリ効率を向上させ、ストレージサイズを削減する。
      - Thanosコンパクターは一度に1つのインスタンスのリクエストのみを処理するように設定されているため、ユーザーはデータが完全に圧縮されるのを待ってから（つまり、2時間ごとに）集計データをクエリできる。
    - M3
      - すべてのダウンサンプリングおよびアグリゲーションはM3・コーディネーターによってローカルに行われる。
      - この設定では、集計はリアルタイムで行われ、各解決間隔の終わりに、集計されたメトリックがすぐにクエリに使用できます（つまり、5分の解像度でデータを集計する場合は5分ごと）。
      - M3コーディネーターサイドカーにダウンタイムがあると、集約されたデータが失われる可能性がある。
  - アフォーダビリティ

### [chago](https://twitter.com/it__chago)


### [bells17](https://twitter.com/bells17_)
