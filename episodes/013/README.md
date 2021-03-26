# 013

- Hosted by @bells17
- Recording date: 2021-03-26
- Video: https://youtu.be/RGms05yeuq8
- Guest: -

## Contents


### @ryojsb

#### [Open Source solutions for chaos engineering in Kubernetes](https://blog.flant.com/chaos-engineering-in-kubernetes-open-source-tools/)

#### [MinIO as Object Storage as a Service](https://blog.min.io/object_storage_as_a_service_on_minio/)

#### [netapp astra](https://siliconangle.com/2021/03/10/netapp-astra-brings-data-portability-kubernetes-apps-netapp-astra/)
- コンテナイメージからKubernetesの状態情報、構成データまで多岐にわたるデータを管理するソリューション
- 通常のスナップショットでデータを保護する機能が含まれていて、ユーザーは、データが誤って削除または破損した場合に、Kubernetes クラスターを以前のスナップショットに戻すことが可能
- リモート・バックアップを使用して、アプリケーションとそのアプリケーションの現在の状態に対するフルバックアップを取り、別のリージョンの別の Kubernetes クラスターに復元することが可能。
- アクティブクローンを用いて、アプリ全体とそのデータを、場所に関係なく、あるKubernetes クラスターから別のクラスターに移動可能。

#### [Configure your Kubernetes Ingress with Ingress Builder](https://www.jetstack.io/blog/introducing-ingress-builder/)
以前にNetworkPloicyに関して、GUIでManifestを作成できるツールをご紹介しましたが、
今回は、Ingressに関するツールが出たようです。
https://ingressbuilder.jetstack.io/#tab-content-v1

Ingress Builder was developed to make configuring Ingress resources more interactive by allowing users to discover and configure annotations for their Ingress controllers easily in a single web interface.

と書かれているので、Annotation専用になっている。
少し勿体無い。。。

#### [Who Needs Open Policy Agent?](https://www.itprotoday.com/devops-and-software-development/who-needs-open-policy-agent)
- EnterpriseはOPAが必要か。
  - 会社にOPAが必要かどうかは、ワークロードをどの程度スケーラブルにする必要があるか、およびワークフローの作成をどの程度自動化するかによって異なる。
- いつOPAを採用する必要が
  - 新しいテクノロジーの採用に慎重な場合は、OPAを本番ワークフローに組み込む前に少し待つことをお勧する。
  - エンジニアがどのようなスキルと好みを持っているかに一部依存するため、最新かつ最高のDevOpsツールを使用するのが好きならOPAは良いかもしれない一方、最先端よりも実証済みの方法を好む場合は、OPAが成熟するのを待つことをお勧します。 

#### [Cosign — Signed Container Images](https://dlorenc.medium.com/cosign-signed-container-images-c1016862618)
Notaryとどっちが有用？

### @bells17

#### [KUBERNETES THE HARD WAY IN "VAGRANT"?](https://suraj.io/post/2021/03/kthw-vagrant/)

- Kubernetes The Hard WayをVagrantでやるためのリポジトリを紹介してくれてる
- control plane(+etcd) と workerが別々のVMに分かれてて結構本格的な気がしてる

#### [VictoriaMetrics と Grafana による Kubernetes クラスタのモニタリング](https://blog.cybozu.io/entry/2021/03/18/115743)

- サイボウズさんがVictoriaMetricsを採用した話
- VictoriaMetrics operatorにもコントリビューションしてるのが強いなと思った


### @chago
