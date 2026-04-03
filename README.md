# StudyShop-Git

study git system logic &amp; flow

# Git Hands up

## 1. 準備 & 環境構築（まだの人のみ）

- Vscode もしくは Cursorをインストール
  - Vscode: https://azure.microsoft.com/ja-jp/products/visual-studio-code
  - Cursor: https://cursor.com/ja/download

### macの場合

- ローカルPC上の任意の箇所にフォルダを用意
- ターミナルを開く
- 作成したフォルダのパスへ移動
  - **cd file_path_name**

### windowsの場合

- ローカルディスク> Program Files配下に作成する
- Gitをインストール: https://git-for-windows.github.io/
- インストーラーに従って構築 ( 参考サイト: https://prog-8.com/docs/git-env-win )
- git bashを立ち上げる
- 作成したフォルダのパスへ移動
  - **cd file_path_name**

## 流れ

- cloneを行う
  - git hubの対象リポジトリにアクセス: ( https://github.com/arp-r-shimoseko/StudyShop-Git )
  - CodeボタンからURLをコピー
    - SSH設定していない方はHTTPSタブを選択してコピーボタン押下
  - 項番1で用意したターミナルcloneを実行
    - **git clone repository_URL**
- master ブランチから作業ブランチ（feature/〇〇）を切る
  - **checkout -b branch_name** or **switch -c branch_name**
- 作業ブランチ上で編集を行う
  - 任意のファイルを修正して保存(**cmd + S**)
- 変更を検知して確認する
  - **git staus**
- 変更したファイルを作業ブランチにステージングする
  - **git add file_name**
- ステージングされたファイルをcommitして履歴に登録する
  - **git commit -m 'commit_name'**
- リモートリポジトリ(git hub) に 同期する(push)
  - 初回の場合 or git configでpush先をcurrentに設定していない場合
    - **git push --set-upstream origin master**
  - 2回目以降の場合
    - **git push**

- github 上で PR を作成
  - Pull requestボタンを押下
  - New Pull requestボタンを押下
  - compare:mainのプルダウンから作成した作業ブランチを作成
  - create pull requestボタンを押下
  - タイトルと内容を記載する
  - create pull requestボタンを押下
