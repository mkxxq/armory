## 解决 `Conda activation in terminal with fish doesn't work`

在pycharm的`fish-integration.fish`, 

在mac下具体目录为: `~/Applications/PyCharm\ Professional\ Edition.app/Contents/plugins/terminal/shell-integrations/fish/fish-integration.fish`

找到以下内容(在文件开头):
```bash
if test -n "$JEDITERM_SOURCE"
  source "$JEDITERM_SOURCE"
  set -e JEDITERM_SOURCE
end
```
替换为以下内容:
```
if test -n "$JEDITERM_SOURCE"
  eval {$_CONDA_EXE} "shell.fish" activate {$JEDITERM_SOURCE_ARGS} | source
  set -e JEDITERM_SOURCE
end
```

> 参考链接: `https://youtrack.jetbrains.com/issue/PY-25644/Conda-activation-in-terminal-with-fish-doesnt-work`
