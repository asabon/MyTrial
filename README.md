# Workflows

## Overview

GitHub Actions を使って自分で実現したことを、せっかくなので共有します。
どなたかのお役に立てたらうれしいです。

## Requirements

特になし

## Usage

.github/workflows 以下に置いてある yml ファイルを参考に、自分の環境の導入してください。

## Features

### (change-param-branch.yml)

[![Change param branch](https://github.com/asabon/Workflows/actions/workflows/change-param-branch.yml/badge.svg?branch=main)](https://github.com/asabon/Workflows/actions/workflows/change-param-branch.yml)


### Doxyfile生成 (gen-doxyfile.yml)

[![Generate Doxyfile](https://github.com/asabon/Workflows/actions/workflows/gen-doxyfile.yml/badge.svg?branch=main)](https://github.com/asabon/Workflows/actions/workflows/gen-doxyfile.yml)

- 目的と背景
  - GitHub リポジトリ内のソースコードを Doxygen でドキュメントにしたい
  - Doxygen の実行も GitHub Actions で行わせる予定のため Doxygen はローカル PC にはインストール不要
  - 不要なものを自分の PC にインストールしたくない
  - だが Doxygen を実行するためには設定ファイル (Doxyfile) が必要
  - Doxyfile は Doxygen を実行して生成可能
  - このためだけに Doxygen を自分の PC にインストールしたくない
  - Doxyfile の生成も GitHub Actions でやらせてしまおう！
- この yml でやっていること
  - Doxygen を使うときに必要な Doxyfile を生成し、アップロードする

### push-to-other-repo.yml

[![Push to other repository](https://github.com/asabon/Workflows/actions/workflows/push-to-other-repo.yml/badge.svg?branch=main)](https://github.com/asabon/Workflows/actions/workflows/push-to-other-repo.yml)

- 目的と背景
  - GitHub Actions でリポジトリ内のソースコードからドキュメントを生成し、生成されたドキュメントを GitHub Pages で公開したい
  - ソースコード用のリポジトリから生成されたドキュメントを GitHub 公開用のリポジトリに push したい
- この yml でやっていること
  - Source リポジトリ (asabon/Workflows) をチェックアウト
  - Destination リポジトリ (asabon/Sandbox) をチェックアウト
  - Destination リポジトリ内のファイルを更新
  - Destination リポジトリを commit, push
- 注意点
  - この yml は Source リポジトリで動作する
  - リポジトリをまたいで push する際に認証が必要
    - Destination リポジトリに push するときに使う秘密鍵を Source リポジトリに登録する
      - この yml では SSH_PRIVATE_KEY として登録してある前提
    - 対応する公開鍵を Destination の Deploy Key として登録してある前提

### ssh-keygen.yml

[![ssh-keygen](https://github.com/asabon/Workflows/actions/workflows/ssh-keygen.yml/badge.svg?branch=main)](https://github.com/asabon/Workflows/actions/workflows/ssh-keygen.yml)

- 目的と背景
  - 認証用の鍵を作りたい
  - ssh-keygen を Linux で実行したいが Linux マシンを持っていない
  - 普段あまり使わないのでセットアップが面倒
  - GitHub Actions の Linux 環境で ssh-keygen を実行しよう！
- この yml でやっていること
  - パラメータを受け取り ssh-keygen を実行
  - 生成された鍵のペアをアップロード
- 注意点
  - 秘密鍵をアップロードしているのでセキュリティ的によろしくはないかも
    - 成果物をダウンロードしたら直ちに削除するなどした方がよいと思う

## Reference

## Author

## License

This project is licensed under the MIT License, see the LICENSE file for details.
