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
- finalizer
  - ファイナライザは、削除前の操作を通知するリソースのキー。
  - リソースのガベージ コレクションを制御し、リソースを削除する前に実行するクリーンアップ操作をコントローラに警告するように設計されている。
  - finalizerを含ませたリソースを作成して削除しようとすると、消えない。
    - Kubernetes がオブジェクトにファイナライザーが含まれていることを確認し、読み取り専用の状態にしたから。
    ```
    cat <<EOF | kubectl create -f -
    apiVersion: v1
    kind: ConfigMap
    metadata:
      name: mymap
      finalizers:
      - kubernetes
    EOF
    ```
  - finalizerを含むリソースに関しては、kubectl delete でリソースの状態は、`live` から `finalizaiton` になり、finalizer keyを取り除くことで、`deletion` というステータスになる。
  ```
  kubectl patch configmap/mymap \
    --type json \
    --patch='[ { "op": "remove", "path": "/metadata/finalizers" } ]'
  ```
  - したがって、ファイナライザーを持つオブジェクトを削除しようとすると、コントローラがファイナライザーキーを削除するか、または Kubectl を使用してファイナライザーが削除されるまで、ファイナライズのままになります。ファイナライザーリストが空になると、オブジェクトは Kubernetes によって実際に再利用され、キューに入れ、レジストリから削除されます。
- 所有者
  - 親オブジェクトを最初に作成し、次に子オブジェクトを作成すると、子を消しても親は消えないが、親を消すと子も消える。
  ```
  cat <<EOF | kubectl create -f -
  apiVersion: v1
  kind: ConfigMap
  metadata:
    name: mymap-parent
  EOF
  CM_UID=$(kubectl get configmap mymap-parent -o jsonpath="{.metadata.uid}")

  cat <<EOF | kubectl create -f -
  apiVersion: v1
  kind: ConfigMap
  metadata:
    name: mymap-child
    ownerReferences:
    - apiVersion: v1
      kind: ConfigMap
      name: mymap-parent
      uid: $CM_UID
  EOF
  ```
  - `--cascade=false` を渡してあげると、親を消しても子は消えない。
  ```
  kubectl delete --cascade=false configmap/mymap-parent
  configmap "mymap-parent" deleted

  kubectl get configmap
  NAME          DATA   AGE
  mymap-child   0      13m21s
  ```
- namespaceの強制終了
  - namespaceを削除し、その下にあるすべてのオブジェクトを削除しても、その名前空間がまだ存在することがある。(Terminationの状態で残り続ける)
  ```
  # kubectl get ns test-ns -o json > delete.json
  # vi delete.json
  {
      "apiVersion": "v1",
      "kind": "Namespace",
      "metadata": {
          "annotations": {
          ...
          "name": "test-ns",
          ...
      },
      "spec": {
          "finalizers": [
              "kubernetes"
          ]
      },
      "status": {
          "phase": "Terminating"
      }
  }
  ```
  - spec.finalizersを消して、APIに渡すと強制的に消せる。
  ```
  # kubectl proxy &
  # curl -H "Content-Type: application/json" -X PUT --data-binary @delete.json http://127.0.0.1:8001/api/v1/namespaces/<ns>/finalize
  ```


### @bells17

### @chago

#### [Tools to develop apps on Kubernetes](https://www.cncf.io/blog/2021/05/10/tools-to-develop-apps-on-kubernetes/)
#### [Explore HashiCorp Consul with Docker Compose](https://www.hashicorp.com/blog/explore-hashicorp-consul-with-docker-compose)

p.s. kubernetes novice meetup #10 お疲れ様でした！！
