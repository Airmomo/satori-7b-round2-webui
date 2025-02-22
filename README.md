# Satori-7B-Round2-WebUI

`Satori-7B-Round2` 模型参数量仅 7B 就在数学推理能力上超越 70B 和一众小型模型，MIT与哈佛基于`行动-思维链（COAT）`机制训练的 Satori-7B-Round2 推理模型。

本项目基于 Satori-7B-Round2 推理模型和 Gradio API 提供了一个友好的 Web UI，方便快速部署实例后立即体验 Satori-7B-Round2 模型的推理能力。

## Satori-7B-Round2 是什么

Satori-7B-Round2 是由**MIT、哈佛大学**等机构研究者推出的 7B 参数大型语言模型，专注于提升推理能力。基于 Qwen-2.5-Math-7B，Satori 通过小规模的格式微调和大规模的增强学习实现了先进的推理性能。

该模型引入了行动-思维链（COAT）机制，通过特殊的元动作标记引导模型进行推理。Satori 在数学推理和跨领域任务中表现出色，展现了优异的泛化能力。

### Satori-7B-Round2 的核心功能

- 自回归搜索能力：Satori 通过自我反思和探索新策略，能进行自回归搜索，无需外部指导即可完成复杂的推理任务。
- 数学推理：Satori 在数学推理基准测试中取得了最佳成绩，展现出卓越的推理能力。
- 跨领域任务：除了数学领域，Satori 在逻辑推理、代码推理、常识推理和表格推理等跨领域任务中也表现出色，具有很强的泛化能力。
- 自我反思与纠错能力：Satori 在推理过程中能自我反思并进行自我纠错，提升了推理的准确率。
- 强化学习优化：采用行动-思维链（COAT）机制和两阶段训练框架，包括小规模格式调优和大规模自我优化，主要依靠强化学习（RL）实现先进的推理性能。

### Satori-7B-Round2 的技术原理 —— COAT

