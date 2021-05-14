# 018

- Hosted by @bells17
- Recording date: 2021-05-14
- Video: -
- Guest: -

## Contents


### @ryojsb

#### [Kubernetes 変更内容共有会（v1.21）](https://kubernetes-updates.connpass.com/event/210969/)
- [Youtube URL](https://www.youtube.com/watch?v=JLAaX0Xg_VI&t=2304s)
- 自分的気になったポイント
  - CrossNamespacePodAffinity quota scope API
    - namespaceSelectorやnamespaceフィールドを通して指定する、cross-namespaceなPodAffinityTermのNamespaceを制限します。(#98582)
    - デフォルトのPodAffinityでは同じNamespaceに属するPodを考慮してスケジュール先を計算しますが、この機能を利用すると対象となるNamespaceを拡張できます。
  - ProbeレベルのterminationGracePeriodSecondsフィールドを追加
  - Generic Ephemeral Volumes
  ```
        volumes:
      - name: varlog
        hostPath:
          path: /var/log
      - name: scratch
        ephemeral:
          metadata:
            labels:
              type: fluentd-elasticsearch-volume
    ```
    - Allow DaemonSets to surge during update like Deployments
      - DaemonSet に MaxSurge が導入 

#### [Annotating Kubernetes Services for Humans](https://kubernetes.io/blog/2021/04/20/annotating-k8s-for-humans/?utm_medium=email&_hsmi=124457540&_hsenc=p2ANqtz-_eUQHxiNZCO_-Qm4dBkZot4mX5iIKyC8Wvv0zTZuzM3A4y7ed-gKGVThS9Lg_U88GHKfhSBqWLJNUZ7qNtFGkvzWXbng&utm_content=124457540&utm_source=hs_email)

#### [Using Finalizers to Control Deletion](https://kubernetes.io/blog/2021/05/14/using-finalizers-to-control-deletion/)
- kubectl delete
  - kubectl delete でリソースの状態は、`live` から `collected` になる。
- finallizer
  - ファイナライザは、削除前の操作を通知するリソースのキー。
  -  リソースのガベージ コレクションを制御し、リソースを削除する前に実行するクリーンアップ操作をコントローラに警告するように設計されてい

### @bells17

### @chago

#### [Tools to develop apps on Kubernetes](https://www.cncf.io/blog/2021/05/10/tools-to-develop-apps-on-kubernetes/)
#### [Explore HashiCorp Consul with Docker Compose](https://www.hashicorp.com/blog/explore-hashicorp-consul-with-docker-compose)

p.s. kubernetes novice meetup #10 お疲れ様でした！！
