# 003

- Hosted by @bells17
- Recording date: 2020-12-11
- Video:

## Contents

### @bells17

#### [「イラストでわかるDockerとKubernetes」は完全に良書](https://jaco.udcp.info/entry/2020/12/08/215058)

#### [KubernetesのLoadBalancerやClusterIPを用いた中間者攻撃（CVE-2020-8554）](https://knqyf263.hatenablog.com/entry/2020/12/08/155720)

#### [Amazon EKS add-ons のご紹介: Kubernetes 運用ソフトウェアのライフサイクル管理](https://aws.amazon.com/jp/blogs/news/introducing-amazon-eks-add-ons-jp/)

#### [WebAssembly Night #10](https://youtu.be/HOAuzkGLVd8)

#### [ちょいと早い忘年会 OpenShift.Run Winter 2020 #11](https://openshift.connpass.com/event/191402/)

### @ryojsb

#### With the release of GKE node version 1.19, the Container-Optimized OS with Docker (cos) variant is deprecated

- [release note on 12/8](https://cloud.google.com/kubernetes-engine/docs/release-notes#december_8_2020)
- [containerd image](https://cloud.google.com/kubernetes-engine/docs/concepts/using-containerd)

#### Amazon EMR on Amazon Elastic Kubernetes Service (EKS)
- Amazon EMR: big data platform for processing vast amounts of data using open source tools such as Apache Spark, Apache Hive, Apache HBase, Apache Flink, Apache Hudi, and Presto. 
- [AWS News Blog](https://aws.amazon.com/jp/blogs/aws/new-amazon-emr-on-amazon-elastic-kubernetes-service-eks/)
- さまざまなEC2インスタンスタイプでパフォーマンスを最適化して、価格とパフォーマンスの要件を満たしていたものを、EKS上で動かすことでリソースを共有したり、管理を統合できたりなどのメリットがある。
- 現在EC2で使用しているものと同じEMR機能をすべてEKSで利用できる。

#### Kubernetes CRDs = Huge Pain In Multi-Tenant Clusters
- [DevSpace Technologies Inc. Blog](https://medium.com/@loft-sh/kubernetes-crds-huge-pain-in-multi-tenant-clusters-a4b394ccd2d9)
- 簡単にどんなことが書かれているか
Kubernetesにおけるマルチテナンシーとは、複数のユーザー、アプリケーション、またはワークロードがいわゆるテナントを形成し、共有クラスター内で互いに共存しているシステムアーキテクチャです。

マルチテナントを管理する際、以下のことが重要である。

・侵害されたテナントが残りのユーザーまたはワークロードに与える影響を最小限に抑えるために、テナント間に適切なレベルの分離を実装する必要がある。

・各テナントがタスクを完了するために必要なものにアクセスできるよう、コンピューティング、ネットワーキング、およびその他のリソースがクラスター内のすべてのテナント間で公平に共有されるようにする必要がある。

この２つを満たすために、テナントには独自のCRDおよびRBACルールを追加または管理することを許可されていないというケースが多い。

マルチテナントクラスターでCRDを使用する際の問題点

・クラスター内の他のユーザーが使用している他のリソースと競合しないようにする

・マルチテナントクラスターにセキュリティの脆弱性をもたらす可能性がある(https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-11247)

・CRDが互換性のない方法で変更または変更された場合、クラスター全体で問題が発生する可能性がある。

・マルチテナント設定でCRDを使用すると、管理上の責任と課題がさらに追加される。

解決策

・回避できる場合はCRDを使用しない。

・個別のクラスターまたは仮想クラスターを検討する。(https://loft.sh/blog/introduction-into-virtual-clusters-in-kubernetes/)

### @chago

- [Announcing General Availability of HashiCorp Nomad 1.0](https://www.hashicorp.com/blog/announcing-general-availability-of-hashicorp-nomad-1-0)
  - Nomad 1.0 GA
  - Nomad は hashicorp社のコンテナオーケストレータ

- [NetApp To Embed Rancher Kubernetes In Its Hyperconverged Infrastructure](https://www.crn.com/news/cloud/netapp-to-embed-rancher-kubernetes-in-its-hyperconverged-infrastructure)
  - NetAppがHCIにRancherを取り込む
