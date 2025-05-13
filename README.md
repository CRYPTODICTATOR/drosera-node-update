# Drosera Node Update Guide — v1.17.2

A step-by-step guide to upgrade your existing Drosera node to version **v1.17.2**.

> **Note:** No need to re-register your operator or trap.

---

## ✅ Prerequisites

You should already have your node installed in this directory:

~/my-drosera-trap

---

## 1. Stop Old Node


```bash
cd ~/Drosera-Network && docker compose down -v
```


# 2. Move to your home directory


```bash
cd ~
```

# 3. Download the latest operator binary (v1.17.2)

```bash
curl -LO https://github.com/drosera-network/releases/releases/download/v1.17.2/drosera-operator-v1.17.2-x86_64-unknown-linux-gnu.tar.gz
```

# 4. Extract the downloaded tar file

```bash
tar -xvf drosera-operator-v1.17.2-x86_64-unknown-linux-gnu.tar.gz
```

# 5. Verify the updated version
```bash
./drosera-operator --version
```
Output should show: drosera-operator v1.17.2


# 6. Pull the latest Docker image
```bash
docker pull ghcr.io/drosera-network/drosera-operator:latest
```

# 7. Navigate to your trap directory
```bash
cd ~/my-drosera-trap
```


# 8. Update the RPC endpoint in drosera.toml

```bash
sed -i '2s|.*|drosera_rpc = "https://relay.testnet.drosera.io"|' "$HOME/my-drosera-trap/drosera.toml"
```
# 9. Apply any configuration changes using your private key
```bash

DROSERA_PRIVATE_KEY=xxx drosera apply
```
Replace `xxx` with your actual private key (never share it publicly)

# 10. Start your updated node with Docker

```bash
cd ~/Drosera-Network && docker compose up -d
```

# 11. Check if your Docker container is running

```bash
docker ps -a
```

# 12. Monitor live logs

```bash
docker compose logs -f
```


✅ Done!

Your Drosera node should now be running v1.17.2 successfully and continue producing blocks.
Check your dashboard for confirmation.


---

Credits


Guide by CRYPTODICTATOR

Twitter: @domainpay

https://x.com/domainpay

---
---

📌 Notes

✅ This update does not require re-deploying your trap or re-registering your operator.

🛠️ If you made edits to drosera.toml, always run drosera apply with your private key.

🔐 Never hardcode your private key in scripts if you plan to publish the repo.

---
