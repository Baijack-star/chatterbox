## 技术细节 (Technical Details)

**主要组件 (Main Components):**

*   `ChatterboxTTS`: 这是处理文本转语音 (Text-to-Speech) 功能的核心类。它负责接收文本输入，并将其转换为语音输出。
*   `ChatterboxVC`: 这是处理语音克隆 (Voice Cloning) 或语音转换 (Voice Conversion) 功能的核心类。它能够学习参考音频的语音特征，并将这些特征应用到新的语音生成中。
*   **模型 (Models):**
    *   **T3:** (具体功能未详细说明，但通常在 TTS 系统中，这类名称可能指代文本处理或声学模型相关的组件)
    *   **S3Gen:** (具体功能未详细说明，但通常在 TTS 系统中，这类名称可能指代频谱生成或声码器相关的组件)
    *   **VoiceEncoder:** 语音编码器，用于提取输入音频的声学特征或说话人嵌入 (speaker embedding)。
    *   **Tokenizers:** 文本处理器或分词器，负责将输入文本转换为模型可以理解的格式。这些通常从 Hugging Face Hub 动态加载。
*   `perth`: 这是一个专门用于在输出音频中添加水印的库，有助于内容的溯源和版权保护。

**音频处理 (Audio Processing):**

*   **采样率 (Sample Rate):** 模型使用的标准采样率为 `S3GEN_SR`。虽然具体数值未给出，但可以推测其为现代 TTS 系统中常见的采样率，例如 24kHz。
*   **条件化 (Conditioning):** 系统通过使用“音频提示 (audio prompt)”来实现特定说话人风格的语音生成。这意味着用户可以提供一小段目标说话人的音频样本，模型将基于该样本的音色、韵律等特征来生成新的语音。

**依赖库 (Key Dependencies):**

项目依赖于以下关键的 Python 库来支持其功能：

*   **PyTorch:** 一个广泛使用的开源机器学习框架，为模型的训练和推理提供基础。
*   **torchaudio:** PyTorch 的一部分，专门用于音频处理任务。
*   **librosa:** 一个用于音频和音乐分析的 Python 库。
*   **huggingface_hub:** 用于从 Hugging Face 模型库下载和共享模型的客户端库。
*   **safetensors:** 一种用于安全存储和加载张量数据的格式。
*   **perth:** 如前所述，用于音频水印的库。
