# 001

- Hosted by @chago
- Recording date: 2020-11-27
- Video: --

## Contents

### @ryojsb

- [Edge Computing with openness](https://www.cncf.io/webinars/kubernetes-in-the-context-of-on-premises-edge-and-network-edge-computing/)
  - kubeweekly 
  - 今後、ますます使い道が増えていくであろうEdge ComputingについてのKubernetes活用方の紹介
  - kubeedgeというものも増えていた。
    - [CNCF Cloud Native Interactive Landscape](https://landscape.cncf.io/)

- [kubectl logsのデフォルトコンテナを指定](https://text.superbrothers.dev/201123-allow-to-preselect-interesting-container-in-logs/)
  - [すぱぶらさん](https://twitter.com/superbrothers)による投稿
  - これまで、ずっと「kubectl logs ~ -c <container name>」
  - kubernetes 1.18から、annotationに`kubectl.kubernetes.io/default-logs-container: container name`を用いることで、-cで指定しない際のデフォルトのコンテナを選択できるようになった。

- [Chaos Engineering tools comparison](https://www.gremlin.com/community/tutorials/chaos-engineering-tools-comparison/)
  - Chaos Engineeringの比較について書かれている。
  - 明日付け足す。

### @chago

### @bells17
