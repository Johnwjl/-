# git 相关的报错及解决
### git clone 的时候遇到报错 'fatal: destination path 'xxx' already exists and is not an empty directory.'
- 解决：已经有这个命名的文件夹了，删掉重新命名一个新的名称的文件夹，再git clone就行了
### git clone 的时候遇到报错 'fatal: unable to access 'https://github.com/xxx/xxx.git/': Failed to connect to github.com port 443: Timed out'
- 解决：git端口被shadowsocks占用了，手动配置git的代理。git命令行输入如下两个命令就可以了：
```
git config --global http.proxy http://127.0.0.1:1080

git config --global https.proxy http://127.0.0.1:1080
```
