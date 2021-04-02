# 014

- Hosted by @bells17
- Recording date: 2021-04-02
- Video: https://youtu.be/VxRDMBmaDgU
- Guest: -

## Contents


### @ryojsb

#### [Quark Container](https://github.com/QuarkContainer/Quark)
RUST製のOCI Runtime
- OCI compatible
- Secure
- High Performance

ゲストシステムコールを通じて、QuarkのKernelを使う。
Host Kernelを使う場合は、QkernelからQcall + Host systemcall もしくは IO-Uring

#### [Modern continuous delivery on Kubernetes for developers](https://dev.to/gabrieltanner/modern-continuous-delivery-on-kubernetes-for-developers-5chf)
〇 CDの概念
- 宣言型
  - 開発者は何を行う必要があるかを定義し、残りをCDツールに処理させる
- スケーラブル
  - 既存のパイプラインまたは宣言的に定義されたプロジェクトに、新しいサービスを追加することの容易性やサービスのこれらのさまざまな構成を維持することに対する労力を考慮する必要がある。
- 拡張可能性
  - 既存のツールを使用してCDワークフローと統合し、既存の機能とともに新しいカスタム機能を実装することができるか
  - Prometheusなどの可観測性ツールやJmeterやNeoloadなどのテスト自動化
- 品質ゲート
  - サービスを本番環境にデプロイする前に、具体的に定義された基準（応答時間、エラー率、スループットなど）が満たされていることを自動的に確認するための仕組み
- SLI
  - 応答時間、エラー率、スループットなど、アプリケーションのいくつかの側面の定量的指標
- SLO
  - テストに合格するために満たす必要があるSLIを使用して特定の条件

〇 Keptonの紹介
- Kobaさん提供
- kubestrというツールについて

```
宣言型アプローチ

Keptnには、SLIやSLOなどのSRE原則に基づく組み込みの品質ゲートも含まれており、
定義された基準を評価およびスコアリングして、新しいバージョンを次の展開段階に昇格できるかどうか、
または保留する必要があるかどうかを判断できます。

JMeter、LitmusChaos、Prometheusなどの多くの有名なサービスとの統合をすでに備えており、ユーザーは独自の統合を簡単に追加できる。
```

この後、Keptonについての導入方法が書かれている。

#### [Identify, Evaluate and Benchmark Kubernetes Storage](https://www.kasten.io/press-releases/kubestr-open-source-kubernetes-solution)
- kobaさん提供
- [kubestr](https://kubestr.io/)について


### @bells17

#### [1ヶ月間仕事でOSSの開発をしてきた](https://blog.tako8ki.me/posts/cyberagent-oss-job/)

#### [Postgres Operator](https://github.com/zalando/postgres-operator)

- おまけ
  - https://github.com/banzaicloud/logging-operator/blob/3.9.2/pkg/sdk/api/v1beta1/logging_types.go#L275

#### [KubernetesのReconcile処理で無駄な更新をしない方法](https://zenn.dev/zoetro/articles/7cf5bbf58e163e)

### @chago

#### [コマンド1発でKubernetes上にProduction Readyな環境を手に入れる](https://www.lifull.blog/entry/2021/03/30/100000)
- @mochizuki875 さんからの提供

#### [ネットアップ、Kubernetesアプリとデータの統合管理「NetApp Astra」発表](https://ascii.jp/elem/000/004/049/4049630/)
