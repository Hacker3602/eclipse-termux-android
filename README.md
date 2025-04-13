# ⚡ Bitz Miner on Android via Termux

Mine the first **ePOW commodity token** on the **Eclipse chain** directly from your Android device using Termux!

---

## 🔷 What is Bitz?

- ⛏️ The first **ePOW (Ethereum Proof-of-Work)** commodity token on **Eclipse**
- 💰 Max Supply: **5,000,000 BITZ**
- 🔐 No pre-mine, no team/insider allocations
- 📦 Token Address: [View on EclipseScan](https://eclipsescan.xyz/token/64mggk2nXg6vHC1qCdsZdEFzd5QGN4id54Vbho4PswCF)

---

## 📲 Requirements

- Android device with **Termux** installed
- Eclipse wallet like **Backpack** funded with **ETH**
- Stable internet connection

---

## ⚙️ Installation Steps

### 1. Update & Install Required Packages

```bash
pkg update && pkg upgrade -y
```

```bash
pkg install curl git clang screen nano wget tar -y
```

### 2. Install Rust

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

When prompted, type 1 and press Enter.

```bash
source $HOME/.cargo/env
```

### 3. Install Solana CLI (Workaround for Termux)

```bash
wget https://github.com/solana-labs/solana/releases/download/v1.18.3/solana-release-aarch64-unknown-linux-gnu.tar.bz2
```

```bash
tar -xvjf solana-release-aarch64-unknown-linux-gnu.tar.bz2
```

```bash
mv solana-release-aarch64-unknown-linux-gnu solana
```

```bash
cd solana
```


```bash
export PATH="$HOME/solana/bin:$PATH"
```

```bash
echo 'export PATH="$HOME/solana/bin:$PATH"' >> ~/.bashrc
```

```bash
source ~/.bashrc
```

Confirm Solana CLI:

```bash
solana --version
```

### 4. Configure Solana RPC

```bash
solana config set --url https://eclipse.helius-rpc.com/
```

---

## 🔐 Wallet Setup

### Create a CLI Wallet

```bash
solana-keygen new
```

Save your seed phrase and public key (your Eclipse wallet address)

### Export Private Key

```bash
solana config get
```

Then:

```bash
cat ~/.config/solana/id.json
```

This JSON array is your Private Key

Import it into your Backpack wallet and fund it with ETH on Eclipse

---

## 🚀 Install Bitz Miner

```bash
cargo install bitz
```

---

## 🛠️ Run Bitz Miner

### Open a Screen Session

```bash
screen -S bitz
```

### Start Mining

```bash
bitz collect
```

🔹 Optional: Use specific CPU cores (e.g., 4):

```bash
bitz collect --cores 4
```

---

## 🧰 Useful Screen Commands

| Action | Command |
|--------|---------|
| Minimize screen | Ctrl + A + D |
| Resume screen | screen -r bitz |
| List all screens | screen -ls |
| Stop miner in screen | Ctrl + C |
| Kill screen | screen -XS bitz quit |

---

## 🧪 Bitz CLI Commands

### Check Account Info

```bash
bitz account
```

### Claim BITZ Rewards

```bash
bitz claim
```

### List All Commands

```bash
bitz -h
```

---

## 📌 Tips

- Use `termux-wake-lock` to prevent your phone from sleeping while mining.
- Add mining command to `.bashrc` to auto-start on Termux launch:
  ```bash
  echo 'screen -S bitz -d -m bitz collect' >> ~/.bashrc
  ```
- For Android devices, install Termux from F-Droid for best compatibility.
- Close other apps when mining for better performance.
