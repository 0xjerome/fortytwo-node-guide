# fortytwo-node-guide
Full installation &amp; operation guide for Fortytwo Node on Ubuntu/Linux

Here is your complete **Fortytwo Node Installation Guide** (for Ubuntu/Linux systems), ready to paste into your GitHub `README.md` or Gist:

---

# 🧠 Fortytwo Node Installation Guide (Linux)

Fortytwo is a decentralized AI protocol that turns everyday GPUs into part of a swarm intelligence system. Instead of relying on centralized cloud infrastructure, Fortytwo distributes inference tasks across idle machines, rewarding users for contributing compute.

By running a Fortytwo node, you help power decentralized AI while earning rewards in return.

---

## 🚀 Requirements (Linux/Ubuntu)

Make sure your system meets the following **minimum requirements**:

* **OS**: Ubuntu 20.04+ or Debian 10+
* **CPU**: 8-core (Intel i7, Ryzen 7 or better)
* **RAM**: 16 GB or more
* **GPU**: Nvidia RTX 3060 or better (Nvidia required)
* **Storage**: At least 20 GB free (SSD or NVMe preferred)
* **Network**: 10 Mbps or better (stable)

> ⚠️ You must be accepted into the Fortytwo devnet to activate a node. Check the official [Application Form](https://fortytwo.network) for access.

---

## 🛠️ Installation Steps

### Step 1: Create a working directory

```bash
mkdir -p ~/Fortytwo && cd ~/Fortytwo
```

### Step 2: Download the Fortytwo console app

```bash
curl -L -o fortytwo-console-app.zip https://github.com/Fortytwo-Network/fortytwo-console-app/archive/refs/heads/main.zip
```

### Step 3: Extract the zip file (no `unzip` or `sudo` needed)

```bash
python3 -m zipfile -e fortytwo-console-app.zip .
rm fortytwo-console-app.zip
```

### Step 4: Change directory into the project

```bash
cd fortytwo-console-app-main
```

### Step 5: Make the installer executable and run it

```bash
chmod +x linux.sh
./linux.sh
```

> ✅ Follow the prompts to choose your model (0–16). Option **4: Programming & Algorithms** is great if you're aiming for high rewards and have sufficient GPU VRAM.

---

## 🧰 Keeping the Node Running (with tmux)

If your server doesn't have `sudo` access, you can't install `screen`, but you can still run your node in the background using `tmux`.

### Step 1: Download tmux binary (no sudo)

```bash
curl -LO https://github.com/tmux/tmux/releases/download/3.3a/tmux-3.3a.tar.gz
tar -xzf tmux-3.3a.tar.gz
cd tmux-3.3a
./configure --prefix=$HOME/.local
make && make install
export PATH=$HOME/.local/bin:$PATH
```

### Step 2: Start a named session

```bash
tmux new-session -s node
```

### Step 3: Inside tmux, navigate to the app and start the node

```bash
cd ~/Fortytwo/fortytwo-console-app-main
./linux.sh
```

### Step 4: Detach from tmux (leave the node running)

Press:

```
Ctrl + B, then D
```

### Step 5: Reconnect later

```bash
tmux attach-session -t node
```

---

## 💡 Notes

* Your node stays online even if you close the terminal (as long as tmux is running and the server stays on).
* Make sure you’re using a **dedicated GPU machine**.
* Monitor your performance and leaderboard inside the Fortytwo interface.

---

## 📬 Need Help?

* Join the Fortytwo [Discord Community](https://discord.gg/fortytwo) for support
* Follow official updates at [https://fortytwo.network](https://fortytwo.network)

---

