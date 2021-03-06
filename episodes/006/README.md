# 006

- Hosted by @bells17
- Recording date: 2021-01-22
- Video: https://youtu.be/Gr7dAYtM5W0

## Contents

### @chago

####  [【オンライン】脱初心者への道！Kubernetes Middle Way!! - cndjp第16回](https://cnd.connpass.com/event/198619/)
- [整理しながら理解するKubernetesネットワークの仕組み](https://speakerdeck.com/hhiroshell/kubernetes-network-fundamentals-69d5c596-4b7d-43c0-aac8-8b0e5a633fc2)
- [これから学ぶKubernetesのReconciliation Loop](https://speakerdeck.com/yosshi_/korekaraxue-hukubernetesfalsereconciliation-loop)

####  [Nvidia Views Kubernetes as Key to GPU Accelerated AI Scale](https://www.sdxcentral.com/articles/news/nvidia-views-kubernetes-as-key-to-gpu-accelerated-ai-scale/2021/01/?utm_campaign=website&utm_source=sendgrid&utm_medium=email)

####  [Amazon: NOT OK - why we had to change Elastic licensing](https://www.elastic.co/jp/blog/why-license-change-AWS)
- [Stepping up for a truly open source Elasticsearch](https://aws.amazon.com/jp/blogs/opensource/stepping-up-for-a-truly-open-source-elasticsearch/)
- @_inductor_ , @takamori_tech , @tzkb さんから

### @bells17

#### [Hitachi Kubernetes Service](https://www.hitachivantara.com/en-us/services/edge-to-cloud-infrastructure-services/kubernetes.html)

- 日立さんのManaged Kubernetes Serviceのように見える
- ebookが https://www.hitachivantara.com/en-us/pdfd/ebook/multicloud-kubernetes-management-ebook.pdf に公開されているよう
- まだあまり情報が無いが、ハイブリットクラウドなどでの利用を想定したもので簡単に利用するためのUIを用意したものように見える...
- https://www.hitachivantara.com/en-us/resources.html#vid=6223900960001 の動画内でダッシュボードが映っているが、印象としてはRancherをシンプル目にしたUIという印象

#### [Welcome To The Container Jungle: Docker vs. containerd vs. Nabla vs. Kata vs. Firecracker and more!](https://www.inovex.de/blog/containers-docker-containerd-nabla-kata-firecracker/)

- コンテナランタイムの種類についての紹介記事

#### [ZAP - ZCPをベースとしたマルチK8sのアプリケーション実行基盤](https://youtu.be/KUdLCzHW3hs)

スライド: https://www2.slideshare.net/techblogyahoo/zap-zcpk8s-yjtc-yjtc21-b3-241223242

- ZLabがYahoo!向けに構築しているZCPというKubernetes基盤の上に構築したZAPというアプリケーション基盤の紹介
- ZAPはマルチテナントk8sクラスターでZAP管理者がZAP全体を管理するらしい
- Appというカスタムリソースを記述することで、Kubernetesのリソースを自動作成してくれる
- k8sのトラブルシュートに慣れてない人でもトラブルシュートに取り組めるようにkubectlをラップしていくつかの独自コマンドを追加したflctlというコマンドを提供
- Flagship(Kubernetesクラスターのグループ?)/Ship(グループに参加するKubernetesクラスター)という仕組みによってマルチクラスター化することで大規模Kubernetesクラスターを実現しているよう
- ZAP全体でFlagshipというのは1つにまとめられているのか？それともFlagshipも複数にわかれているのか？というのが気になった


### @ryojsb
#### [GCPSketchnote](https://github.com/priyankavergadia/GCPSketchnote)
GCPの様々なリソースについて絵を使って、動作やユースケースなどの説明してくれている。


#### [CNCF Security Whitepaper Shows the Complexity of Securing Cloud Native Operations](https://thenewstack.io/cncf-security-whitepaper-shows-the-complexity-of-securing-cloud-native-operations/)
- [Cloud Native Security Whitepaper](https://github.com/cncf/sig-security/blob/master/security-whitepaper/CNCF_cloud-native-security-whitepaper-Nov2020.pdf)というものがあるらしい。
- CNCFは、クラウドネイティブ開発は、develop、destribute、deploy、runtimeの4つの異なるライフサイクルフェーズにモデリングする必要があると述べている。
  - Develop: アプリケーション作成段階
    - セキュリティはアプリケーションライフサイクルの早い段階で導入する必要がある。
    - セキュリティテストではコンプライアンス違反や設定ミスを即座に特定しよう。
    - 12 FactorAppなどの推奨デザインパターンに準拠しよう。
  - Destribute: CICDの段階
    - 開発者は、マルウェアを含んだimageをデプロイする可能性がある。
    - 脆弱性、マルウェア、および安全でないコーディングをコンスタントにスキャンする必要がある。
  - Deploy: Containerとして動かす段階
    - 次のことを確認しよう。
      - 署名されたアーティファクト(ソースコード、デザインファイル、テストのエビデンス、ログファイルなどなど)となっているか検証できているか。
      - コンテナイメージはセキュリティポリシーに準拠しているか。
      - ホストの適合性を検証したか。
    - 監視は、次の3つに基づいて実施
      - metrics
      - trace
      - log
  - Runtime: 基盤に関して
      - 認可されたプロセスのみがコンテナ名前空間内で動作する
      - 不正なリソースアクセスを防ぐ
      -　敵対的なツールアクティビティを検出するために、ネットワーク監視を行う 
      
#### [What’s Your Kubernetes Maturity?](https://www.cncf.io/blog/2021/01/12/whats-your-kubernetes-maturity/)
- [Kubernetes Maturity Model](https://www.fairwinds.com/kubernetes-maturity-model)というものをざっくりと解説した記事
  - Phase1: Prepare
    - Kubernetesが、ビジネス目標と技術目標の推進にどのように役立つか、コスト、および達成しようとしていることを検討
  - Phase2: Transform
    - 基礎的な知識や理解、マインドセットだったりエコシステムの変革を行う段階
    - 既存の技術をCloud Nativeな文脈から見ること、技術的負債を払拭してKubernetes内に持ち込まないこと
  - Phase3: Deploy
    - 実際にKubernetes上でApplicationを本番運用し始める。
    - CI / CDのセットアップ、開発者の権限付与、限定的な監視と可観測性の導入
  - Phase4: Build Confidence
    - 経験から自信をつける段階
  - Phase5: Improve Operation
    - Kubernetesクラスターのセキュリティ、効率、信頼性を向上させる段階
  - Phase6: Measure & Control
    - この段階では、何を測定および追跡し、どのようにKubernetesを制御するかを理解すべく、より多くのデータ、インサイト、ツールによる情報を収集して処理する。
    - infrastructure as code and CI/CD driven processes
  - Phase7: Optimize and Auutomate
