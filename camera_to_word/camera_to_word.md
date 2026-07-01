# Tool Name: camera_to_word

## Description
当用户需要将实体纸质文档、打印材料、合同、发票或摄像头眼前的任何文字内容扫描、识别并转换为精排版的 Word (.docx) 文档时，调用此工具。该工具会启动本地摄像头捕捉画面，并利用本地 Qwen3-VL:30B 模型进行高精度解析与排版，最终在桌面生成 Word。

## Triggers / Intents
- 帮我把摄像头里的内容导到word里面
- 帮我扫描面前的纸质文件到Word
- 帮我把手里的合同打印成电子档Word
- 启动摄像头看一眼这个文件并转成Word
- 拍照转Word

## Dependencies & Requirements
运行该技能需要以下 Python 第三方库：
- `opencv-python` (用于调用摄像头和图像捕捉)
- `requests` (用于与本地 Ollama API 通信)
- `python-docx` (用于生成和排版 Word 文档)

## Agent Environment Setup Instruction (CRITICAL)
当你（Agent）在执行此技能时，请按照以下逻辑处理依赖环境（只需确认/执行一次）：
1. **静默检测/一键安装**：在首次执行此技能，或用户是一台全新机器时，请先在后台终端隐式执行以下依赖安装命令（确保环境就绪）：
   `pip install opencv-python requests python-docx`
2. **异常捕获 fallback**：如果在后续执行 Python 脚本时遇到 `ModuleNotFoundError`（找不到模块错误），请立即自动执行上述 `pip install` 命令，无需反复询问用户，安装完成后重新尝试执行脚本。

## Execution Type
python_script

## Command
python C:\Users\dell\Desktop\doc_agent_qwen3_safe.py

## Output Format
JSON string indicating completion status and file path.

## Notes
- 该工具运行在戴尔 Precision 专业工作站上，本地加载 Qwen3-VL:30B 模型。
- 任务执行完毕后，脚本会自动释放摄像头资源并退出，无需手动关闭后台。
