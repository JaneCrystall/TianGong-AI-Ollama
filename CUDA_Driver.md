# 在 Ubuntu 中删除所有 NVIDIA 驱动

## 1. 列出并卸载 NVIDIA 驱动

运行以下命令以列出所有 NVIDIA 驱动包：

```bash
dpkg -l | grep nvidia
```

然后使用 `apt` 或 `apt-get` 命令逐一删除这些包：

```bash
sudo apt-get purge '^nvidia-.*'
```

## 3. 删除其他相关组件

执行以下命令以删除可能安装的其他 NVIDIA 组件（例如 CUDA 工具包）：

```bash
sudo apt-get purge '*cublas*' '*cufft*' '*curand*' '*cusolver*' '*cusparse*' '*npp*' '*nvjpeg*' '*nsight*'
```

## 4. 清理残留文件

使用以下命令清理系统中的残留配置文件和依赖包：

```bash
sudo apt-get autoremove
sudo apt-get autoclean
```

## 5. 验证删除

重启系统后，可以通过以下命令来验证 NVIDIA 驱动是否已被完全卸载：

```bash
nvidia-smi
```

如果显示类似于“command not found”的错误，说明 NVIDIA 驱动已成功卸载。
