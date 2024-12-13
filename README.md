# 使用说明

在华为云中打开ModelArts的Jupyter Notebook，拉取本项目代码。

```bash
git clone https://github.com/eternal-echo/SinhCustom.git
```

然后进入`SinhCustom/SinhCustom`文件夹，检查是否存在`build.sh`脚本。

```bash
cd SinhCustom/SinhCustom
ls
```

运行`build.sh`脚本。

```bash
bash build.sh
```

当命令行显示如下信息证明构建成功：

```
Self-extractable archive "custom_opp_euleros_aarch644.run" successfully created.
```

构建成功后，在算子工程目录下执行如下命令将构建成功的算子包安装到环境中：

```bash
cd build_out

./custom_opp_euleros_aarch64.run
```

显示如下信息证明安装成功：

```
Verifying archive integrity...
Uncompressing version:1.0 100%
100%
SHA256 checksums are OK. All good.
[runtime] [2024-12-13 20:26:55] [INFO] copy uninstallsh_success
[ops_custom]upgrade framework
tensorflow [runtime] [2024-12-13 20:26:55] [INFO] replaceor merge old ops framework files .g.....
[runtime] [2024-12-13 20:26:55] copy new ops framework files .....
[ops_custom]upgrade op proto
inc lib [runtime] [2024-12-13 20:26:55] [INFO] replace or mergeold ops op_proto files .g.........
[runtime] [2024-12-13 20:26:55] copy new ops op_proto files .....
[ops_custom]upgrade version.info
[runtime] [2024-12-13 20:26:55] copy new version.info filees ......
[ops_custom]upgrade op impl
ai_core [runtime] [2024-12-13 20:26:55] [INFO] replace or |merge old ops op_impl files .g....
[runtime] [2024-12-13 20:26:55] copy new ops op_impl files......
[ops_custom]upgrade op api
include lib [runtime] [2024-12-13 20:26:55] [INFO] repplace or merge old ops op_api files .g....
[runtime] [2024-12-13 20:26:55] copy new ops op_api filies .....
[runtime] [2024-12-13 20:26:55] [INFO] no need to upgrade custom.proto files
SUCCESS
```

提供的考题代码工程中，AclNNInvocation目录为Aclnn单算子API调用方式调用算子的测试工程目录，请在上述操作成功完成后进入本目录

```bash
cd ../../AclNNInvocation
```

执行入下命令进行测试（注意检查一下AclNNInvocation文件夹下是否已经有空文件夹input和output，没有就创建一个）：

```bash
bash run.sh
```

测试工程中的其它文件请勿修改。测试通过后最终屏显：

```
make[1]: Leaving directory '/home/ma-user/work/SinhCusstom/AclNNInvocation/build'
INFO: make success!
INFO: execute op!
[INFO]
[INFO]
[INFO]
[INFO]
[INFO]
[INFO]
[INFO]
[INFO]
[INFO]
[INFO]
[INFO]
[INFO]
Set device[0] success
Get RunMode[1] success
Init resource success
Set input success
Copy input[0] success
Create stream success
Synchronize stream success
Copy output[0] success
Write output success
Run op success
Reset Device success
Destory resource success
INFO: acl executable run success!
test pass
INFO: you have passed the Precision!
```