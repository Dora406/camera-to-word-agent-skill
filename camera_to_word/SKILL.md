# Tool Name: camera_to_word

## Description
当用户需要将实体纸质文档、打印材料、合同、发票或摄像头眼前的任何文字内容扫描、识别并转换为精排版的 Word (.docx) 文档时，调用此工具。该工具会启动本地摄像头捕捉画面，并利用本地 Qwen3-VL:4B 模型进行高精度解析与排版，最终在桌面生成 Word。

## Triggers / Intents
- 帮我把摄像头里的内容导到word里面
- 帮我扫描面前的纸质文件到Word
- 帮我把手里的合同打印成电子档Word
- 启动摄像头看一眼这个文件并转成Word
- 拍照转Word

## Dependencies & Requirements
运行该技能需要以下 Python 第三方库：
- `opencv-python`
- `requests`
- `python-docx`

## Agent Environment Setup Instruction
当你（Agent）在执行此技能时，请按照以下逻辑处理依赖环境：
1. **依赖检测与安装**：在首次执行此技能时，请先在终端执行以下命令以确保环境就绪：
   `pip install opencv-python requests python-docx`
2. **异常防翻车**：如果在执行过程中遇到 `ModuleNotFoundError`，请自动重新运行上述 `pip install` 命令。

## Execution Type
python_script

## Command
python ./doc_agent_qwen3_safe.py

## Output Format
JSON string indicating completion status and file path.

## Notes
- **【开源部署说明】**：请确保本 `.md` 配置文件与 `doc_agent_qwen3_safe.py` 脚本放置在**同一个文件夹**内。Agent 框架会切换到当前目录并使用相对路径运行。
- 本工具默认在本地加载 `qwen3-vl:4b` 模型，推荐使用具备强大 GPU 显存的专业工作站（如 Dell Precision 系列）以获得流畅体验。用户亦可自行在 `.py` 脚本中修改为其他本地轻量化模型，或者更大模型（如 `qwen2.5-vl`或者`qwen3-vl:30b`）。
- 任务执行后，摄像头会自动开启，用户进行操作，agent不需要再什么。
