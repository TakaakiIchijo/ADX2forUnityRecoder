# ADX2 for Unity Recorder
ADX2 for Unityで再生中の音を録音するエディタ拡張

![ADX2UnityRecoder](ADX2UnityRecoder.png)

## 動作確認環境
Unity 2019.3.1f1 + ADX2 LE SDK 2.10.05

Unity 2018.4.13f1 + ADX2 (CRIWARE SDK for Unity 3.00.04)

## エディタでの使用方法
Window/CRIWARE/CriAtomRecorderからツールウィンドウを呼び出すことができます。
ゲームを再生開始し、任意のタイミングで「Start Recording」ボタンを押してください。

### Unity Recorderとの連携方法
Unity Recorderは機能拡張が許可されていない(継承したいクラスがintarnal）ため、Recorderの動画キャプチャイベントをフックして、同時に音声をwaveファイル出力する機能を作りました。

1. CriAtomRecorderEditorWindow.csのOnEnableメソッドのコメントアウトを外す
2. CriAtomRecorderウィンドウを開き直す
3. Unity Recorderも一緒に起動するのでゲームを再生開始する
4. 任意のタイミングでUnity Recorder側の録画開始ボタンを押す
5. 任意のタイミングでUnity Recorder側の録画停止ボタンを押す

## ランタイムでの使用方法
CriAtomRecorder.csを任意のゲームオブジェクトにアタッチし、録音したいタイミングでStartRecordメソッドを叩いてください。その際はプラットフォームごとの保存可能ファイルパスを指定して渡す必要があります。

/Sampleに日付時刻を入れたwavファイルをApplication.persistentDataPathに保存するサンプルを用意しています。このスクリプトを適当なゲームオブジェクトにアタッチし、OnRecordStartメソッドをボタンイベントなどにアサインすることで、録音をかんたんにテストできます。

## 今後のアップデート
- Unity Recorderが拡張可能になったら対応
- 出力されたwavをどうにかしてmp4とくっつける方法を探す
