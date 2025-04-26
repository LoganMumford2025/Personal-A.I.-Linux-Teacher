# Personal-A.I. Instructor and Assistant

## Table of Contents

- [Personal A.I.](#personal-ai)
- [Objective](#objective)
- [Required Hardware & Software](#hardware--software)
- [Why This Project Matters](#why-this-project-matters)
- [Challenges & Solutions](#challenges--solutions)
- [Key Learnings](#key-learnings)
- [Next Steps & Improvements](#next-steps--improvements)
- [Example of Use Screenshots](#example-of-use-screenshots)
- [Conclusion](#conclusion)

## Personal A.I.

This project is a custom-built virtual machine (VM) running on my local hardware, integrated with an AI assistant to provide interactive, hands-on Linux education. The AI acts as a mentor, offering real-time guidance, answering questions, and suggesting practical exercises to master Linux concepts like file systems, shell scripting, permissions, and more.

## Objective
- **Personalized Learning**: I wanted a tailored way to learn Linux at my own pace, with an AI that adapts to my skill level and learning style. I have since expanded this machine with other LLM's tuned for learning python and learning pentesting.
- **On-Premise Power**: Running everything locally gives me full control, privacy, and the ability to experiment without relying on cloud services.
- **Showcase My Journey**: This repo is a living record of my progress, challenges, and discoveries, meant to inspire others to combine AI and Linux in creative ways.
- **Cost & Security**: Running AI locally allows my data to stay private and I have unlimited tokens for queries and the only associated cost is the power to run my VM.

## Hardware & Software

### Hardware:

- 6 CPU cores (Intel 14900K)
- GPU NVIDIA 4070 Ti Super (16GB VRAM)
- 32 GB RAM
- 500GB SSD Drive

### Software:

- Proxmox Hypervisor
- Ubuntu 24.04LTS Virtual Machine
- Ollama
- Open Web UI (running in docker)
- Tavily used for web searches

### LLM Models:
- Gemma3:12b (8bit Quantized): Personal Linux and networking teacher. Takes prompts/ questions and only gives answers when asked. I can also use it to troubleshoot and ask specific questions unique to my home lab environment.
- Mistral:8b Pentesting assistant. This one is tweaked and prompted to help me learn Kali Linux and is also prompted to be aware of all the VM's in my [Active Directory and Security Lab](https://github.com/LoganMumford2025/Active-Directory-and-Security-Lab)
- Openhermes:8b Python instructor and assistant. This LLM provides hands-on problems to solve, offering partial code snippets or troubleshooting challenges. I can also upload screenshots of my Python code from Visual Studio, and it will analyze, grade, and suggest improvements or alternative solutions.

## Why This Project Matters

Learning technical skills like Linux, Python, or pentesting can be overwhelming, but AI makes it approachable and engaging. This project demonstrates how to leverage powerful hardware, open-source AI tools, and a custom VM to create a personalized learning hub. By sharing my work, I hope to:
- Inspire others to build their own AI-powered learning systems.
- Empower beginners to tackle Linux, coding, or cybersecurity with confidence.
- Foster a community of learners who share ideas, exercises, and improvements.

## Challenges & Solutions

- **Dedicated GPU** Running on premise AI models requires a lot of VRAM from GPU's. I am limited to LLM's that are around 8-12 billion parameters. Large models that could compete with Grok3 or Chat GPT 4 would require multiple enterprise NVIDIA GPUS like H100 or A100. Won't be able to afford one of those for awhile let alone 8 or 9 of them. Running LLMs with around 8 billion parameters typically requires at least ~8-10 GB of VRAM. I can run 8B models comfortably without quantization. However, when making certain tweaks — like increasing the context window size (via Open WebUI) — I found that VRAM usage increased. I aimed to push each model, with adjustments, to use about 75% of my available VRAM for optimal performance.
- **Prompting** A lot of work went into getting a good prompt written for each LLM to get it to "act" the way I want it to. In open web ui, you can add a prompt for each LLM to provide the AI with context on how it should answer and also provide it a bit of personality in some cases. This is still a work in progress and I am constantly tweaking the prompts to get finer tuned answer formats.
- **Adding Web Search Funcionality** Luckily, Open WebUI allows users to link an external API for search queries by the AI model. I used Tavily (free version), which enables different AI models to search the internet for better context when answering questions. There’s definitely room for further tweaking, and there are many other search API options available besides Tavily. However, Tavily has a free option and I haven't hit the limit on how many searches are allowed per month yet.

## Key Learnings

- **Prompting** I did a lot of tweaking and research on how prompts affect how the AI will respond. This is definitely and art and science and will require future practice.
- **LLM Fine-tuning/ Training** I looked at fine tuning some LLM's from Ollama and a few other models from Hugging Face. I couln't get the software stack to work properly in order to fine tune. I ran into a lot of dependency conflicts and versions of software not playing well with either a driver or another software. I opted to create and maintain an offline repository of datasets that my LLM's can reference instead of fine tuning. With only one small GPU, fine tuning can be time consuming, order of 12 hours to multiple days, depending on how large the dataset is. Training an LLM from scrath is completely out of the question at this scale. I can get pretty good results from careful prompts and feeding the AI good clean datasets to reference.
- **Open Web-UI Tweaks** Open WebUI is an awesome web interface. Each LLM model has its own section where you can add prompts to adjust behavior and formatting. There are also many sliders, such as temperature, top-k, context length, and more. I'm still learning about each parameter, but tweaking these settings has helped me fine-tune each LLM to provide longer and more detailed responses. 

## Next Steps & Improvements

- Build a large database of scrubbed and converted datasets to provide faster and more reliable AI references. This approach not only speeds up AI queries but also conserves network bandwidth. Instead of reaching out to an external API for every user question, the AI can first reference a large local dataset, delivering quicker results without being limited by internet speed. This also adds a layer of security and the ability to add sensitive documents, medical, financial, etc, and an LLM can use this information to give tailored and specific answers without compromising security or leaking sensitive data.
- Convert Linux Manual Pages, Arch Wiki, and other open source manuals from human readable words to vectors and store those vectors in an on premise database for references.

## Example of Use Screenshots

This is my typical setup for practice problems. I don't have 2 screens so I just split my web browser screen (open web ui) and a console screen of my ubuntu Virtual machine side by side.

![Typical Setup](https://github.com/user-attachments/assets/0b8ffb31-7764-4261-a3ed-a6cb0a527a85)

Example of dialogue and practice walkthrough.

![Practice Problem](https://github.com/user-attachments/assets/8fe8c87a-ee78-4fcb-a463-2c15b016efd0)

![Dialogue 1](https://github.com/user-attachments/assets/57a0eecc-864f-42de-8e63-3795dc5aa706)

![Dialogue 2](https://github.com/user-attachments/assets/c629b137-5c35-4233-a92b-e9dfa20a92b4)

![Dialogue 3](https://github.com/user-attachments/assets/279138ad-9b40-4eb5-81db-7ea56cfef6d1)

![Dialogue 4](https://github.com/user-attachments/assets/85c95c2d-73d5-4035-b884-5f8363e1fe78)

![Dialogue 5](https://github.com/user-attachments/assets/978173c9-305f-4ebf-9005-cd3f0cd0a06a)

## Conclusion

This has been an awesome project and remains my main priority. I am constantly looking for ways to improve this machine and use it in unique ways. If I'm not working on the VM itself I am using it for an hour or two just working through random problems. 

---

By following this template, you can create a structured and professional home lab project that effectively demonstrates your IT skills to potential employers.

