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

### @bells17

### @chago

#### [Tools to develop apps on Kubernetes(https://www.cncf.io/blog/2021/05/10/tools-to-develop-apps-on-kubernetes/)
