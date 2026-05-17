# snort3-alloy-loki-Grafana-docker
sudo apt-get update #更新套件清單

sudo apt-get install -y apt-transport-https software-properties-common wget #安裝必要的套件

sudo mkdir -p /etc/apt/keyrings #建立key的目錄

wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null #下載並加入 Grafana GPG 金鑰

echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee /etc/apt/sources.list.d/grafana.list #加入來源(Stable 版本)

sudo apt-get update #更新套件清單

sudo apt-get install alloy #安裝alloy

建立docker-compose.yml跟config.alloy在同一個目錄下

容器建立時，會去讀config.alloy

另一個是在用戶端的alloy用的設定檔

sudo usermod -aG adm alloy #將adm使用者加入到該群組中

sudo mkdir -p /var/lib/alloy #建立目錄

sudo groupadd alloy #建立alloy群組

sudo usermod -aG alloy alloy #將alloy使用者加入到該群組中

sudo chown -R alloy:alloy /var/lib/alloy #修改目錄所有權

sudo chmod 755 /var/lib/alloy #確保權限正確

sudo systemctl start alloy #啟動alloy

sudo systemctl enable alloy #設定開機自動啟動

sudo systemctl status alloy #檢查狀態顯示 active (running)就成功了

sudo -u alloy ls -l /var/log/snort/alert_json.txt #檢查檔案是否可讀

sudo chmod 644 /var/log/snort/alert_json.txt #修改權限

sudo chmod 755 /var/log/snort/  #修改權限

journalctl -u alloy -f #追蹤日誌觀察

/etc/alloy/config.alloy 
