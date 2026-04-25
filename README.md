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
  - **cd file_path_name** </br>
```
例)

TaroYamada@TaroYamada ~ % cd dev
TaroYamada@TaroYamada dev % 

↑のように指定したフォルダパスに移動できていればOK
```

### windowsの場合

- ローカルディスク> Program Files配下に作成する
- Gitをインストール: https://git-for-windows.github.io/
- インストーラーに従って構築 ( 参考サイト: https://prog-8.com/docs/git-env-win )
- git bashを立ち上げる
- 作成したフォルダのパスへ移動
  - **cd file_path_name** </br>
```
例)

TaroYamada@TaroYamada ~ % cd dev
TaroYamada@TaroYamada dev % 

↑のように指定したフォルダパスに移動できていればOK
```

## 初回の流れ
- cloneを行う
  - git hubの対象リポジトリにアクセス: ( https://github.com/arp-r-shimoseko/StudyShop-Git )
  - CodeボタンからURLをコピー
    - SSH設定していない方はHTTPSタブを選択してコピーボタン押下
  - CLIからダウンロードしたいフォルダに移動 </br>
  ( macはターミナル、windowsはgit bash等、IDEのターミナルからでも可能 ) <br>
  ( 今回初回構築した方は項番1で)
    - **cd donload_folder_path**
    - **git clone repository_URL**

## 基本の流れ
- 親ブランチ(main,master,develop等)から作業ブランチ（feature/〇〇）を切る
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
  - 作成したブランチから初回pushの場合
    - **git push --set-upstream origin main** ( ローカルブランチをリモートに接続 )
  - git configでpush先をcurrentに設定している場合
    - **git push**
  - 同じブランチで2回目以降の場合
    - **git push**
- github 上で PR を作成
  - Pull requestボタンを押下
  - New Pull requestボタンを押下
  - compare:mainのプルダウンから作成した作業ブランチを作成
  - create pull requestボタンを押下
  - タイトルと内容を記載する
  - create pull requestボタンを押下

## コミットを取り消すを実践
- commitを用意する
  - どこかのファイルを修正
  - git commit -m '取り消し実践'
- git reset --soft HEAD~1

## push済みのコミットを取り消す実践
- commitを用意する
  - どこかのファイルを修正
  - git status
  - git add ファイル名
  - git commit -m '取り消し実践'
- git pushを実行
- git hub側にcommitがpushされたことを確認
- ローカルでgit revert commit_idを実行
- git push
- git hubでrevert commitがpushされたことを確認

## コンフリクトを出して修正するを実践
- mainに移動して最新化
  - git checkout main
  - git fetch origin main
  - git merge origin main
- ブランチを作成A & 移動
  - git checkout -b feature-A (git switch -c feature-A)
- commitを用意する
  - どこかのファイルを修正
  - git status
  - git add ファイル名
  - git commit -m '取り消し実践'
 
- mainに移動(最新化はしない)
  - git checkout main
- ブランチBを作成 & 移動
  - git checkout -b feature-B (git switch -c feature-B)
- commitを用意する
  - ブランチBと同じ箇所を修正
  - git status
  - git add ファイル名
  - git commit -m '取り消し実践'
- コンフリクトを発生させる
  - git checkout feature-A
  - git merge feature-B
- 正しい修正にしてコミットする
- コンフリクト解除を辞める場合
  - git merge --abort


## その他コマンド
- 変更差分を確認したい
  - git diff
- 対象ブランチとの差変更差分を比較したい
  - git diff main..feature
- 履歴を確認したい
  - git log --oneline
- 履歴やブランチ構造を確認したい
  - git log --oneline --graph --decorate --all
- commit履歴の詳細を調べたい
  - git reflog
- 誰の変更か確認したい
  - git blame false_name
- ブランチを削除したい
  - git branch -D branch_name
- push済みのcommitを取り消したい
  - git revert commit_id
- push前のコミットを取り消したい
  - git reset HEAD~コミットのHEAD番号
- 一時退避させたい(stashよりcommit + reset HEAD推奨)
  - git stash
- 一時退避させた内容を戻したい
  - git stash apply
- 一時退避させた内容戻す + 退避履歴から削除
  - git stash pop
- 退避履歴の確認
  - git stash list
- 退避リストから復元
  - git stash apply stash@{listの番号}
- 強制的にリモートの状態にする（危険 = 作業は全て消えます）
  - git reset --hard origin/main


  ### 斎藤さんおすすめコマンド
  - リモートのブランチを消す
  - git push origin :任意のリモートのブランチ名

  - 今のブランチにmerge済みのブランチを調べる
  - git branch -a --merged
  
  - ブランチ削除
  - git branch -d branch_name
  - git branch -D branch_name
