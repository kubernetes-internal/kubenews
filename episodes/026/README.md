# 026

- Hosted by @bells17
- Recording date: 2021-07-09
- Video: https://youtu.be/XlJu96QZi94
- Guest:

## Contents

### [chago](https://twitter.com/it__chago)

### [bells17](https://twitter.com/bells17_)

https://zenn.dev/bells17/articles/k8s-cloud-native-and-other-20210709

### [ry](https://twitter.com/URyo_0213)

#### [Kubernetes Essential Tools: 2021](https://itnext.io/kubernetes-essential-tools-2021-def12e84c572)

#### [Run the HAProxy Kubernetes Ingress Controller Outside of Your Kubernetes Cluster](https://www.haproxy.com/blog/run-the-haproxy-kubernetes-ingress-controller-outside-of-your-kubernetes-cluster/?utm_medium=email&_hsmi=136268628&_hsenc=p2ANqtz-9HT5IOiCl6ZsXHnx30juwpMPq17EJ5U-uQkif-7d-ATXBi6mGdqlZl_doy-JexA5L3xfhHPaMb8EgmXbbwSM33FV3b0g&utm_content=136268628&utm_source=hs_email)

(要約)

Podへ外部から到達する際に、NodePortもしくはLoad BalancerのServiceを公開する必要があり、クラウド環境では、LoadBalancerオプションは各クラウドプロバイダーが用意しているロードバランサーがありそれを利用できるが、オンプレミス環境では、通常 NodePortを使用し、ロードバランサーを手作業で前面に配置する必要があります。

従来のレイアウトでは、外部ロードバランサーがワーカーノードの 1 つにトラフィックを送信し、次に Kubernetes がIngressコントローラーポッドを実行しているノードにトラフィックを中継します。

HAProxy Kubernetes Ingressコントローラのバージョン 1.5 以降では、Kubernetes クラスターの外部で実行するオプションがあり、前にロードバランサーを追加する必要がなくなります。

注意すべき点として、IngressコントローラがPodとして実行されておらず、Kubernetes クラスタ内に存在しない場合、Pod レベルのネットワークに何らかの方法でアクセスする必要があります。

Project Calicoを Kubernetes のネットワーク プラグインとしてインストールし、次に Calico が BGP ピアリングを介してIngressコントローラ サーバーとネットワーク ルートを共有できるようにすることで、この問題を解決することができます。

#### [Handling Auth in EKS Clusters: Setting Up Kubernetes User Access Using AWS IAM](https://nextlinklabs.com/insights/handling-authentication-in-EKS-clusters-kubernetes-AWS-IAM?utm_medium=email&_hsmi=136268628&_hsenc=p2ANqtz-98auBpz71i9RKXibaaCZuPssqSLvFu5XsnRJaLz_V1BgpjUtGDXhweg5wb28sgAm_Y04kVkbwc6W0jXNHSeqvhAmACEg&utm_content=136268628&utm_source=hs_email)
