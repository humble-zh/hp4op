把下面这行

```bash
src-git hp4op https://github.com/humble-zh/hp4op.git
```

追加到 feeds.conf.default 里面，然后执行

```bash
./scripts/feeds update hp4op
./scripts/feeds install -a
make menuconfig
    #find and select the package you want to build.
```
