# 记录在 Deepin Linux 中安装 Nix 包管理器：

1. 安装：
    - ```sh <(curl -L https://nixos.org/nix/install) --daemon```
    - 提示的安装注意事项：
        - 不能在已有 Nix 包管理的系统中再安装 Nix 包管理器，如果你安装了，脚本会指导你如何卸载老版本；
        - 安装过程会提示安装到哪个目录，并会询问是否继续；
        - 会为 Nix 包管理器守护进程创建系统用户和组；
        - 推荐 Nix 文件守护进程基础安装；
        - 配置 shell 导入 Nix 特定配置文件，以方便直接使用；
        - 启动 Nix 守护进程。
    - 安装前提示：
        - 再次提示是否之前安装过，安装过就会清理掉；
        - 创建本地用户；
        - 创建目录，在 ```/nix``` 目录下；
        - 配置文件存放在 ```/etc/nix``` 目录下；
        - 设置默认的配置文件，由 Nix 相关文件创建，存放在 ```/root``` 目录下；
        - 加载并启动 Nix 相关服务，分别是：```/etc/systemd/system/nix-daemon.service``` ， ```/etc/systemd/system/nix-daemon.socket``` 。
    - sudo 提问：默认安装将需要用 sudo 权限；如果使用 root 权限运行脚本，将会退出脚本提示请使用
    - ```sudo test -e /root/.nix-channels```
    - ```sudo test -e /root/.nix-profile```
2. 使用：
    - 检查是否安装成功：```nix-env --version```；
    - 使用 ```nix-channel``` 命令，添加，列出，更新源；
    - 使用 ```nix-env -qa``` 命令所有包；
    - 使用 ```nix-env -qa firefox``` 列出所有包含 firefox 的包；
3. 完成测试。