# 005

- Hosted by @bells17
- Recording date: 2021-01-13
- Video: 

## Contents

### @chago

####  [Kubernetes Ingress Controllerの機能比較表](https://docs.google.com/spreadsheets/d/191WWNpjJ2za6-nbG4ZoUMXMpUK8KlCIosvQB0f-oq3k/edit#gid=907731238)
- https://twitter.com/openshiftjp/status/1346963518302658562
- OpenShift Community Japan のツイートより
####  [2021年に注目すべきCNCFの5つのテクノロジーを「Kubernetes Meetup Tokyo」のセッション記事から解説する](https://zenn.dev/hodagi/articles/5461eb6f7e19bb)

####  [Sysdig 2021 container security and usage report](https://sysdig.com/blog/sysdig-2021-container-security-usage-report/)

p.s. 技術書典お疲れ様でした！

### @bells17

#### [Kubernetes で cgroup がどう利用されているか](https://valinux.hatenablog.com/entry/20210114)

- Kubernetesでcgroupがどう利用されているか調べられたという記事
- Kubeletの解析も技術同人誌である程度まとめたくらいには進んだので、そろそろLinuxコンテナやコンテナランタイム周りの理解もしていきたいなということで気になった記事
- なお内容が理解できているわけではないです

#### [Toolboxの話](https://speakerdeck.com/kenya888/toolboxfalsehua-1438a53a-7182-4e0e-98c1-2607fe8047f1)

- 気になる👀

#### [Kubernetes InternalでKubeletについて話すときに使った補足資料です](https://speakerdeck.com/bells17/kubelet)

- https://techfeed.io/comments/60007e344085a1b904ff58e1

#### [Kubeletから読み解くKubernetesのコンテナ管理の裏側](https://techbookfest.org/product/5738785868349440)

- 技術書典10で販売したKubelet解説本です。興味ある方どうぞ
- Boothでも販売開始しました
- https://bells17.booth.pm/items/2649601

### @ryojsb

#### [Kubernetes Storage Performance Comparison](https://medium.com/volterra-io/kubernetes-storage-performance-comparison-v2-2020-updated-1c0b69f0dcf4)
- GlusterFS, CEPH, Portworx, OpenEBS(cStor backend), OpenEBS MayaStor, Longhornの比較記事
- 比較はAKS上で実施
- 結果としては、Portworx と OpenEBS Mayastorがすごそう

#### [KubernetesにおけるContainer Object Storage Interface (COSI)の概要](https://qiita.com/ysakashita/items/9916f8ae922601e6fe6e#apis)
- Object Storage用のCSI相当であるCOSIについての解説記事
- BucketRequest (PVC)、Bucket (PV)、BucketClass (StorageClass)は分かった。
- BucketAccessRequest、BucketAccess、BucketAccessClassあたりがいまいち。。。
