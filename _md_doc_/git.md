# git

## ファイル保存領域
ローカル
  git add
ステージングエリア
  git commit
リポジトリ(ローカル)
  git push
リポジトリ(リモート)

## 共有リポジトリ(リモート)初期化
git init --bare

## ローカルリポジトリ初期化
git init

## 設定ファイル

local 該当リポジトリ
repository/.git/config

global 該当ユーザーの全リポジトリ
~/.gitconfig

system システム全体 全ユーザー
/etc/gitconfig

## ユーザー名/E-mail指定

該当リポジトリに適用
git config --local user.name auser
git config --local user.email auser@gmail.com

該当ユーザーの全リポジトリ に適用
git config --global user.name chomo
git config --global user.email chomo@gmail.com

システム全体 全ユーザー
git config --global user.name chomo
git config --global user.email chomo@gmail.com


## 共有リポジトリ追加
git remote add origin /d/develop/git_practice/share_repo/

origin は任意
Pathはリモートリポジトリの場所

以下で確認
git config -l
remote.origin.url=D:/develop/git_practice/share_repo/

origin はリモートリポジトリの別名となる
現在の値は以下で確認可能
git remote get-url origin

## 無視するファイルの指定
以下に記載する
./gitignore



# ブランチ種類
作業ブランチ

追跡ブランチ











## 直前のcommitを修正する
git commit --amend

## addを取り消し 直前の状態に戻す
git reset --hard HEAD

## commit済みのものを一つ戻す
git reset --hard HEAD^

## id指定で取得
git reset --hard (id 最低7桁)

## 先の操作を1つだけ取り消す
git reset --hard ORIG_HEAD

## ローカルの変更を破棄
git checkout (filename)
git checkout .

## ブランチ確認
git branch

## ブランチ作成
git branch hoge

## ブランチ切り替え
git checkout hoge

## ブランチ作成＆切り替え
git checkout -b hoge

## ブランチのマージ／リベース
マージ先にchekcoutで切り替えてマージ対象(取り込みたい)のブランチを指定
git merge hoge
指定したブランチがHEADの指しているブランチに取り込まれます

merge後の操作
git add
git commit

リベース先にchekcoutで切り替えてリベース対象(取り込みたい)のブランチを指定
git rebase hoge

merge も rebase も checkout中のブランチに指定したブランチを統合するのは同じ

master
 - issue2
 - issue3

master からのブランチ issue2 と issue3 があり、
issue2 と issue3 の内容をmaster に取り込みたいとする。

merge は マージ先(master)にてマージ操作して、コミット操作する。issue2 と issue3 のコミットが記録され、更にissue2とissue3をマージした時のコミットも記録される
rebase は マージ元(issue3)にマージ先(master)のコミットを取り込んでから、マージ先(master)にて、merge(fast-forword)する。
よって、issue2とissue3をマージした時のコミット は記録されない


## pull と fetch

pull は リモートリポジトリから取り込み
pull は fetch + marge を行っている


## ブランチの削除
git branch -d develop

## タグの作成 直近のcommitにタグを付ける
git tag v1.0
git tag v1.0 (id 最低7桁)

## タグの削除
git tag -d (tag名)

## タグの修正内容を確認する
git show v1.0

## エイリアス
git config --global alias.co checkout
git config --global alias.st status

## エイリアス確認
git config -l

## リポジトリ登録
git remote add origin ~/share_repo.git

## リポジトリ登録削除
git remote rm origin

## 設定パラメータ確認
git config -l
  登録リポジトリ確認
  remote.origin.url=..\share_repo.git\

  Commitエディタ確認
  core.editor="d:\\Program Files\\Microsoft VS Code\\Code.exe" --wait


## 共有リポジトリへ入れる
git push origin master

## 共有リポジトリの中身を共有する(取得する)
git clone ./share_repo.git work2

## 共有リポジトリより取得
git pull origin master







# tortoisegit

https://tortoisegit.org/download/

日本語化 Language Packs を入れる
設定から言語設定












# エラー

> git.exe push --progress "origin" master:master
> To D:/develop/git_practice/local_repo_buser/../share_repo/
> ! [rejected]        master -> master (fetch first)
> error: failed to push some refs to 'D:/develop/git_practice/local_repo_buser/../share_repo/'
> hint: Updates were rejected because the remote contains work that you do
> hint: not have locally. This is usually caused by another repository pushing
> hint: to the same ref. You may want to first integrate the remote changes
> hint: (e.g., 'git pull ...') before pushing again.
> hint: See the 'Note about fast-forwards' in 'git push --help' for details.
