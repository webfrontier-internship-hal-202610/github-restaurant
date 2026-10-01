# GitHub Restaurant

レストランを題材にGit、GitHubの練習をするためのリポジトリです。

## 役割
- 客
  - 料理をオーダーする
  - 料理を受け取る

- コック(複数名を想定)
  - オーダーを受ける
  - 調理をする
  - 料理を出す

## 作業フロー
[GitHub フロー](https://docs.github.com/ja/get-started/quickstart/github-flow)を使用します。


## 0.オーダーを作成する
客役が行う作業

[オーダー](order.md)に基づき以下の手順を行う。

1. GitHubでIssue（イシュー）を立てる(作成する)
2. Issueに注文したい料理名を書く
3. コックにIssueを割り当てる
4. 上記をコック分行う

## 1.オーダーを受ける
コック役が行う作業

### 1−1.割り当てられたIssueを確認する

割り当てられたIssueにコメントを書く

### 1−2.作業ブランチを作成する

ローカルでmainブランチから作業ブランチを作成する

```sh
$git switch -c <作業ブランチ名>
```

ブランチ名のルール：
>**order-[number]-[menu-name]**

例：

1回目のオーダーでカレーライスの場合
>order-1-curry_rice

2回目のオーダー、牛丼の場合
>order-2-beef_bowl

3回目のオーダーでポテトサラダの場合
>order-3-potato_salad

リモートリポジトリに作業ブランチをpushする

```sh
$git push origin <作業ブランチ名>
```

## 2.調理する
コック役が行う作業

### 2−1.foodstuff.mdの表を編集する
メニューを調理するのに必要な食材の在庫数を変更する

例：

カレーライスの場合
>肉、玉ねぎ、じゃがいも、にんじんの在庫数からそれぞれ１減らす

牛丼の場合
>肉、玉ねぎの在庫数からそれぞれ１減らす

ポテトサラダの場合
>玉ねぎ、じゃがいも、にんじんの在庫数からそれぞれ１減らす

### 2-2.作業ブランチにコミットする

作業ブランチに1つ目のコミットを作成する

```sh
$git add restaurant/foodstuff.md
$git commit -m <コメント>
```

### 2-3.dish.mdの表を編集する

調理したメニューの調理数を増やす

### 2-4.作業ブランチにコミットする

作業ブランチに2つ目のコミットを作成する


```sh
$git add restaurant/dish.md
$git commit -m <コメント>
```

### 2-5.作業ブランチをリモートリポジトリにpushする

作業ブランチをリモートリポジトリにpushする

```sh
$git push origin <作業ブランチ名>
```

## 3.料理を出す
コック役が行う作業

1. GitHub上でPull Request(PR/プルリクエスト)を作成する
2. Assigneesに自分を設定する
3. Reviewersに客を設定する
4. DevelopmentにIssueを紐付ける

## 4.料理を受け取る
客役が行う作業

1. GitHub上でPull Requestを確認する
2. コンフリクトが発生しているか確認する
3. Pull Requestの内容をレビューする

## コンフリクトが発生した場合
コック役が行う作業

1. リモートリポジトリの変更をfetchする
```sh
$git fetch origin main
```
2. ローカルのmainブランチにmergeする
```sh
$git switch main
$git merge origin/main
```
3. ローカルのmainブランチからローカルの作業ブランチにmergeする
```sh
$git switch <作業ブランチ名>
$git merge main
```
4. コンフリクトを解決する

```sh
※コンフリクトした箇所を修正

$git add <修正したファイル>
$git commit -m <コメント>
$git push origin　<作業ブランチ名>
```

5. ローカルの作業ブランチをリモートの作業ブランチにpushする
```sh
$git push origin　<作業ブランチ名>
```
6. Pull Requestを修正する

## 4.参考

### ブランチ戦略
- [GitHub Flow](https://docs.github.com/ja/get-started/quickstart/github-flow)
- [git flowとgithub flow　開発運用方法の違い](https://qiita.com/Yu-kiFujiwara/items/40b503683d6525c8d274)

### リポジトリ戦略
- [モノレポ入門](https://zenn.dev/anneau/articles/4c9beff9645af7)
- [モノレポについて.md](https://gist.github.com/pipopotamasu/efe7097454d9668f80cd8b43068afafc)

### GitHub Issue/Pull Request
- [GitHubで課題を管理する便利機能Issueとその作成方法](https://tonari-it.com/github-issue/)
- [GitHubでIssueについて解決してクローズするまでの手順](https://tonari-it.com/github-issue-close/)
- [Pull RequestをIssueにリンクする](https://docs.github.com/ja/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)

### Git操作
- [The Official GitHub Training Manual](https://githubtraining.github.io/training-manual/#/ja/)
- [GitHub GITチートシート](https://training.github.com/downloads/ja/github-git-cheat-sheet.pdf)
