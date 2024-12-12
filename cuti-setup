#!/bin/bash

# Bước 1: Cài đặt wget và chạy script từ URL
echo "Installing wget and running nexus.sh..."
sudo apt update && sudo apt install -y wget
wget -qO - https://raw.githubusercontent.com/zunxbt/nexus-prover/main/nexus.sh | bash

# Bước 2: Kiểm tra và ghi prover-id
echo "Configuring prover-id..."
while true; do
    if sed -i 's/.*/obW6aJuJN5Vb8ykq3L1Ge73y0l62/' .nexus/prover-id 2>/dev/null; then
        echo "prover-id updated successfully."
        break
    else
        echo "prover-id file not found. Retrying in 5 seconds..."
        sleep 5
    fi
done

# Bước 3: Khởi động lại dịch vụ nexus
echo "Restarting nexus service..."
sudo systemctl restart nexus.service

# Bước 4: Theo dõi log của nexus service
echo "Displaying nexus service logs..."
journalctl -u nexus.service -f -n 50
