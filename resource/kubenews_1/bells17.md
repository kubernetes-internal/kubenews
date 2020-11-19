## bells17 ネタ

### [【インターンレポート】KubernetesのOperator Patternを用いた効率的なHypervisorの更新システムの構築](https://engineering.linecorp.com/ja/blog/internship-report20-hypervisor-update-system-with-kubernetes/)

- LINEのインターンの方がVerda開発チームという社内プライベートクラウドのHypervisorの更新処理システムをKubernetes Operatorで作成したというお話
- 元々Jenkins + Ansibleでタスクを並列実行していたものを、Kubernetes Operator + Ansibleとすることで高速化につながったとのこと
- 一部出ていたCRDのSpecを見る限り内部的にはOperatorの調整ループ内部でAnsibleを実行している雰囲気
- 個人的には(調べてないけど) https://access.redhat.com/documentation/ja-jp/openshift_container_platform/4.2/html/operators/osdk-ansible と近いのでは？というところが気になってる


![１【インターンレポート】KubernetesのOperator_Patternを用いた効率的なHypervisorの更新システムの構築_-_LINE_ENGINEERING](https://user-images.githubusercontent.com/2158863/99149095-5751da80-26cf-11eb-80c5-fe2eb7df37f4.png)


### [KEP-1959: Service Type=LoadBalancer Class Field](https://github.com/kubernetes/enhancements/pull/1960)

- ついにServiceの type: Loadbalancer でもLBを使い分けられるように
- CCM周りを開発したりする側からするとありがたい
- type: Loadbalancerだけを扱う拡張アプリケーションとかを書いてる人からしてもありがたいかも
- これいんだくたーさんにはあんまりいらなそうって言われたんだけどプラットホーム提供者側としては結構ありがたいと思ってる
- すぱぶらさんのツイートで見つけた

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">複数の Service type=LoadBalancer の実装を使えるようにしようという KEP。たしかに Service type=LoadBalancer が提供されてしまっていると他の実装を使えない。新しい Service API では GatewayClass としてこれに相当する機能があるそう。 <a href="https://twitter.com/hashtag/kubernetes?src=hash&amp;ref_src=twsrc%5Etfw">#kubernetes</a> <a href="https://t.co/ioM0c8yOFf">https://t.co/ioM0c8yOFf</a></p>&mdash; すぱぶら (Kazuki Suda) (@superbrothers) <a href="https://twitter.com/superbrothers/status/1322699680996757505?ref_src=twsrc%5Etfw">November 1, 2020</a></blockquote>

### [Rancher Day](https://rancher.co.jp/rdt2020/)

- 11/12にあったRancherという様々な環境のKubernetesクラスターを管理・運用・構築できるソフトウェアなどを開発しているRancher Labsの各種製品に関するイベント\
- 個人的には以下のあたりが面白かった/聞けてよかった点
  - KDDIさんが自社内のプライベートクラウド環境へのCaaS提供をRancherを使って行っているという話し
    - Rancherを外側から拡張して色々な開発を行いCaaSを提供しているという話が面白かった
    - ちなみにRacher Labs的にはこういう外側での拡張は大歓迎とのこと

### [イラストでわかるDockerとKubernetes](https://www.amazon.co.jp/dp/4297118378)

- まだ情報がほぼ無いんだけど、タイトル的にはDocker/Kubernetes初学者向けの本？
- 著者はNTTの徳永さんという方(多分直接お話したこと無い)
  - https://www.youtube.com/watch?v=W5dcfyuHohw
- 初心者向けの情報が増えるのは良さそう

###  [CKS Certified Kubernetes Security Specialist](https://medium.com/faun/cks-certified-kubernetes-security-specialist-418d55c86465)

- 新しくできたk8sの資格であるCKSについての紹介記事
- CKSの試験範囲や勉強に役立つコンテンツへのリンクが紹介されている
- ちょっと勉強してみたい気もする(まだCKAも持ってないけど)

### [eBPF - The Future of Networking & Security](https://cilium.io/blog/2020/11/10/ebpf-future-of-networking/)

- eBPFとCiliumなどの解説記事
- 今までに何度か(e)BPFをテーマにしたセッションを聞いてなんとなく一部分を知った気はするけど、でもeBPF相変わらず全然わかってないという感じだったんだけど、この記事見て改めて興味出てきたので勉強したい
- わかってないんだけど、図とかいっぱい使って結構細かく特徴を説明してくれてるのでちょっとだけわかったつもりになれる
- 参考で紹介されてる https://ebpf.io/ も見て勉強してきたい

### [Introduction to Kubernetes Networking](https://www.tigera.io/lp/kubernetes-networking-ebook)

- 登録するとKubernetesのネットワークに関する情報をまとめたPDF本がもらえる
- 51pあったからちょっと時間をとって見ていきたい
- 内容的にはKubernetesの基本的なネットワークの話しからeBPFやCalicoの話しなど結構網羅的な感じっぽい
- 最近taishoさんもzennでKubernetesのネットワーク本を出してたと思うので合わせて読んできたいな


### [Kubernetesネットワーク 徹底解説](https://zenn.dev/taisho6339/books/fc6facfb640d242dc7ec)

- taishoさんが書いたKubernetesのネットワークで起きてることを色々と書いてくれてるzennの本
- 僕が弱々な色んなネットワークの色んな概念やコマンドとかその見方など含めてKubernetesのネットワークがどんなふうに設定されているについて色々と書いてくれてるっぽい
- ぶっちゃけネットワークの知識が無いので軽く眺めただけだと雰囲気しかわからないけど、すごいわかりやすく書いてくれてる気がしているので、これをベースに色々試してみてネットワーク周りの理解を深めたいなという感じ
- まずこれを元に勉強してからeBPFとかも触っていきたい

### [Banzai Cloud Logging operator](https://github.com/banzaicloud/logging-operator)

- Banzai Cloudが提供するfluentd/fluent-bitのOperator
- Rancher Day 2020で紹介されててRancher2.5からのRancherのLoggingはこれが使用されるらしい
- 実態としてはKubernetesのログを転送するためのfluent-bit/fluentdのOperatorっぽくて結構良さげな印象だった

![logging_operator_flow](https://user-images.githubusercontent.com/2158863/99152424-0c42c200-26e5-11eb-9594-4b47489f7b7a.png)

### [Geographically Distributed Stateful Workloads Part One: Cluster Preparation](https://www.openshift.com/blog/geographically-distributed-stateful-workloads-part-one-cluster-preparation)

- 地理的に分散されたStatefulワークロードを動かす3つのアクティブ/アクティブ構成のOpenshiftクラスターの構築方法について話されていて面白かった
- リクエストをクラスター間でデプロイするためのGSLBとしてRoute53を利用して分散を行っていて(DNSによるクラスターへのリクエスト分散をしてるっぽい)
- クラスター間の接続にRancherのSubmarinerを利用していて
- クラスター間の信頼確立のための認証局をVaultで用意して
- 証明書管理をcert-managerで行って
- といった感じでマルチクラスター運用のノウハウが書かれていて面白かった
- この記事ではStatefulワークロード自体には詳しく触れていないけど、それは前提となる別のブログ記事「[Disaster Recovery Strategies for Applications Running on OpenShift
](https://www.openshift.com/blog/disaster-recovery-strategies-for-applications-running-on-openshift)」で触れられていて
- 元記事と同じアクティブ/アクティブのときにはCockroachDBやTiDBなどの利用を例として上げていたり
- また2クラスターで構築した際のアクティブ/パッシブのパターンについてレプリケーションやストレージレベルでの同期などのパターンによるディザスタリカバリの方法が紹介されていた

![Geographical-Availability-with-OpenShift-Nov-02-2020-04-06-03-66-PM](https://user-images.githubusercontent.com/2158863/99153101-b1f83000-26e9-11eb-993d-3b491651157e.png)
