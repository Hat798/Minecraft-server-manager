

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



# Minecraft Server Manager – GUI, CLI & Remote API

## 📌 Introduction / Giới thiệu

**Minecraft Server Manager (QSMM)** is a cross-platform, multi-functional application for managing Minecraft servers. It supports:
**Minecraft Server Manager (QSMM)** là ứng dụng đa nền tảng và đa chức năng để quản lý Minecraft Server, hỗ trợ:

* Local and remote management via API / Quản lý cục bộ và từ xa qua API.
* Run multiple servers simultaneously / Chạy nhiều server song song.
* Modern Qt GUI / Giao diện Qt hiện đại.
* Powerful CLI for server and client / CLI mạnh mẽ cho server và client.
* Automatic Minecraft version, mods, and plugins installation / Tự động tải và cài đặt phiên bản Minecraft, mods và plugins.
* Real-time CPU/RAM monitoring / Theo dõi CPU/RAM theo thời gian thực.

---

## 🚀 Key Features / Tính năng chính

* Multi-instance management / Quản lý nhiều instance.
* Edit `server.properties` via UI or CLI / Chỉnh sửa `server.properties` qua UI hoặc CLI.
* Version management: Vanilla, Paper, Purpur, Fabric, Forge…
* Mod/Plugin install from Modrinth and Spiget / Cài đặt Mods/Plugins từ Modrinth và Spiget.
* CPU%, RAM usage tracking / Theo dõi hiệu năng CPU%, RAM.
* REST API for remote management / API REST để quản lý từ xa.
* Security with Bearer Token + HTTPS support / Bảo mật với Bearer Token + hỗ trợ HTTPS.
* Supports Linux, Windows, macOS.

---

## 🏗 Architecture / Kiến trúc hệ thống

```
+------------------+          +----------------------+
|  Client GUI (Qt) | <------> |  Server CLI (Agent)  |
+------------------+    API   +----------------------+
|  Client CLI      | <------> |  REST API + Core     |
+------------------+          |  Manage Instances   |
                               |  Mods / Plugins     |
                               |  Versions Control   |
                               |  Metrics Monitor    |
                               +----------------------+
```

---

## 📡 Main API / API chính

* `GET  /api/v1/instances` – List all servers / Liệt kê tất cả server.
* `POST /api/v1/instances/:id/start` – Start server / Khởi động server.
* `POST /api/v1/instances/:id/stop` – Stop server / Dừng server.
* `POST /api/v1/instances/:id/command` – Send console command / Gửi lệnh vào console.
* `GET  /api/v1/instances/:id/props` – Get configuration / Lấy cấu hình.
* `POST /api/v1/instances/:id/props` – Update configuration / Chỉnh cấu hình.
* `GET  /api/v1/instances/:id/metrics` – CPU/RAM usage / Thông tin CPU/RAM.
* `POST /api/v1/instances/:id/modrinth/install` – Install mod / Cài mod.
* `POST /api/v1/instances/:id/spiget/install` – Install plugin / Cài plugin.

---

## 📦 Installation / Cài đặt

### Requirements / Yêu cầu

* C++17+
* Qt 6.x
* `nlohmann/json` (header-only)
* `cpp-httplib` (header-only)
* JDK 17+

### Build / Biên dịch

```bash
git clone https://github.com/<yourname>/qsmm.git
cd qsmm
mkdir build && cd build
cmake ..
make
```

---

## ⚡ Run / Chạy ứng dụng

### 1. Run server CLI (agent) / Chạy server CLI (agent)

```bash
./qsmm-agent
# First run prints token / Lần đầu chạy sẽ in token
```

### 2. Connect from client / Kết nối từ client

* **GUI**: Enter IP + token / Nhập IP + token.
* **CLI**:

```bash
qsmm-cli --host http://<IP>:8787 --token <TOKEN> list
```

---

## 🔐 Security / Bảo mật

* All API requests require Bearer Token / Mọi API yêu cầu Bearer Token.
* IP restriction or HTTPS via reverse proxy / Giới hạn IP hoặc chạy sau reverse proxy với HTTPS.
* Role-based access (read-only/admin) / Phân quyền (read-only/admin).

---

## 🗺 Roadmap / Lộ trình

* [ ] Multi-instance support / Hỗ trợ đa instance.
* [ ] Edit `server.properties` via UI / Chỉnh sửa `server.properties` qua UI.
* [ ] Mod/plugin install from Modrinth & Spiget / Cài mod/plugin từ Modrinth & Spiget.
* [ ] Version management (Vanilla, Paper, Purpur, Fabric…) / Quản lý phiên bản.
* [ ] CPU/RAM metrics / Thống kê CPU/RAM.
* [ ] CLI server/client.
* [ ] Windows/macOS support.

---

## 📜 License / Giấy phép

MIT License – Free to use and modify / Tự do sử dụng và chỉnh sửa.
