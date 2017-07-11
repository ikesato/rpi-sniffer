概要
====

Raspberry Pi を使った WiFi のネットワークキャプチャ用 Ansible 設定です。
一つはアクセスポイントとして動作、もう一つは WiFi クライアントとして動作させます。
ルーターとして動作するので、Raspberry Pi で tcpdump を仕掛ければ tcpdump が可能。


詳細
====

- WiFi ドングルを２つ使用  
 ドングルは wlan0, wlan1 という名前のインターフェースにする必要があります。
- 動作確認済みドングル  
 Buffalo WLI-UC-GNM
- アクセスポイント情報
  - SSID : RPi
  - パスワード : raspberry
  - files/hostapd.conf を編集することで変更可能

Ansible 使用方法
================

はじめに Raspberry Pi の eth0 の IP アドレスを 192.168.2.1 固定とします。  
そして以下で Ansible を実行で完了。

```
ansible-playbook -i hosts main.yml
```

使い方
======

1. Raspberry Pi を起動
2. Raspberry Pi の /etc/wpa_supplicant/wpa_supplicant.conf を編集し、キャプチャしたい WiFi ネットワークの SSID, password を設定
3. スマホなどキャプチャしたい端末の WiFi 設定で Raspberry Pi に接続  
 SSID : RPi, パスワード : raspberry  
 スマホで 2 のネットワークが見えていることを確認  
4. Raspberry Pi で tcpdump を仕掛ければスマホの通信内容がわかります！
