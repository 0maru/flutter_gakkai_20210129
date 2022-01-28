# LT
発表時間15分

- 1分 自己紹介・twitter_loginの紹介
- 1分 Melos について
    - そもそもmelosとは？
    - どういうのに使われているか
    - できること
- 3分 Melos の使い方
    - 初期化
    - yaml の書き方
    - 実行方法
    - envやignoreなどのオプションについて
    - 引数と標準入力は使えない
    - 標準入力が必要な時はDartでスクリプトを書いている
    - バージョン番号の更新はDartのスクリプトでやってる
- 5分 ライブコーディング（モノレポ、どうやって使ってるかを実演）
    - アプリ作ってディレクトリ移動させる
    - プラグインとライブラリを作ってモノレポで管理する
    - melosでビルドする
    - grinder を組み合わせる
    - Grinder を組み合わせる理由はGrinder だとDartてスクリプトが書けるから
    - melos だけだとパイプで渡す必要があり長いタスクを実行するのが困難
    - 2分 プラグインでの使い方
    - platform_interface
    - versionup
    - コミットログ
1分 まとめ、会社の紹介
 - 社員募集中です

 ---

# 2.設定ファイルの作成

```shell
touch melos.yaml
```

#### melos.yaml
``` yaml
name: flutter_monorepo_project
packages:
  - "*"
  - "packages/**"

scripts:
  get:all:
    run: |
      melos exec -c 1 -- \
        "flutter pub get"
```

<div class="abs-br m-6 flex flex-col gap-2">
  <a class="text-xl icon-btn opacity-50 !border-none !hover:text-white m-0 p-0"
     href="https://melos.invertase.dev/configuration/overview">
    https://melos.invertase.dev/configuration/overview
  </a>
</div>

---

# 3. Melos を有効にする

```shell
melos bootstrap
```

---