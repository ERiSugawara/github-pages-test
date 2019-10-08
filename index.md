GitHub PagesによるHTMLドキュメント
================================

<style>
svg {
    border: 1px solid #000;
}
</style>

# 概要

この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。

## 他ページへのリンク

* [doc1](./doc1.html)
* [doc2](./sub/doc2.html)

# 解説

この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。

```plantuml
@startuml テスト用クラス図

left to right direction

class MainActivity <<EntryPoint>> {
    + onCreate()
    + onStart()
    + onStop()
    + onDestroy()
}

class MainViewModel {
    + onStart()
    + onStop()
}

class BeaconScanner #dbf9ff {
    + スキャン開始(): Observable<Beacon>
}

class Beacon <<DataClass>> #dbf9ff {
    + BDアドレス: String
    + RSSI: Int
    + データ: ByteArray
}

MainActivity --> "1" MainViewModel
MainViewModel --> "1" BeaconScanner
BeaconScanner .r.> Beacon: <<create>>

MainViewModel --> "*" Beacon: 一定時間内の受信結果リスト

@enduml
```


```plantuml
@startuml テスト用シーケンス図

hide footbox

participant ": MainActivity" as MainActivity
participant ": MainViewModel" as MainViewModel
participant ": Subject<Beacon>" as BeaconSubject #dbf9ff
participant ": BeaconScanner" as BeaconScanner #dbf9ff
participant " : Beacon" as Beacon <<DataClass>> #dbf9ff

[-> MainActivity: onStart()
activate MainActivity
MainActivity -> MainViewModel: onStart()
activate MainViewModel
MainViewModel -> BeaconScanner: スキャン開始()
activate BeaconScanner
BeaconScanner ->]: BLEスキャン開始API
create BeaconSubject
BeaconScanner -> BeaconSubject: <<create>>

return Observable<Beacon>

MainViewModel -> BeaconSubject: susbscribe()
activate BeaconSubject

deactivate MainViewModel
deactivate MainActivity

...

alt BLEアドバタイズ受信時

BeaconScanner <-]: BLE受信結果
activate BeaconScanner #2bdcff

alt 対応ビーコンからのデータ
create Beacon
BeaconScanner -> Beacon: <<create>>
activate Beacon #2bdcff
return

BeaconScanner -> BeaconSubject: onNext(生成したBeacon)
activate BeaconSubject #2bdcff
BeaconSubject -> MainViewModel: onNext(...)
activate MainViewModel #2bdcff
deactivate MainViewModel
deactivate BeaconScanner
deactivate BeaconSubject

end
end

...

[-> MainActivity: onStop()
activate MainActivity
MainActivity -> MainViewModel: onStop()
activate MainViewModel
MainViewModel -> BeaconSubject: dispose()
activate BeaconSubject
BeaconSubject -> BeaconScanner: onDispose()
activate BeaconScanner
BeaconScanner ->]: BLEスキャン停止API
deactivate BeaconSubject
destroy BeaconSubject

deactivate MainViewModel
deactivate MainActivity

@enduml
```

この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。

この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。

この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。この文章はダミーです。文字の大きさ、量、字間、行間等を確認するために入れています。
