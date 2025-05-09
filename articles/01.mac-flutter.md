---
title: "【Flutter】MacでFlutterの環境構築する際にパスを通したのに、not foundになった場合に確認する事"
emoji: "📚"
type: "tech"
topics:
  - "flutter"
  - "mac"
  - "環境構築"
published: true
published_at: "2023-04-09 12:27"
---

環境構築でパスを通すため　.bash_profileを編集
```
vim .bash_profile
```

以下を追加
```
export PATH="$PATH:[PATH_OF_FLUTTER_GIT_DIRECTORY]/bin"
```

パスが通っているか確認する
```
which flutter
flutter not found
```

ここでnot foundとなり、パスが通っていなかった。
原因を確認すると、自身の環境がzshになっていることが原因でした。
※追記　
.bash_profileの変わりに以下でも可能
```
vim .zshrc
```
※mac OS Catalinaからデフォルトがbashからzshに変更されている

現在の環境確認
```
echo $SHELL
/bin/zsh
```

変更可能なSHELL
```
cat /etc/shells
# List of acceptable shells for chpass(1).
# Ftpd will not allow users to connect who are not using
# one of these shells.

/bin/bash
/bin/csh
/bin/dash
/bin/ksh
/bin/sh
/bin/tcsh
/bin/zsh
```

bashに変更
※変更時にPCのパスワードを求められるので入力
```
chsh -s /bin/bash
```

ターミナルを再起動して改めて現在の環境を確認
```
echo $SHELL
/bin/bash
```

パスを設定し直して通っていることを確認
```
which flutter
[PATH_OF_FLUTTER_GIT_DIRECTORY]/bin/flutter
```

