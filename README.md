# drosera-node-update
Step-by-step guide to update Drosera operator to v1.17.2
🔄 Drosera Node Update — v1.17.2
This guide helps you update your existing Drosera node to version v1.17.2. It covers updating the binary, applying updated config, and restarting the node with Docker.

⚠️ Important: Make sure your trap and operator were already registered before performing these steps. This guide assumes an existing setup.

✅ Step-by-Step Update Instructions
bash
Copy
Edit
# 1. Stop your currently running Docker node and remove volumes
cd ~/Drosera-Network && docker compose down -v
bash
Copy
Edit
# 2. Move to your home directory
cd ~
bash
Copy
Edit
# 3. Download the latest operator binary (v1.17.2)
curl -LO https://github.com/drosera-network/releases/releases/download/v1.17.2/drosera-operator-v1.17.2-x86_64-unknown-linux-gnu.tar.gz
bash
Copy
Edit
# 4. Extract the downloaded tar file
tar -xvf drosera-operator-v1.17.2-x86_64-unknown-linux-gnu.tar.gz
bash
Copy
Edit
# 5. Verify the updated version
./drosera-operator --version
# Output should show: drosera-operator v1.17.2
bash
Copy
Edit
# 6. Pull the latest Docker image
docker pull ghcr.io/drosera-network/drosera-operator:latest
bash
Copy
Edit
# 7. Navigate to your trap directory
cd ~/my-drosera-trap
bash
Copy
Edit
# 8. Update the RPC endpoint in drosera.toml (if required)
# Make sure the relay endpoint is set properly
sed -i '2s|.*|drosera_rpc = "https://relay.testnet.drosera.io"|' "$HOME/my-drosera-trap/drosera.toml"
bash
Copy
Edit
# 9. Apply any configuration changes using your private key
# Replace `xxx` with your actual private key (never share it publicly)
DROSERA_PRIVATE_KEY=xxx drosera apply
bash
Copy
Edit
# 10. Start your updated node with Docker
cd ~/Drosera-Network && docker compose up -d
bash
Copy
Edit
# 11. Check if your Docker container is running
docker ps -a
bash
Copy
Edit
# 12. Monitor live logs
docker compose logs -f
📌 Notes
✅ This update does not require re-deploying your trap or re-registering your operator.

🛠️ If you made edits to drosera.toml, always run drosera apply with your private key.

🔐 Never hardcode your private key in scripts if you plan to publish the repo.
