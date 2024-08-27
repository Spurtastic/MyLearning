---
date: 2024-06-12T20:14
tags:
  - WSL
  - AISetup
---
# Installing wsl

```

wsl --install
```

# Wsl Best practices

```
sudo apt update
sudo apt upgrade -y 

# For new instance of the terminal
wsl -d Ubuntu 
```


# Running the model
```
ollama run qwen2
```

# Watch NVIDIA working
```
watch -n 0.5 nvidia-smi
```