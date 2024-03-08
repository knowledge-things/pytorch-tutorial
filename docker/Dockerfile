# 使用 pytorch/pytorch:2.1.0-cuda11.8-cudnn8-devel 作为基础镜像
FROM pytorch/pytorch:2.1.0-cuda11.8-cudnn8-devel

# 设置工作目录
WORKDIR /workspace

# 安装必要的软件包和依赖项
RUN apt-get update && apt-get install  --no-install-recommends -y \
    python3 \
    python3-pip \
    git \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# 使用 pip 安装 JupyterLab
RUN pip install jupyterlab

COPY requirements.txt .
# 安装 Python 依赖项
RUN pip install --no-cache-dir -r requirements.txt

# 配置 JupyterLab 服务器以便通过网络访问
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--allow-root"]
