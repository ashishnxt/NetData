# NetData
NetData


[﻿learn.netdata.cloud/docs/netdata-agent/installation/linux](https://learn.netdata.cloud/docs/netdata-agent/installation/linux) 

# **Netdata Installation and Usage Guide**
## ** Netdata Installation on Linux**
To install Netdata, run the following command in your terminal:

```bash
bashCopy codewget -O /tmp/netdata-kickstart.sh https://get.netdata.cloud/kickstart.sh && sh /tmp/netdata-kickstart.sh
```
### **Uninstallation**
If you wish to uninstall Netdata, use the following command:

```bash
bashCopy code--uninstall
```
Once installed, access Netdata through your browser at:

```arduino
arduinoCopy codehttp://<ip-address>:19999
```
## ** Logging into Netdata**
To log in to Netdata, use the following command to retrieve your random session ID:

```bash
bashCopy codesudo cat /var/lib/netdata/netdata_random_session_id
```
- Copy the random session ID and paste it on the login dashboard.
![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/waDl1Iq8ON9yyPVNSc6Co.png?ixlib=js-3.7.0 "image.png")



## **Netdata Dashboard**
The dashboard provides real-time system monitoring. To analyze the dashboard, you can apply a stress test on the system.

#### **Run Stress Test:**
Install the stress-ng tool:

```bash
bashCopy codesudo apt-get install stress-ng
```
Then, run the stress test:

```bash
bashCopy codestress-ng --cpu 0 --cpu-method all --timeout 60s
```
You can now analyze the metrics in your Netdata dashboard.



![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/yCGo0OOKDf5fLKqNLRnQT.png?ixlib=js-3.7.0 "image.png")



Connect two machine with netdata via a master node method.

![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/yAPFYifMgwtiKN1HhSKLw.png?ixlib=js-3.7.0 "image.png")



## **Connecting Nodes via Master Node Method**
To connect multiple machines to a master Netdata instance, follow these steps:

1. **Add Node**: On your master dashboard, click **Add Node**.
2. **Copy the Command**: Copy the command to connect the node.
3. **Run the Command**: Run the copied command on the node you wish to connect.
![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/TXi7ihVgo-71Kq4tnyX1r.png?ixlib=js-3.7.0 "image.png")

Once successful, your node will appear in the master dashboard.



![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/C3ovz1C681rl5Ms6t3T5D.png?ixlib=js-3.7.0 "image.png")







## **Step-by-Step Guide: Copy Netdata Data to Another Machine**
To transfer Netdata data to another machine:

#### **Copy Netdata Configuration Files:**
- `/etc/netdata/netdata.conf` 
- `/etc/netdata/*.conf` 
- `/etc/netdata/go.d/*` 
- `/etc/netdata/health.d/*` 
Stop the Netdata service on the source machine:

```bash
bashCopy codesudo systemctl stop netdata
```
Use `scp` to copy the configuration files:

```bash
bashCopy codescp -r /etc/netdata user@target_machine:/etc/netdata
```
#### **Copy Netdata Database Files:**
- `/var/lib/netdata/` 
Run the following command to copy database files:

```bash
bashCopy codescp -r /var/lib/netdata user@target_machine:/var/lib/netdata
```
#### **Install Netdata on the Target Machine (if not installed)**
If Netdata is not installed on the target machine, install it with the command:

```bash
bashCopy codewget -O /tmp/netdata-kickstart.sh https://get.netdata.cloud/kickstart.sh && sh /tmp/netdata-kickstart.sh --dont-start-it
```
Start Netdata on the target machine:

```bash
bashCopy codesudo systemctl status netdata
```
#### **Restart Netdata**
To apply the changes, restart the Netdata service:

```bash
bashCopy codesudo systemctl restart netdata
```
Check the status:

```bash
bashCopy codesudo systemctl status netdata
```
![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/9Ux5v4DZ7xQMqjkGwcs4Z.png?ixlib=js-3.7.0 "image.png")



![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/KREbAVMEygcmyL2oX0LDQ.png?ixlib=js-3.7.0 "image.png")



![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/WnmN8S6kzmHpseW9Aj-5S.png?ixlib=js-3.7.0 "image.png")



![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/VELeodpMyFqwf95Smizg0.png?ixlib=js-3.7.0 "image.png")



![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/3PJTLA75ag-61tJJeBD8k.png?ixlib=js-3.7.0 "image.png")



Here’s an improved version of your Netdata documentation with structured headings, subheadings, bullet points, and additional details:

---

# **Netdata Installation and Usage Guide**
## **1. Netdata Installation on Linux**
To install Netdata, run the following command in your terminal:

```bash
wget -O /tmp/netdata-kickstart.sh https://get.netdata.cloud/kickstart.sh && sh /tmp/netdata-kickstart.sh
```
### **2. Uninstallation**
If you wish to uninstall Netdata, use the following command:

```bash
--uninstall
```
Once installed, access Netdata through your browser at:

```arduino
http://<ip-address>:19999
```
## **3. Logging into Netdata**
To log in to Netdata, use the following command to retrieve your random session ID:

```bash
bashCopy codesudo cat /var/lib/netdata/netdata_random_session_id
```
- Copy the random session ID and paste it on the login dashboard.
### **4. Netdata Dashboard**
The dashboard provides real-time system monitoring. To analyze the dashboard, you can apply a stress test on the system.

#### **Run Stress Test:**
Install the stress-ng tool:

```bash
bashCopy codesudo apt-get install stress-ng
```
Then, run the stress test:

```bash
bashCopy codestress-ng --cpu 0 --cpu-method all --timeout 60s
```
You can now analyze the metrics in your Netdata dashboard.

![Netdata Stress Test](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/9OK-18jYAGViKFLHLN2OH.png?ixlib=js-3.7.0 "")

## **5. Connecting Nodes via Master Node Method**
To connect multiple machines to a master Netdata instance, follow these steps:

1. **Add Node**: On your master dashboard, click **Add Node**.
2. **Copy the Command**: Copy the command to connect the node.
3. **Run the Command**: Run the copied command on the node you wish to connect.
![Add Node Screenshot](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/PaNcRQRuP0H-Zk_g_n1uZ.png?ixlib=js-3.7.0 "")

Once successful, your node will appear in the master dashboard.

### **6. Step-by-Step Guide: Copy Netdata Data to Another Machine**
To transfer Netdata data to another machine:

#### **Copy Netdata Configuration Files:**
- `/etc/netdata/netdata.conf` 
- `/etc/netdata/*.conf` 
- `/etc/netdata/go.d/*` 
- `/etc/netdata/health.d/*` 
Stop the Netdata service on the source machine:

```bash
bashCopy codesudo systemctl stop netdata
```
Use `scp` to copy the configuration files:

```bash
bashCopy codescp -r /etc/netdata user@target_machine:/etc/netdata
```
#### **Copy Netdata Database Files:**
- `/var/lib/netdata/` 
Run the following command to copy database files:

```bash
bashCopy codescp -r /var/lib/netdata user@target_machine:/var/lib/netdata
```
#### **Install Netdata on the Target Machine (if not installed)**
If Netdata is not installed on the target machine, install it with the command:

```bash
bashCopy codewget -O /tmp/netdata-kickstart.sh https://get.netdata.cloud/kickstart.sh && sh /tmp/netdata-kickstart.sh --dont-start-it
```
Start Netdata on the target machine:

```bash
bashCopy codesudo systemctl status netdata
```
#### **Restart Netdata**
To apply the changes, restart the Netdata service:

```bash
bashCopy codesudo systemctl restart netdata
```
Check the status:

```bash
bashCopy codesudo systemctl status netdata
```
![Netdata Service Status](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/gaNND_s1UyLp2CTlytFMY.png?ixlib=js-3.7.0 "")

---

## **7. Netdata on Docker**
To install Netdata via Docker, follow the instructions from the official documentation: [﻿Netdata on Docker](https://learn.netdata.cloud/docs/netdata-agent/installation/docker).

![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/Qn0DtWowAAwr5Gg5dl9cA.png?ixlib=js-3.7.0 "image.png")



Here’s an improved version of your Netdata documentation with structured headings, subheadings, bullet points, and additional details:

---

# **Netdata Installation and Usage Guide**
## **1. Netdata Installation on Linux**
To install Netdata, run the following command in your terminal:

```bash
bashCopy codewget -O /tmp/netdata-kickstart.sh https://get.netdata.cloud/kickstart.sh && sh /tmp/netdata-kickstart.sh
```
### **2. Uninstallation**
If you wish to uninstall Netdata, use the following command:

```bash
bashCopy code--uninstall
```
Once installed, access Netdata through your browser at:

```arduino
arduinoCopy codehttp://<ip-address>:19999
```
## **3. Logging into Netdata**
To log in to Netdata, use the following command to retrieve your random session ID:

```bash
bashCopy codesudo cat /var/lib/netdata/netdata_random_session_id
```
- Copy the random session ID and paste it on the login dashboard.
### **4. Netdata Dashboard**
The dashboard provides real-time system monitoring. To analyze the dashboard, you can apply a stress test on the system.

#### **Run Stress Test:**
Install the stress-ng tool:

```bash
bashCopy codesudo apt-get install stress-ng
```
Then, run the stress test:

```bash
bashCopy codestress-ng --cpu 0 --cpu-method all --timeout 60s
```
You can now analyze the metrics in your Netdata dashboard.

![Netdata Stress Test](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/3x4xOXGLpqOQ7SUhRae6Y.png?ixlib=js-3.7.0 "")

## **5. Connecting Nodes via Master Node Method**
To connect multiple machines to a master Netdata instance, follow these steps:

1. **Add Node**: On your master dashboard, click **Add Node**.
2. **Copy the Command**: Copy the command to connect the node.
3. **Run the Command**: Run the copied command on the node you wish to connect.
![Add Node Screenshot](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/p8lhKejAezyLk8tjkQ_er.png?ixlib=js-3.7.0 "")

Once successful, your node will appear in the master dashboard.

### **6. Step-by-Step Guide: Copy Netdata Data to Another Machine**
To transfer Netdata data to another machine:

#### **Copy Netdata Configuration Files:**
- `/etc/netdata/netdata.conf` 
- `/etc/netdata/*.conf` 
- `/etc/netdata/go.d/*` 
- `/etc/netdata/health.d/*` 
Stop the Netdata service on the source machine:

```bash
bashCopy codesudo systemctl stop netdata
```
Use `scp` to copy the configuration files:

```bash
bashCopy codescp -r /etc/netdata user@target_machine:/etc/netdata
```
#### **Copy Netdata Database Files:**
- `/var/lib/netdata/` 
Run the following command to copy database files:

```bash
bashCopy codescp -r /var/lib/netdata user@target_machine:/var/lib/netdata
```
#### **Install Netdata on the Target Machine (if not installed)**
If Netdata is not installed on the target machine, install it with the command:

```bash
bashCopy codewget -O /tmp/netdata-kickstart.sh https://get.netdata.cloud/kickstart.sh && sh /tmp/netdata-kickstart.sh --dont-start-it
```
Start Netdata on the target machine:

```bash
bashCopy codesudo systemctl status netdata
```
#### **Restart Netdata**
To apply the changes, restart the Netdata service:

```bash
bashCopy codesudo systemctl restart netdata
```
Check the status:

```bash
bashCopy codesudo systemctl status netdata
```
![Netdata Service Status](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/BQGm_JAAyBJcGBYMpWtFp.png?ixlib=js-3.7.0 "")

---

## **Netdata on Docker**
To install Netdata via Docker, follow the instructions from the official documentation: [﻿Netdata on Docker](https://learn.netdata.cloud/docs/netdata-agent/installation/docker).

![Netdata Docker Screenshot](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/98lUPPp2F1E7n20en610x.png?ixlib=js-3.7.0 "")

---

## **Netdata v1 Export / import Features (Offline Method)**
### **Export and Import Metrics**
Netdata v1 allows users to export and import metrics between machines. The process involves creating a snapshot of your data, which can be transferred and imported on another system.



![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/MtAaDwwvv_uX_J8wu3Wm8.png?ixlib=js-3.7.0 "image.png")





#### **Export Feature:**
You can export metrics from the dashboard by selecting the export option.

![image.png](https://eraser.imgix.net/workspaces/6Re2Ug8vFKhPpFryP1IE/3NNNTOPahOMbiiQsXPT4UsLofJ73/kxWVRVkMYfz31jfxWp_mQ.png?ixlib=js-3.7.0 "image.png")



#### **Import Feature:**
The import feature allows you to upload the snapshot file to another machine.

