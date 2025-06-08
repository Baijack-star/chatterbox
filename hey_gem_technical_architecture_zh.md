## 技术架构与依赖 (Technical Architecture and Dependencies)

HeyGem 项目的实现依赖于一系列先进的AI技术和特定的软件环境。其技术架构和主要依赖项如下：

**关键技术 (Key Technologies):**

*   **声音克隆技术 (Voice Cloning Technology):** 项目集成了先进的声音克隆算法，能够从较短的音频片段中学习并复制特定个体的声音特征，实现高度逼真的语音模仿。
*   **自动语音识别 (ASR - Automatic Speech Recognition):**
    *   采用了 **fun-asr** (通常指 Alibaba FunASR) 作为其自动语音识别引擎。
    *   fun-asr 提供了高效准确的语音转文本能力，是实现语音驱动数字人的关键组件之一。
*   **计算机视觉技术 (Computer Vision Technology):**
    *   应用计算机视觉技术进行人脸检测、特征点提取、以及唇部运动分析等，以实现数字人形象的精确驱动和自然的口型同步。

**TTS 技术 (Text-to-Speech Technology):**

*   文本转语音功能主要基于 **fish-speech-ziming** 模型或技术栈。
*   该 TTS 技术负责将输入的文本转换为自然流畅的语音，并与克隆的声音特征相结合。

**主要依赖 (Main Dependencies):**

为了确保项目能够顺利运行并发挥其全部功能，需要以下主要依赖项：

*   **Node.js:**
    *   要求 **Node.js 18** 版本。Node.js 可能用于项目的后端服务、构建脚本或用户界面部分。
*   **Docker Images:** 项目的核心AI功能通过 Docker 容器化部署，依赖于以下预构建的 Docker 镜像：
    *   `guiji2025/fun-asr`: 包含 fun-asr 自动语音识别服务的镜像。
    *   `guiji2025/fish-speech-ziming`: 包含 fish-speech-ziming TTS 服务的镜像。
    *   `guiji2025/heygem.ai`: 可能是包含 HeyGem 项目核心应用逻辑或整合其他AI服务的镜像。

通过这些关键技术和依赖项的组合，HeyGem 旨在提供一个集成化、高效且易于部署的数字人解决方案。
