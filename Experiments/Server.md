## SERVER ACCESS 
SSH_KEY_PATH=~/.ssh/id_ed25519
JUMPHOST_HOST=jumphost.mtec.tu-berlin.de
JUMPHOST_PORT=22
JUMPHOST_USER=gabriella
TURBO_HOST=130.149.16.96
TURBO_USER=gabriella

## SERVER METADATA 
### CPU & Memory

| Resource | Total   | Used    | Free    | Available |
| -------- | ------- | ------- | ------- | --------- |
| RAM      | 125 GiB | 3.2 GiB | 116 GiB | 122 GiB   |
| Swap     | 8.0 GiB | 0 B     | 8.0 GiB | —         |
### GPU
|GPU ID|Model|VRAM (Total)|VRAM (Used)|Driver|CUDA|
|---|---|---|---|---|---|
|0|NVIDIA RTX 6000 Ada Generation|49,140 MiB (~48 GB)|38 MiB|580.65.06|13.0|

##  USEFUL COMMANDS 
- ssh username@host # access the host
- exit # disconnect 
- nvidia-smi    # GPU usage
- who           # logged-in users
- htop          # CPU/RAM per user
