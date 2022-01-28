---
theme: geist
---

# MelosでFlutterのmonorepo環境を構築する 
 
<div class="abs-br m-6 flex gap-2">
  <a href="https://twitter.com/0maru_dev" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-twitter />
    @0maru_dev
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# 自己紹介

<div style='display:flex'>
  <div style="width: 70%">
    <ul>
      <li>Toi Yoshimaru (@0maru_dev)</li>
      <li>
      twitter_login のメンテナ<br />
      <a href="https://github.com/0maru/twitter_login">https://github.com/0maru/twitter_login</a>
      </li>
    </ul>    
  </div>
  <div style="width: 30%">
    <img src='https://pbs.twimg.com/profile_images/1130712117445718016/7tB6uvkk_400x400.png' alt='profile'
         class="icon">
  </div>
</div>

<style>
.icon {
  width: 80px;
  height: 80px;
  border-radius: 80px;
}
</style>

---

# Melos とは


複数のFlutter プロジェクト/Dart パッケージを管理するCLIツール  
  
・ ローカルパッケージのリンクとインストール  
・ ローカルパッケージで同時にコマンドを実行する

その他諸々（特にプラグイン・ライブラリ向けの機能が多い）

<p>Melos が使用されているプロジェクト</p>
<ul>
  <li>・ FirebaseExtended/flutterfire</li>
  <li>・ fluttercommunity/plus_plugins</li>
  <li>・ rrousselGit/river_pod</li>
</ul>

<style>
  li {
    color: #099099;
  }
</style>

---

# Melos でできること

複数のFlutter プロジェクト/Dart パッケージを管理するCLIツール  

-> そもそもFlutterで複数のプロジェクトとは？？

---

# Monorepo とは？
<div grid="~ cols-2 gap-2" m="-t-2">

<div>
Flutter

</div>

<div>
複数言語

</div>

```yaml
project
  - packages/
    - app/                      # main.dart があるエントリーポイント
    - oooo_login/         # 自社のOAuth用のライブラリ
    - oooo_utils/         # よく使う処理やWidget をまとめたライブラリ
```

```yaml
project
  - typescript
    - client
    - utils
    - BFF
  - go
    - server
    - batch
  - python
    - tools
```

</div>

---

# Melos の初期設定

<p>1. Melos のインストール</p>

```shell
dart pub global activate melos
```

<p>2. Melos の構成ファイルを作成する</p>

```shell
touch melos.yaml
```

<p>3. プロジェクトに対してMelos を有効にする</p>

```shell
melos bootstrap
```
---

# Melos の構成ファイル

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

# Melos の実行方法

#### スクリプトを指定して実行する
```shell
melos run get:all
```

#### スクリプト一覧をみてから実行する
```shell
melos run

1) get:all

? Enter your choice
```
---

# Melos のオプション

#### --scope（実行対象を指定する）
```shell
melos run --scope="app" -- "flutter test"
```

#### --ignore（特定のディレクトを実行対象外にする）
```shell
melos run --ignore="*example*" -- "flutter pub get"
```

#### --flutter（Flutter に依存しているプロジェクトのみで実行する）
```shell
melos run --flutter -- "flutter run build"
```

<div class="abs-br m-6 flex flex-col gap-2">
  <a class="text-xl icon-btn opacity-50 !border-none !hover:text-white m-0 p-0"
     href="https://melos.invertase.dev/filters">
    https://melos.invertase.dev/filters
  </a>
</div>

---

# ライブコーディング


---

# まとめ



---

# おまけ

新卒・中途のエンジニア募集中です！！  

話を聞きたいなどでも大丈夫です  
気になった方はコーポレートサイトまたはTwitter のDM までお願いします！！

<div>
  <div>
    コーポレート: <a href="https://www.torico-corp.com/recruit/">https://www.torico-corp.com/recruit/</a>
  </div>
  <div>
    Twitter: <a href="https://twitter.com/0maru_dev">https://twitter.com/0maru_dev</a>
  </div>
</div>


