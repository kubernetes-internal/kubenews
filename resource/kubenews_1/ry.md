# ry ネタ

- [KubeLinterを使用したYAMLのベストプラクティスの確保](https://www.civo.com/learn/yaml-best-practices-using-kubelinter)
  - KubeWeekly #240: November 6, 2020
  - Kubernetes YAMLファイルとHelmチャートをチェックして、それらに表されているアプリケーションがベストプラクティスに準拠していることを確認する静的分析ツール
  - CIに統合するなど、様々な使い方が期待できる。
  - 選定理由
    - kubernetesを始めたばかりであったり、なかなか周りに聞ける環境ではない中でbest practiceを最初から設定していくことは難しい
     - kustomizeやhelmと連携していく中で、こういったチェックを簡単にはさめるツールはとてもありがたい。

- [TokenRequestとTokenRequestProjectionのGA](https://github.com/kubernetes/kubernetes/pull/93258)
  - [LWKD Week Ending November 1, 2020](http://lwkd.info/2020/20201102)
    - Secretに書かれないと記載あり
  - [Service Account Token Projection](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/#service-account-token-volume-projection)
    - manifestの記載例
  - [A Look at How to Use TokenRequest Api](https://jpweber.io/blog/a-look-at-tokenrequest-api/)
    - REST APIでの呼び出しについて書かれている。
  - Podに対して期限つきのServiceAccountTokenを指定パスに指定することができ、期限が切れた際は、自動で更新される。
  - 選定理由
    - 期限を決めて自動更新できたり、ポッドまたはServiceAccountが削除されると、サービスアカウントトークンもAPIに対して無効になり、TokenはSecretに残らないと言うことなので、Security 的にとても有用だと思った。

- [Introducing the Anthos Developer Sandbox—free with a Google account](https://cloud.google.com/blog/topics/anthos/introducing-the-anthos-developer-sandbox)
  - ついにAnthosを無料で体験することができるようになった。
  - 新規でGCP上にGKEを立てたり、既存のKubernetesを登録したりできるので、楽しめそう。
  - 選定理由
    - 最近よく耳にするAnthosがつい最近まで無料アカウントではさわれない状態だったので、純粋にありがたい。

- [Unleash developer productivity with Gitpod on Oracle Container Engine for Kubernetes](https://blogs.oracle.com/cloud-infrastructure/unleash-developer-productivity-with-gitpod-on-oracle-container-engine-for-kubernetes)
  - `gitpod.io/#`をURLの最初につけるだけで起動できる。
  - VS Codeライクに使うことが可能
  - .gitpod.yml にimageなどを記載することで、Workspaceをコンテナで立てることができる。
    - https://www.gitpod.io/docs/config-gitpod-file/
  - kubernetesの上で用いることで、使い捨ての開発環境をすぐに立てることができる。

- [Container Security Book](https://container-security.dev/)
  - 前半にContainerの基礎となる部分があり、そこだけでも勉強になる。
  - Containerのセキュリティはいつでも課題になるので、基礎知識として良さそう。
