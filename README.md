# Drosera Node Update Guide — v1.17.2

A step-by-step guide to upgrade your existing Drosera node to version **v1.17.2**.

> **Note:** This guide assumes you already have a working Drosera node setup. No need to re-register trap or operator.

---

## ✅ Prerequisites

Make sure you’re logged into your server where the node is installed and your current node is running under `~/my-drosera-trap`.

---

## 1. Stop Old Node

```bash
cd ~/Drosera-Network && docker compose down -v


---

2. Download & Install New Binary

cd ~
curl -LO https://github.com/drosera-network/releases/releases/download/v1.17.2/drosera-operator-v1.17.2-x86_64-unknown-linux-gnu.tar.gz
tar -xvf drosera-operator-v1.17.2-x86_64-unknown-linux-gnu.tar.gz

Check the installed version:

./drosera-operator --version


---

3. Pull Latest Docker Image

docker pull ghcr.io/drosera-network/drosera-operator:latest


---

4. Update drosera.toml Config (Optional but Recommended)

cd ~/my-drosera-trap

sed -i '2s|.*|drosera_rpc = "https://relay.testnet.drosera.io"|' "$HOME/my-drosera-trap/drosera.toml"


---

5. Apply Changes with Your Private Key

cd ~/my-drosera-trap

DROSERA_PRIVATE_KEY=your_private_key_here drosera apply

> Replace your_private_key_here with your actual private key (no spaces).




---

6. Restart Node

cd ~/Drosera-Network && docker compose up -d


---

7. Check Logs & Status

Check running containers:

docker ps -a

View live logs:

docker compose logs -f


---

✅ Done!

Your Drosera node should now be running v1.17.2 successfully and continue producing blocks.
Check your dashboard for confirmation.


---

Credits

Guide by CRYPTODICTATOR
Twitter: @Domainpay

---
