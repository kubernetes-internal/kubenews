# 009

- Hosted by @bells17
- Recording date: 2021-02-12
- Video: https://youtu.be/WH3FcQY3zk8
- Guest: -

## Contents

### @chago

#### [Kubernetesを標的とする新たなTeamTNTのクリプトジャックマルウェア](https://unit42.paloaltonetworks.jp/hildegard-malware-teamtnt/)
- TwitterのTLで話題になっていた
- セキュアではないDockerデーモンを悪用し、悪意のあるコンテナイメージをデプロイする

#### [NetworkPolicy Editor: Create, Visualize, and Share Kubernetes NetworkPolicies](https://cilium.io/blog/2021/02/10/network-policy-editor)

### @bells17

### @ryojsb
#### [Kubernetes Policy Comparison: OPA/Gatekeeper vs Kyverno](https://neonmirrors.net/post/2021-02/kubernetes-policy-comparison-opa-gatekeeper-vs-kyverno/)
- PSP(Pod Security Policy)の廃止に伴って、代替手段としてOPA-GAtekeeperとKyvernoを比較している。
- ゲートキーパーの利点
  - 非常に複雑なポリシーを表現できる
  - コミュニティにおける確立性の高さ
  - 可用性と拡張性のために複数のレプリカをサポート
- ゲートキーパーの短所
  - 新しいプログラミング言語を必要とすることの学習コスト
  - Munationがまだ初期段階
  - Generationの能力がない
  - ポリシーが複雑で、実装するには複数のドキュメントが必要
  
- Kyvernoの利点
  - ポリシー表現のシンプルさ
  - Mutationが安定している
  - GeneratingやSyncなどの機能があり、ユースケースが多様
- Kyvernoの短所
  - 複雑なポリシーの作成が一般的に不可能
  - APIルックアップ機能は初期段階 
  - HAが未対応
  
#### [NetworkPolicy Editor: Create, Visualize, and Share Kubernetes NetworkPolicies](https://cilium.io/blog/2021/02/10/network-policy-editor)

#### [EKS vs GKE vs AKS](https://www.stackrox.com/post/2021/01/eks-vs-gke-vs-aks-jan2021/)
- 3つのサービスを表を用いて比較してくれている。
