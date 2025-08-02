# แอป Flask Docker

แอปพลิเคชัน Flask อย่างง่ายที่รันใน Docker container พร้อมส่งคืนข้อความทักทาย

## ความต้องการของระบบ

- Docker
- Docker Compose (ไม่บังคับ)

## โครงสร้างไฟล์

```
├── Dockerfile          # ไฟล์คำสั่งสำหรับสร้าง Docker image
├── app.py              # แอปพลิเคชัน Flask หลัก
├── requirements.txt    # รายการ dependencies ของ Python
└── README.md          # ไฟล์นี้
```

## วิธีการติดตั้งและรัน

### 1. Clone หรือดาวน์โหลดโปรเจค

```bash
git clone <repository-url>
cd <project-directory>
```

### 2. สร้าง Docker Image

```bash
docker build -t flask-app .
```

### 3. รัน Container

```bash
docker run -p 5000:5000 flask-app
```

### 4. เข้าถึงแอปพลิเคชัน

เปิดเว็บเบราว์เซอร์และไปที่:
```
http://localhost:5000
```

คุณจะเห็นข้อความ: "Hello, this is my first docker app"

## คำสั่งที่มีประโยชน์

### รัน container ในโหมด detached (รันเบื้องหลัง)
```bash
docker run -d -p 5000:5000 --name my-flask-app flask-app
```

### ดู logs ของ container
```bash
docker logs my-flask-app
```

### หยุด container
```bash
docker stop my-flask-app
```

### ลบ container
```bash
docker rm my-flask-app
```

### ลบ image
```bash
docker rmi flask-app
```

## รายละเอียดเทคนิค

- **Base Image**: Python 3.9-slim
- **Port**: 5000
- **Framework**: Flask
- **Working Directory**: /app

## การพัฒนาเพิ่มเติม

หากต้องการแก้ไขโค้ด:

1. แก้ไขไฟล์ `app.py`
2. สร้าง image ใหม่: `docker build -t flask-app .`
3. รัน container ใหม่: `docker run -p 5000:5000 flask-app`

## การแก้ไขปัญหา

### Port ถูกใช้งานแล้ว
หากพบข้อผิดพลาดเรื่อง port ให้เปลี่ยนเป็น port อื่น:
```bash
docker run -p 8080:5000 flask-app
```
แล้วเข้าถึงที่ `http://localhost:8080`

### Container ไม่รัน
ตรวจสอบ logs:
```bash
docker logs <container-name>
```

## License

โปรเจคนี้เป็นตัวอย่างสำหรับการเรียนรู้ Docker และ Flask
