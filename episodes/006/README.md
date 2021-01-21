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
