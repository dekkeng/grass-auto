# Grass on VPS

0. [Register Grass](https://app.getgrass.io/register/?referralCode=UNgwK9yHCn4BS3c)

-------------------
วิธีการติดตั้ง
-------------------

# Run Grass VPS with Proxy

VPS spec CPU 2, RAM 2Gb, SSD 10Gb

1. ไปซื้อ proxy ที่ https://app.proxies.fo/ref/d99823ad-3956-75f4-2410-70a3b7845e52
สมัคร แล้วเข้าสู่ระบบ

2. มาที่ https://app.proxies.fo/purchase/residential
เลือก Package $4 อันแรก
จ่ายด้วย crypto ได้ (ใช้ transfer ตามจำนวนที่กำหนด แล้วรอ confirm)

3. ไปหน้า https://app.proxies.fo/dashboard
กดตรง Generate Proxy ตรงตัวที่เราเพิ่งซื้อมา (Active Plans)
แก้ไขช่อง Protocol เป็น SOCKS
Format เป็น username:password@hostname:port
ตั้ง Sticky Amount เป็นจำนวน IP ที่ต้องการสร้าง
แล้ว Copy ตรงช่อง Sticky Proxies มาทั้งหมด ใส่ Notepad

4. ไปดู Grass UID บน browser เรา
เข้า https://app.getgrass.io/dashboard
กด Ctrl + Shift + I
เปิดแถบ Application ไปที่ Local storage และชื่อเว็บ app.getgrass
หารายการที่ชื่อ userId ให้ copy เลขนั้นมา

5. รัน ทีละบรรทัด
```
apt update && apt -y upgrade
apt install -y python3 python3-venv python3-pip git screen
pip install loguru websockets_proxy
git clone https://github.com/dekkeng/grass-auto.git && cd grass-auto
cp config.json.sample config.json && nano config.json
```
เอา Grass UID จากข้อ 4 แปะตรง userid
และเอารายการ Proxies จากข้อ 3 มาแปะใน proxy list
โดยให้ format เป็นแบบ config คือ
"socks5://<รายการจากข้อ 3>" ใช้ replace all เพิ่มไปข้างหน้า ครอบด้วย "" และ คั่นด้วย ,
```
{
    "user_id": "00000000-0000-0000-0000-0000000xxx",
    "proxy_list": [
        "socks5://user1:pwd1@ip1:port1",
        "socks5://user2:pwd2@ip2:port2"
    ]
}
```
เซฟ แล้วปิด Ctrl + X > Y > enter

6. รัน
```
screen -S grass
python3 main.py
```

แล้วก็ Ctrl + A + D ออกได้ครับ

ไปเช็คบน Grass dashboard ว่ามี IP โผล่เพิ่มมาหรือยัง ถ้าคะแนนขึ้นแปลว่าถูก
