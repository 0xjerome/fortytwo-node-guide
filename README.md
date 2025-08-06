# 🧠 Fortytwo Node Setup Guide (Linux, No `sudo`)

Fortytwo is a decentralized AI protocol that harnesses idle compute power from devices around the world to run AI inference workloads. By installing and running a Fortytwo node, you contribute to the network and earn rewards in the form of Points based on your device's resources.

---

## 🌐 Official Links

- Website: [https://fortytwo.network](https://fortytwo.network)
- Discord: [https://discord.gg/fortytwo](https://discord.gg/fortytwo)
- VPS Provider (Used in this guide): [https://compute.hivenet.com](https://compute.hivenet.com)

---

## ✅ Requirements (Linux Only)

Ensure your machine meets the following minimum requirements before installing Fortytwo:

- **OS**: Ubuntu 20.04+ or Debian 10+
- **CPU**: 8-core or better
- **RAM**: 16 GB minimum
- **GPU**: Nvidia RTX 3060 or better
- **Storage**: 20+ GB free SSD (preferably NVMe)
- **Network**: Stable 10 Mbps upload/download
- **Privileges**: No `sudo` access required

---

## 🛠️ Step-by-Step Installation (No sudo)

```bash
# 1. Create and enter the install directory
mkdir -p ~/Fortytwo && cd ~/Fortytwo

# 2. Download the node zip
curl -L -o fortytwo-console-app.zip https://github.com/Fortytwo-Network/fortytwo-console-app/archive/refs/heads/main.zip

# 3. Extract using Python (since unzip may not be installed)
python3 -m zipfile -e fortytwo-console-app.zip fortytwo-console-app-main

# 4. Enter the extracted folder
cd fortytwo-console-app-main

# 5. Make script executable and run
chmod +x linux.sh && ./linux.sh
````

---

## 🖥️ Running the Node in Background (with `tmux`)

If you don’t have `sudo` and need to keep the node running after you log out:

1. **Install tmux manually (no sudo)**
   Run from home dir:

   ```bash
   cd ~
   curl -LO https://github.com/tmux/tmux/releases/download/3.3a/tmux-3.3a.tar.gz
   tar -xzf tmux-3.3a.tar.gz
   cd tmux-3.3a
   ./configure --prefix=$HOME/.local
   make && make install
   ```

2. **Add tmux to PATH**

   ```bash
   export PATH=$HOME/.local/bin:$PATH
   ```

3. **Start the node inside tmux**

   ```bash
   tmux new -s node
   cd ~/Fortytwo/fortytwo-console-app-main
   ./linux.sh
   ```

4. **Detach from tmux (keep node running)**
   Press: `Ctrl + B`, then `D`

5. **Reconnect later**

   ```bash
   tmux attach -t node
   ```

---

## 🧠 Node Model Selection

During setup, you'll be asked to select your node's specialization. For **high rewards**, we recommend:

```
4 ⬢ PROGRAMMING & ALGORITHMS - OlympicCoder 32B Q4
```

This model uses \~20GB VRAM and is suitable if your GPU is RTX 4090 or similar.

---

## ❌ Stopping the Node

If you're inside the tmux session, press:

```bash
Ctrl + C
```

Or simply kill the session:

```bash
tmux kill-session -t node
```

---

## 🤝 Join the Community

* Discord: [https://discord.gg/fortytwo](https://discord.gg/fortytwo)

---

## 💡 Credits

This guide is maintained by the community. VPS used in this guide is from [HiveNet Compute](https://compute.hivenet.com).


