# 008

- Hosted by @bells17
- Recording date: 2021-02-05
- Video: https://youtu.be/QtHOLScNtXY
- Guest: @tzkb

## Contents

### @tzkb

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
