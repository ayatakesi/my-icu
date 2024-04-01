# libicuuc
GNU Emacs30.0.50に含まれる`java/INSTALL`にしたがってパッチを適用したlibicuucモジュール(libxml2の依存モジュール)のレポジトリ。

# 作成した手順
1. [Google Gitのicu](https://android.googlesource.com/platform/external/icu)をcloneして`nougat-release`をcloneしようとしたけどあまりにサイズが大きいので、それに相当する書庫を取得


```bash
$: wget https://android.googlesource.com/platform/external/icu/+archive/refs/heads/nougat-release.tar.gz
$: mkdir icu; cd icu; tar xvfz ../nougat-release.tar.gz
```

2. gitレポジトリとして初期化、初期状態をcommitしてから修正用ブランチ`my/master`をcheckout

```bash
$: git init
$: git add -A
$: git commit -m '1st. commit'
$: git checkout -b my/master
```

3. `java/INSTALL`にしたがいpatchを適用

```bash
$: patch -p1 < PATCH_FOR_ICU.patch
```

4. 上記patch ファイルとpatch適用後ファイルをcommitして空レポジトリにpush

```bash
$: git add -A
$: git commit -m 'nanika commit messages...'
$: gh repo create my-icu --public
$: git remote add mine https://github.com/JIBUN/my-icu.git
$: git branch -M my/master
$: git push -u mine my/master
```
