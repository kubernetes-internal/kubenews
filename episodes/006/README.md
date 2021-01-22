# 006

- Hosted by @bells17
- Recording date: 2021-01-
- Video: 

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
[What’s Your Kubernetes Maturity?](https://www.cncf.io/blog/2021/01/12/whats-your-kubernetes-maturity/)
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
    - 
  - Phase6: 
  - Phase7: 
