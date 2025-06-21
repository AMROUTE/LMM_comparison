主要是针对ChatGLM3-6b与千问两个大模型之间的部署以及语言生成对比
✅ 1. ChatGLM3-6B 环境配置

📦 推荐环境
	•	Python：3.10
	•	PyTorch：>=1.13.1（建议 2.x 以上）
	•	transformers：>=4.32.0
	•	必需依赖：pip install torch transformers accelerate sentencepiece
📁 模型文件
从 HuggingFace 下载模型 THUDM/chatglm3-6b
如果无法联网，可手动下载后放到 /mnt/data/chatglm3-6b
✅ 示例代码
//from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("/mnt/data/chatglm3-6b", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained("/mnt/data/chatglm3-6b", trust_remote_code=True).eval()

history = []
response, history = model.chat(tokenizer, "你好", history=history)
print(response)//
✅ 2. Qwen-7B Chat 环境配置

📦 推荐环境
	•	Python：3.10
	•	PyTorch：>=2.0
	•	transformers：>=4.35.0
	•	需要安装：pip install torch transformers accelerate einops tiktoken
📁 模型文件
 HuggingFace 下载）：Qwen/Qwen-7B-Chat
若手动下载：保存到 /mnt/data/Qwen-7B-Chat

✅ 示例代码
//from transformers import AutoModelForCausalLM, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("/mnt/data/Qwen-7B-Chat", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained("/mnt/data/Qwen-7B-Chat", trust_remote_code=True).eval()

response, history = model.chat(tokenizer, "你好", history=[])
print(response)//
