# 20251203更新
Cherry Studio app打开流式输出功能时openai模型报错"Unknown parameter: stream_options".
issue:https://github.com/CherryHQ/cherry-studio/issues/11652
关闭Cherry Studio app 的"流式输出"选项后可以正常使用. 因此想到方法,在代码中清除app发送的stream_options参数,同时在app中继续保持"流式输出"的选项打开,没想到成功解决这个问题.

# Poe-API-Parameter-Injection-for-Cherry-Studio-Web-Search-Thinking-Budget-
自从POE更新API参数后(似乎是在20251101左右),即不再支持文本注入的方式调用模型内置搜索引擎以及设置思维链长度,cherry studio的websearch/思维链长度选项对于POE的api就不再有效. 已提交issue但截止当前(20251201)官方似乎未能解决相关问题(https://github.com/CherryHQ/cherry-studio/issues/11177), 这对于一不小心开通年费POE会员且对POE网页版功能不满意的我来说有点难以接受,因此找了很多方法,最后依靠Gemini编写了初步可行的注入参数的代码,后续为了方便使用也让Gemini生成了一个webui.我并不会编程,全程依靠Gemini编写,供各位参考.
代码运行的逻辑是检测到Claude/Gemini模型则分别注入相应参数,非上述两者则默认为Openai模型.因此建议这三家的模型使用这个代码中转,其他模型不要经过这个中转.
仅针对上述模型提供 **Web Search** 和 **Thinking Budget/Reasoning effort** 的参数控制。

已测试模型:**Claude-Sonnet-4.5/Claude-Haiku-4.5/GPT-5.1/GPT-5.1-instant /Gemini-3.0-Pro**

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
下载"POE in Cherry.py"到项目根目录并运行
### 4. 在Cherry Studio中新建一个模型供应商(Openai类型),如POE_DIY
Base URL: http://127.0.0.1:8001/v1

API Key: (随便填，或者填你的 Poe Key)
<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/fef13395-00b3-49cf-8ae2-0ade3cfef836" />

 

## 🛠️ 界面预览

<img width="500" height="500" alt="520608929-f20b1811-acfc-4278-9e72-377b97d7c603" src="https://github.com/user-attachments/assets/fea1d998-9dae-49f2-b571-19b39ba08f2c" />

## 🛠️ 流式输出预览
<img width="800" height="600" alt="Image" src="https://github.com/user-attachments/assets/4c9649e6-3007-4966-a3f2-6820f7ed2763" />

