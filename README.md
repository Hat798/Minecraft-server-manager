Ok, đây là nguyên **code của file `README.md`** anh có thể copy-paste thẳng vào GitHub repo:

```markdown
# Minecraft Server Manager – GUI, CLI & Remote API

## 📌 Giới thiệu
**Minecraft Server Manager (QSMM)** là ứng dụng quản lý Minecraft Server **đa nền tảng** và **đa chức năng**, hỗ trợ:
- **Quản lý cục bộ (Local)** và **quản lý từ xa (Remote)** qua API.
- **Chạy nhiều server song song (Multi-instance)** trên cùng một máy.
- Giao diện đồ họa hiện đại với **Qt**.
- **CLI** mạnh mẽ cho cả server và client.
- Tự động tải, cài đặt **phiên bản Minecraft**, **Mods** và **Plugins**.
- Theo dõi **CPU/RAM** từng server instance theo thời gian thực.

---

## 🚀 Tính năng chính
- **Multi-instance** – Quản lý nhiều server Minecraft độc lập.
- **Chỉnh sửa server.properties** trực tiếp bằng UI hoặc CLI.
- **Quản lý phiên bản**: Vanilla, Paper, Purpur, Fabric, Forge…
- **Tải & cài đặt Mods/Plugins** từ Modrinth và Spiget.
- **Theo dõi hiệu năng**: CPU%, RAM realtime.
- **API REST** từ server CLI để quản lý từ xa bằng client.
- **Bảo mật** với Bearer Token, hỗ trợ reverse proxy + HTTPS.
- Hỗ trợ Linux, Windows, macOS.

---

## 🏗 Kiến trúc hệ thống
```

+------------------+          +----------------------+
\|  Client GUI (Qt) | <------> |  Server CLI (Agent)  |
+------------------+    API   +----------------------+
\|  Client CLI      | <------> |  REST API + Core     |
+------------------+          |  Manage Instances   |
\|  Mods / Plugins     |
\|  Versions Control   |
\|  Metrics Monitor    |
+----------------------+

````

---

## 📡 API chính
- `GET  /api/v1/instances` – Liệt kê tất cả server.
- `POST /api/v1/instances/:id/start` – Khởi động server.
- `POST /api/v1/instances/:id/stop` – Dừng server.
- `POST /api/v1/instances/:id/command` – Gửi lệnh vào console.
- `GET  /api/v1/instances/:id/props` – Lấy cấu hình.
- `POST /api/v1/instances/:id/props` – Chỉnh cấu hình.
- `GET  /api/v1/instances/:id/metrics` – CPU/RAM.
- `POST /api/v1/instances/:id/modrinth/install` – Cài mod.
- `POST /api/v1/instances/:id/spiget/install` – Cài plugin.

---

## 📦 Cài đặt
### Yêu cầu
- C++17 trở lên
- Qt 6.x
- `nlohmann/json` (header-only)
- `cpp-httplib` (header-only)
- JDK 17+ (để chạy Minecraft server)

### Biên dịch
```bash
git clone https://github.com/<yourname>/qsmm.git
cd qsmm
mkdir build && cd build
cmake ..
make
````

---

## ⚡ Chạy ứng dụng

### 1. Chạy server CLI (agent)

```bash
./qsmm-agent
# In ra token lần đầu
```

### 2. Kết nối từ client

* **GUI**: nhập IP + token để kết nối.
* **CLI**:

```bash
qsmm-cli --host http://<IP>:8787 --token <TOKEN> list
```

---

## 🔐 Bảo mật

* Mọi API yêu cầu Bearer Token.
* Có thể giới hạn IP hoặc đặt sau reverse proxy với HTTPS.
* Hỗ trợ phân quyền (read-only / admin).

---

## 🗺 Lộ trình phát triển

* [ ] Chạy server đa instance.
* [ ] Chỉnh sửa `server.properties` qua UI.
* [ ] Tải & cài mod/plugin từ Modrinth và Spiget.
* [ ] Quản lý phiên bản Minecraft (Vanilla, Paper, Purpur, Fabric…).
* [ ] Theo dõi hiệu năng CPU/RAM.
* [ ] CLI server/client hoàn thiện.
* [ ] Hỗ trợ Windows/macOS đầy đủ.

---

## 📜 Giấy phép

MIT License – Tự do sử dụng và tùy chỉnh.

```

---

Nếu anh muốn repo **nổi bật hơn trên GitHub**, em có thể thêm **ảnh banner + badges (build, license, platform)** vào phần đầu README để nhìn chuyên nghiệp hơn.  
Anh có muốn em làm luôn phần đó không?
```