![Satori](https://s2.loli.net/2025/02/11/mUiAHC4s8yql51z.png)

- **行动-思维链（COAT）推理**：
  - **继续推理**（<|continue|>）：鼓励模型生成下一个中间步骤。
  - **反思**（<|reflect|>）：验证之前的推理步骤是否正确。
  - **探索替代方案**（<|explore|>）：识别推理中的漏洞并探索新的解决方案。

- **两阶段训练框架**：
  - **小规模格式调优阶段**：在少量推理轨迹示例的小数据集上进行微调，使模型熟悉 COAT 推理格式。
  - **大规模自我优化阶段**：通过强化学习（RL）优化模型性能，采用重启与探索（RAE）技术，提升模型的自回归搜索能力。

### Satori-7B-Round2 的数学推理能力基准

在数学推理中，Satori-7B-Round2 的表现已达到 SOTA 性能，并优于使用相同基础模型（Qwen-2.5-Math-7B）的 Qwen-2.5-Math-7B-Instruct。甚至大幅度超越了 Llama-3.1-70B-Instruct 这个参数量比它还大十倍的模型。

![Satori_math_reasoning](https://s2.loli.net/2025/02/13/rIdankjoPZJSNwe.png)

### Satori-7B-Round2 的通用领域推理基准

仅在数学数据集上训练的 Satori-7B-Round2 在跨多个领域外的推理基准测试中表现出强大的迁移能力，并且大幅超越了 Qwen-2.5-Math-7B-Instruct。

尽管没有在其他领域进行训练，Satori-7B-Round2 的性能与或超过了其他小型通用指令模型，与 Llama-3.1-70B-Instruct 等大型模型不相上下。

![Satori_general_domain_reasoning](https://s2.loli.net/2025/02/13/k6B2KLUpwhtSmEj.png)

## Satori-7B-Round2-WebUI 的运行界面

![Satori-7B-Gradio](https://s2.loli.net/2025/02/11/VwUoqjbtGizNyMm.png)

## 一键部署 Satori-7B-Round2-WebUI

在这里特别感谢 `UCloud` 优云智算提供的 GPU 算力支持！让项目得到了快速的部署和调试运行。

### UCloud 介绍

![UCloud](https://s2.loli.net/2025/02/13/dDV4fosLACQgpmJ.png)

> 优云智算是 UCloud 优刻得的GPU算力租赁平台，专注于为用户提供灵活的算力资源。支持按天、按小时短期租赁及包月长期租赁，满足各类需求。
> 
> 结合丰富的公共镜像社区，优云智算提供多种预配置的容器镜像，如LLamaFactory、SD-webUI 和 LLM 等，实现一键部署，5分钟就能快速上手 AI，助力用户快速启动和扩展项目。

### 通过镜像一键部署实例

#### 1. 使用该镜像创建实例

首先，在`镜像发布页`可以查看到我制作完成并分享到平台的实例镜像，通过右侧的`使用该镜像创建实例`可以快速创建一个实例。

**Satori-7B-Round2-WebUI 镜像发布页**：<https://www.compshare.cn/images-detail?ImageID=compshareImage-18czitmv51ov&referral_code=4sOb83sEXe4BLkKYqw9G4P&ytag=GPU_hych_Lcsdn_csdn_display>

>【算力福利速递】通过镜像发布页的链接注册可以获得 40 算力金，免费体验 20 小时顶配 4090 显卡，企业或高校认证后有 95 折和额外 10 元算力金。

![Satori_mirror](https://s2.loli.net/2025/02/13/jak4KsMnvJ5Ftz1.png)

#### 2. 部署GPU实例

Satori-7B-Round2 模型的参数量为 `7B` 大小，这里`推荐配置 4090 单卡`。也可按需选择配置后再`立即部署`。

![Satori_mirror_load](https://s2.loli.net/2025/02/13/MtHOD7AWsVSKFbI.png)

#### 3. 启动实例

稍等片刻后，实例就会自动创建并启动，通过查看`实例列表`可查看实例的运行状态，并支持随时关闭或启用。

![UCloud_contorl](https://s2.loli.net/2025/02/13/Jw9BvKVS5POXW2k.png)

实例同时提供了一个 `JupyterLab` 应用作为交互式开发环境，它提供了更现代化和灵活的用户界面，方便我们继续后续的步骤。

![UCloud_JupyterLab](https://s2.loli.net/2025/02/13/utpxBdQqGCMOZSA.png)

#### 4. 运行 WebUI 服务

启动实例后，你可以通过 `JupyterLab` 应用的终端输入以下命令来快速启动服务：
```bash
python gradio_app.py --share --host 0.0.0.0 --port 7860
```

WebUI 服务默认通过 `7860` 端口进行访问，镜像已经配置了端口转发，你可以直接通过公网访问。

- 参数说明：

| 参数         | 说明                           | 示例命令                                      |
|--------------|-------------------------------|----------------------------------------------|
| `--port`     | 指定应用程序运行的端口号       | `python gradio_app.py --port 7860`           |
| `--share`    | 允许通过公网访问应用程序       | `python gradio_app.py --share`               |
| `--host`     | 指定应用程序绑定的主机地址     | `python gradio_app.py --host 0.0.0.0`        |

**镜像已内置模型**，运行时会检测本地模型路径，不用再重新配置和下载模型，程序会自动启动推理引擎和 Gradio App 并输出访问地址，大致如下：
```raw
* Running on local URL:  http://0.0.0.0:7860
* Running on public URL: https://62c32ff6bbd7ca4d2f.gradio.live
```

## 手动本地部署 Satori-7B-Round2-WebUI

#### 1. 克隆项目到本地
```bash
git clone https://github.com/Airmomo/satori-7b-round2-webui.git
cd satori-7b-round2-webui
```

#### 2. 创建虚拟环境：
```bash
python -m venv myenv
```

#### 3. 激活虚拟环境：
```bash
# Windows
myenv\Scripts\activate

# macOS/Linux
source myenv/bin/activate
```

#### 4. 安装依赖包：
```bash
pip install torch vllm gradio tqdm
```

#### 5. 运行程序：

你可以通过以下方式启动应用：
- 默认本地访问：
```bash
python gradio_app.py
```

默认配置：
- 主机地址：127.0.0.1
- 端口：7860
- 仅允许本地访问

程序会自动帮你下载模型文件，下载完成后会自动启动推理引擎和 Gradio App。最终会输出 Gradio App 的访问地址，大致如下：
```raw
* Running on local URL:  http://127.0.0.1:7860
* Running on public URL: https://62c32ff6bbd7ca4d2f.gradio.live
```

## 资源

- **HuggingFace 仓库**：<https://huggingface.co/Satori-reasoning/Satori-7B-Round2>
- **Satori-7B-Round2-WebUI 镜像发布页**：<https://www.compshare.cn/images-detail?ImageID=compshareImage-18czitmv51ov&referral_code=4sOb83sEXe4BLkKYqw9G4P&ytag=GPU_hych_Lcsdn_csdn_display>

>【算力福利速递】通过镜像发布页的链接注册可以获得 40 算力金，免费体验 20 小时顶配 4090 显卡，企业或高校认证后有 95 折和额外 10 元算力金。