## 安装与使用 (Installation and Usage)

**安装命令 (Installation Command):**

您可以使用 pip 包管理器轻松安装 Chatterbox TTS：

```bash
pip install chatterbox-tts
```

**TTS 使用示例 (TTS Usage Example):**

以下是如何使用 Chatterbox TTS 进行文本转语音的基本示例：

```python
import torch
import torchaudio
from chatterbox_tts import ChatterboxTTS

# 确定运行设备 (CUDA GPU 或 CPU)
device = "cuda" if torch.cuda.is_available() else "cpu"

# 加载预训练的 ChatterboxTTS 模型
# 模型会自动从 Hugging Face Hub 下载
tts_model = ChatterboxTTS.from_pretrained(device=device)

# 要转换的文本
text_to_speak = "这是一个示例文本，将通过 Chatterbox TTS 转换为语音。"

# （可选）提供一个音频提示文件，以生成特定说话人风格的语音
# 如果不提供 audio_prompt_path，模型将使用其默认的通用语音
audio_prompt_file = "YOUR_FILE.wav"  # 替换为您自己的音频文件路径

# 生成语音波形
# tts_model.generate() 返回一个包含波形和采样率的元组
wav, sr = tts_model.generate(text_to_speak, audio_prompt_path=audio_prompt_file)

# 保存生成的音频文件
output_filename = "tts_output.wav"
torchaudio.save(output_filename, wav.cpu(), sr)

print(f"文本转语音完成，音频已保存至 {output_filename}")
```

**VC 使用示例 (VC Usage Example):**

以下是如何使用 ChatterboxVC 进行语音转换/克隆的基本示例：

```python
import torch
import torchaudio
from chatterbox_tts import ChatterboxVC

# 确定运行设备 (CUDA GPU 或 CPU)
device = "cuda" if torch.cuda.is_available() else "cpu"

# 加载预训练的 ChatterboxVC 模型
# 模型会自动从 Hugging Face Hub 下载
vc_model = ChatterboxVC.from_pretrained(device=device)

# 输入音频文件路径 (要转换的原始语音)
input_audio_file = "INPUT_AUDIO.wav"  # 替换为您的输入音频文件

# 目标语音文件路径 (提供目标音色的语音样本)
target_voice_file = "TARGET_VOICE.wav" # 替换为您的目标音色文件

# 生成语音波形
# vc_model.generate() 返回一个包含波形和采样率的元组
wav, sr = vc_model.generate(audio=input_audio_file, target_voice_path=target_voice_file)

# 保存生成的音频文件
output_filename = "vc_output.wav"
torchaudio.save(output_filename, wav.cpu(), sr)

print(f"语音转换完成，音频已保存至 {output_filename}")
```

**示例文件 (Example files):**

项目中通常会提供示例脚本，以帮助用户快速上手：

*   `example_tts.py`: 包含文本转语音功能的完整示例代码。
*   `example_vc.py`: 包含语音转换/克隆功能的完整示例代码。

建议查看这些文件以获取更详细的用法和参数说明。
