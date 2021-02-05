# 008

- Hosted by @bells17
- Recording date: 2021-02-05
- Video: https://youtu.be/QtHOLScNtXY
- Guest: @tzkb

## Contents

### @tzkb
#### [KUBERNETES上にGo言語とNoSQLで、独自のマイクロサービスフレームワークを構築した話](https://speakerdeck.com/iwask/kubernetes-shang-ni-go-yan-yu-to-nosql-de-du-zi-falsemaikurosabisuhuremuwakuwo-gou-zhu-sitahua)
- DB on Kubernetesがてんこもり。

#### [分散ストレージCephのオーケストレータRookのデータ破壊バグを修正しました](https://blog.cybozu.io/entry/2021/01/28/065400)
- いい話。
 
#### [業界初のクラウドネイティブ専用ベアメタルコンテナプラットフォームDIAMANTIを知ろう！](https://hybridcloud.connpass.com/event/203151/)
- 来週のMeetup
- Kubernetes用のHCIであるDIAMANTIを取り上げた、国内では珍しい内容になる模様。

### @ryojsb
#### [スクリュードライバーとKubernetesを使用したデータベースのマイグレーション](https://www.verizonmedia.com/technology/blog/database-migrations-using-screwdriver-kubernetes)
- もともと、DBのマイグレーションは物理サーバー1つの上でshell scriptsを動かすところから、Screwdriverを用いてJavaアプリケーションからパッチファイルを叩くものに変更した。
- 今回は、screwdriverとCronJobを用いて、DBのマイグレーションをするようにした 
- DBの文脈におけるマイグレーションって？？
- [Screwdriver](https://screwdriver.cd/)
- [Athenz](https://www.athenz.io/)

#### [Self-Service Velero Backups with Kyverno](https://nirmata.com/2021/01/24/self-service-velero-backups-with-kyverno/)
veleroを使ってバックアップの準備をし、kyvernoのgenerate機能を用いて`nirmata.io/auto-backup: enabled`というlabelが付いたNamespaceが作成されたときに、VeleroのBackup Scheduleを作成するもの。

#### [LWKD](http://lwkd.info/2021/20210202)
- 気になったトピック
  - [Add EndPort to Network Policy](https://github.com/kubernetes/kubernetes/pull/97058)
  - [prefer nominated node](https://github.com/kubernetes/kubernetes/pull/93179)  

### @chago

#### [Nested OpenShift using OpenShift Virtualization](https://www.openshift.com/blog/nested-openshift-using-openshift-virtualization)
- OpenShift Virtualization (KubeVirt) で作成した VM で クラスタをつくる話 (by @superbrothers)
#### [KubeVirt Summit](https://community.cncf.io/events/details/cncf-kubevirt-community-presents-kubevirt-summit/#/)
- 2021年2月9日14:00 - 2021年2月10日19:00 (UTC)
- 実際のところ、どれくらい使われてるんだろうか？ (by @yosshi_)
#### [Cloud Native Computing Foundation Announces Open Policy Agent Graduation](https://www.cncf.io/announcements/2021/02/04/cloud-native-computing-foundation-announces-open-policy-agent-graduation/)

余談：話題のアプリclubhouseで「今週のKubernetes☸ 」という企画を目撃した

### @bells17

#### [Hacking Kubernetes](https://www.oreilly.com/library/view/hacking-kubernetes/9781492081722/)

Table of Contentsはこんな感じらしい
ネットワーク周り面白そう

- Preface
  - Who Should Read This Book
  - Why We Wrote This Book
  - How To Use This Book
  - Conventions Used in This Book
  - Using Code Examples
  - O’Reilly Online Learning
  - How to Contact Us
- 1. Networking
  - Defaults
  - Threat models
  - Intra-pod networking
  - Inter-pod networking
    - Traffic flow control
    - ARP-based attacks
  - No security context
  - No environmental restrictions
  - No workload identity
  - No encryption on the wire
  - Service Meshes
    - Concept
    - Options and uptake
    - Case study: mTLS with Linkerd
- 2. Container Runtime Isolation
  - Sensitive Workloads
  - What’s wrong with containers?
  - User Namespace Vulnerabilities
  - Containers, VMs, and sandboxes
  - How virtual machines work
  - Sandboxes: Mixing Containers and VMs
  - gVisor vs Firecracker vs Kata
    - gVisor
    - Firecracker
    - Kata Containers
  - rust-vmm
  - What are the risks of next gen proc iso?
  - Which Sandbox to Use?
  - Kubernetes RuntimeClass

### https://link.medium.com/LoBk7HNSCdb
