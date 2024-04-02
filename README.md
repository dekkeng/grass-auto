# Grass on VPS

-------------------
วิธีการติดตั้ง
-------------------

1. เปิด VPS เครื่องที่ต้องการรัน

2. ติดตั้ง [Python](https://www.python.org/downloads/) ถ้ามีแล้วข้ามไปได้

3. ติดตั้ง [Git](https://git-scm.com/downloads) ถ้ามีแล้วข้ามไปได้

4. ติดตั้ง Screen `apt install -y screen` ถ้ามีแล้วข้ามไปได้

5. พิมพ์คำสั่ง `pip3 install loguru`

6. `git clone https://github.com/dekkeng/grass-auto.git && cd grass-auto`

7. `screen -S grass`

8. `cp config.json.sample config.json && nano config.json` 

9. แก้ไขค่า user_id เป็น user grass วิธีดูเลข ให้เปิดเข้า[เว็บ Grass](https://app.getgrass.io/dashboard) ในเครื่อง login ให้เรียบร้อย แล้วกด F12 (Console) พิมพ์ (ถ้าก็อปวางไม่ได้ต้องพิมพ์เอา) `localStorage.getItem('userId')` จะได้เลข USER ID ที่ต้องนำมาใส่

9. `python main.py`

10. Ctrl + A + D แล้วออกจาก VPS ได้เลยครับ