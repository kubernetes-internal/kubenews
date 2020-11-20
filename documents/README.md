# documents

## 配信周りの機器構成

![](https://github.com/kubernetes-internal/kubenews/blob/main/documents/streaming-overview.png)

Google Drawing: https://docs.google.com/drawings/d/1evvAtWzqhbcgnoeR16KrIy2iZjIO7sp1TbxTmJCB_5M/edit

- 配信用マシンは
  - OBS
  - Youtube Live管理
  - Youtube Live Chat
  - Zoom画面+音声共有
- のみ行い、配信マシンから直接Zoomの画面共有や音声共有は行わない
- 配信者含め画面共有やマイク音声などは別マシンからZoomにつないで行い、全てZoomを経由して情報を共有する
