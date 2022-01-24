---
theme: geist
background: https://source.unsplash.com/collection/94734566/1920x1080
class: 'text-center'
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
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
      https://github.com/0maru/twitter_login
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


Melos is a CLI tool used to help manage Dart projects with multiple packages (also known as mono-repos).   
It is currently still in active development however is in use on projects such as FlutterFire.

-> 複数のFlutter プロジェクト/Dart パッケージを管理するCLIツール

<p>Melos が使用されているプロジェクト</p>
<ul>
  <li>FirebaseExtended/flutterfire</li>
  <li>fluttercommunity/plus_plugins</li>
  <li>rrousselGit/river_pod</li>
</ul>

<style>
  li {
    color: #099099;
  }
</style>

---

# Melos でできること

複数のプロジェクトを管理することができる

そもそもFlutterで複数のプロジェクトとは？？

---

# Monorepo とは？
<div grid="~ cols-2 gap-2" m="-t-2">

<div>
Flutter

</div>

<div>
複数言語

</div>

```
- project
  - packages/
    - app/                      # main.dart があるエントリーポイント
    - oooo_login/         # 自社のOAuth用のライブラリ
    - multi_payment/  # PayPay などの決済を実装したプラグイン
    - maru_utils/         # よく使う処理やWidget をまとめたライブラリ
```

```
- project
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

# Melos の使い方

<p>1. Melos のインストール</p>
<p>2. プロジェクトに対してMelos を有効にする</p>

--- 

# Melos のインストール

```
dart pub global activate melos
```

---

# 設定ファイルの作成

```
touch melos.yaml
```

#### melos.yaml
``` 
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

---

# Melos の実行方法

#### スクリプトを指定して実行する
```
melos run get:all
```

#### スクリプト一覧をみてから実行する
```
melos run

Enter your choice? 1
```
---

# Melos のオプション

#### --scope
```
melos run --scope="app" -- "flutter test -t integration_test"
```

#### --ignore
```
melos run --ignore="*example*" -- "flutter pub get"
```

#### --flutter
```
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

# 会社紹介

新卒・中途のエンジニア募集中です！！
