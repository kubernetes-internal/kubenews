# 001

- Hosted by @chago
- Recording date: 2020-11-27
- Video: https://youtu.be/DXDF3TOJ7l0

## Contents

### @ryojsb

- [Edge Computing with openness](https://www.cncf.io/webinars/kubernetes-in-the-context-of-on-premises-edge-and-network-edge-computing/)
  - kubeweekly 
  - 今後、ますます使い道が増えていくであろうEdge ComputingについてのKubernetes活用方の紹介
  - 個人的には、2019年にwalmartの話を聞いてから、edge-computingにおけるkubernetesの活用に意識が向きはじめた。
    - [KubeCon North America 2019](https://kccncna19.sched.com/event/UdJf/keynote-seamless-customer-experience-at-walmart-stores-powered-by-kubernetesedge-maneesh-vittolia-principal-architect-sriram-komma-principal-product-owner-walmart)
  - kubeedgeというものも増えていた。
    - [CNCF Cloud Native Interactive Landscape](https://landscape.cncf.io/)
    - [github - kubeedge](https://github.com/kubeedge/kubeedge)

- [kubectl logsのデフォルトコンテナを指定](https://text.superbrothers.dev/201123-allow-to-preselect-interesting-container-in-logs/)
  - [すぱぶらさん](https://twitter.com/superbrothers)による投稿
  - これまで、ずっと「kubectl logs ~ -c <container name>」
  - kubernetes 1.18から、annotationに`kubectl.kubernetes.io/default-logs-container: container name`を用いることで、-cで指定しない際のデフォルトのコンテナを選択できるようになった。

- [Chaos Engineering tools comparison](https://www.gremlin.com/community/tutorials/chaos-engineering-tools-comparison/)
  - Chaos Engineeringの比較について書かれている。
  - GremlinというChaos Engineering Toolについて書かれている記事
    - [Developers.IO](https://dev.classmethod.jp/articles/gremlin_ecs_php_sample_app/)

### @chago

- [Diamanti Extends Kubernetes Stateful Storage Reach and Support for AWS](https://thenewstack.io/diamanti-extends-kubernetes-stateful-storage-reach-and-support-for-aws/)
  - Diamantiはコンテナ版HCI
  - ハイブリッドクラウドに対応するため「spektra」をリリース
    - 最初にAzureをサポートし、今回新たにAWSサポート発表
    - 2021年初頭にはGCPも対応予定

- [How to set up k0s Kubernetes: A quick and dirty guide](https://www.mirantis.com/blog/how-to-set-up-k0s-kubernetes-a-quick-and-dirty-guide/)
  - MIRANTIS社
    - Docker Enterpriseを買収したことで話題に
  - (参考)[早速K0sを試してみた(日本情報通信株式会社)](https://www.niandc.co.jp/sol/tech/date20201124_1935.php)
    - minikubeと違いvirtualboxやKVMが不要

### @bells17

#### [おうち Kubernetes のための Auth0 コトハジメ](https://atpons.hateblo.jp/entry/20201122/1606014048)

- https://github.com/int128/kubelogin というkubectlプラグインを使ってAuth0の認証をKubernetesクラスターに組み込むという内容
- Kubernetesの認証方法については理解が浅い & どこからとっついて行けばよいかピンと来てないのでかなり面白かったし、勉強になった
- Kubernetesの認証の理解を深めるきっかけにしたいので今度試してみたいな

#### [Nomad, Kubernetes, and a Pragmatic Look at Choosing Orchestrators](https://www.hashicorp.com/blog/nomad-kubernetes-a-pragmatic-look-at-choosing-orchestrators)

- Nomadはhashicorp社が開発しているコンテナオーケストレーターの1つ
- この記事ではhashicorpの視点でNomadとKubernetesの比較やどんなユースケースにNomadが適しているかなどを説明してくれている
- またここ2年でNomadを導入する企業も増えているとのこと
- Nomadはgetting startedくらいしか試した記憶がないので、いつかアーキテクチャなど含めて勉強してみたい

#### [LitmusChaos and Argo Bring Chaos Workflows to Kubernetes](https://thenewstack.io/litmuschaos-and-argo-bring-chaos-workflows-to-kubernetes/)

- LitmusChaosというKubernetesを利用したカオスエンジニアリングツールとArgoというワークフローエンジンを利用したカオスエンジニアリングについて先日のKubeConでお話されてた内容をまとめたものっぽい
- LitmusChaosを使うとPodを削除したりなど色んなカオスエンジニアリングを実現できるテンプレートが揃っている
- こういうカオスエンジニアリングをCIのテストに組み込んでいくのもできるのかもなーと思った

