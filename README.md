# Grass on VPS

0. [Register Grass](https://app.getgrass.io/register/?referralCode=UNgwK9yHCn4BS3c)

-------------------
วิธีการติดตั้ง
-------------------

1. เปิด VPS เครื่องที่ต้องการรัน

2. ติดตั้ง [Python](https://www.python.org/downloads/) `apt install -y python3 python3-venv python3-pip` ถ้ามีแล้วข้ามไปได้

3. ติดตั้ง [Git](https://git-scm.com/downloads) ถ้ามีแล้วข้ามไปได้

4. ติดตั้ง Screen `apt install -y screen` ถ้ามีแล้วข้ามไปได้

5. พิมพ์คำสั่ง `pip install loguru websockets_proxy`

6. `git clone https://github.com/dekkeng/grass-auto.git && cd grass-auto`

7. `screen -S grass`

8. `cp config.json.sample config.json && nano config.json` 

9. แก้ไขค่า user_id เป็น user grass 

วิธีดูเลข ให้เปิดเข้า[เว็บ Grass](https://app.getgrass.io/dashboard) ในเครื่อง login ให้เรียบร้อย แล้วกด F12 (Console) พิมพ์ (ถ้าก็อปวางไม่ได้ต้องพิมพ์เอา) `localStorage.getItem('userId')` จะได้เลข USER ID ที่ต้องนำมาใส่

แก้ไข Proxy list เป็น user, pwd, ip, port ของ Proxy ที่ต้องการใช้ ,(คอมม่า) ต่อไปได้หลายตัว ถ้าไม่ใช้ Proxy ให้ลบค่าใน [ ] Proxy list ให้หมด เหลือแค่ "proxy_list": []

9. `python3 main.py`

10. Ctrl + A + D แล้วออกจาก VPS ได้เลยครับ