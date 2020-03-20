---
id: git-concept
title: 基本概念
sidebar_label: 基本概念
description: Gitの基本概念ページ
keywords:
  - Git
---

## Gitオブジェクト
`git add`や`git commit`した時に作成される、「圧縮ファイル」「ツリーファイル」「コミットファイル」といったファイルのこと。
`.git/objects`ディレクトリの下に保存される。
GitはこのGitオブジェクトをもとにスナップショットを記録していく。

### 圧縮ファイル
ファイルの中身そのものを圧縮したもの。  
正確には「**blobオブジェクト**」と呼ぶ。ファイル名はハッシュIDになる。

そのため、ファイルの中身に対して一意となるため、ファイルの中身が同じであれば`git add`しても追加で圧縮ファイルが作られることはない。（元々のファイル名の情報が残らないが、ツリーファイルに構造情報がある）

### ツリーファイル
ファイル名とファイルの中身の組み合わせ（ファイル構造）を保存するためのもので、コミットすると作成される。  
「**treeオブジェクト**」と呼ぶ。

ディレクトリの1つの階層ごとに1つのツリーファイルになっており、ツリーファイルには圧縮ファイルだけでなく、ツリーファイルも保存されている。

### コミットファイル
ファイルの変更に関して、いつ・誰が・何を・何のために変更したのかという情報を保存するためのファイル。  
「**commitオブジェクト**」と呼ぶ。

このコミットファイルに保存することで、親コミット情報を保存しているため、ここからコミットの履歴をたどることができる。そして、作成者の名前、メールアドレス、改行、コミットメッセージの保存と続く。