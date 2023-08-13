# 病毒吧官方网站

## 本地构建

网站使用了 [cofess/hexo-theme-pure](https://github.com/cofess/hexo-theme-pure) 主题。由于该主题通过 `git clone` 进行安装，故使用 git submodule 对其进行管理。在本地构建预览时，若出现警告 `WARN  No layout: index.html`，请执行：

```sh
$ git submodule init
$ git submodule update
```

克隆该主题仓库后继续。
