# 20251203更新
Cherry Studio app打开流式输出功能时openai模型报错"Unknown parameter: stream_options".
通过在代码中清除app发送的stream_options参数解决.

# Poe-API-Parameter-Injection-for-Cherry-Studio-Web-Search-Thinking-Budget-
自从POE更新API参数后(似乎是在20251101左右),即不再支持文本注入的方式调用模型内置搜索引擎以及设置思维链长度,cherry studio的websearch/思维链长度选项对于POE的api就不再有效. 已提交issue但截止当前(20251201)官方似乎未能解决相关问题(https://github.com/CherryHQ/cherry-studio/issues/11177), 这对于一不小心开通年费POE会员且对POE网页版功能不满意的我来说有点难以接受,因此找了很多方法,最后依靠Gemini编写了初步可行的注入参数的代码,后续为了方便使用也让Gemini生成了一个webui.我并不会编程,全程依靠Gemini编写,供各位参考.

仅针对特定模型提供 **Web Search** 和 **Thinking Budget/Reasoning effort** 的参数控制。

已测试模型:**Claude-Sonnet-4.5/Claude-Haiku-4.5/GPT-5.1/Gemini-3.0-Pro**

## ✨ 功能特点
- **完美兼容**：专为 Cherry Studio 适配，解决原生 Poe 支持不完善的问题。
- **可视化控制台**：提供 WebUI (默认端口 8001)，可实时调整：
  - 🧠 **思考预算 (Budget)**：支持 Claude/Gemini 4k-32k 五档调节。
  - 🚀 **推理强度 (Effort)**：支持 ChatGPT 系列的 Low/Medium/High 设置。
  - 🌐 **联网开关**：一键开启/关闭 Web Search。
- **参数注入**：自动将 WebUI 的设置注入到每一次 API 请求中。

## 🛠️ 使用方法

### 1. 安装依赖
```bash
pip install -r requirements.txt
```

### 2. 配置
在项目根目录创建 .env 文件，填入你的 Poe API Key：
```bash
POE_API_KEY=xxxxxxxxxx
```
### 3. 运行
```bash
python POE.py
```
### 4. 在Cherry Studio中配置POE
Base URL: http://127.0.0.1:8001/v1

API Key: (随便填，或者填你的 Poe Key)

 

## 🛠️ 界面预览

<img width="500" height="500" alt="520608929-f20b1811-acfc-4278-9e72-377b97d7c603" src="https://github.com/user-attachments/assets/fea1d998-9dae-49f2-b571-19b39ba08f2c" />
