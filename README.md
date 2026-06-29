markdown

# 🐧 Arch Linux Xfce4 Auto Install Script

> Script tự động cài đặt **Xfce4 Desktop** + **LightDM** + **OpenSSH** trên Arch Linux.

[![Arch Linux](https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white)](https://archlinux.org/)
[![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![GitHub stars](https://img.shields.io/github/stars/DKhoa25/arch-xfce-installer?style=for-the-badge&color=yellow)](https://github.com/DKhoa25/arch-xfce-installer/stargazers)

---

## 📋 Mục lục

- [✨ Tính năng](#-tính-năng)
- [📋 Yêu cầu](#-yêu-cầu)
- [🚀 Cài đặt nhanh](#-cài-đặt-nhanh)
- [📖 Tạo script thủ công](#-tạo-script-thủ-công)
- [🔧 Cấu hình sau cài đặt](#-cấu-hình-sau-cài-đặt)
- [❗ Xử lý lỗi thường gặp](#-xử-lý-lỗi-thường-gặp)
- [🛠️ Tùy chỉnh script](#️-tùy-chỉnh-script)
- [❓ Hỏi đáp](#-hỏi-đáp)
- [🤝 Đóng góp](#-đóng-góp)
- [📄 Giấy phép](#-giấy-phép)

---

## ✨ Tính năng

| Tính năng | Mô tả |
| :--- | :--- |
| 🚀 **Xfce4** | Môi trường desktop nhẹ, nhanh và ổn định |
| 🔌 **xfce4-goodies** | Plugin và công cụ mở rộng |
| 🖥️ **LightDM** | Màn hình đăng nhập đồ họa (chỉ Xfce4) |
| 🔒 **OpenSSH** | Kết nối từ xa, tự động khởi động |
| ⚡ **Tự động hóa** | Cài đặt với 1 script duy nhất |
| 🎨 **Tùy chỉnh sẵn** | Cấu hình LightDM tối ưu cho Xfce4 |

---

## 📋 Yêu cầu

- <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/archlinux/archlinux-original.svg" width="16" height="16"/> **Arch Linux** (hoặc các bản phân phối dựa trên Arch)
- 🌐 **Kết nối Internet** (để tải các gói từ kho)
- 🔑 **Quyền sudo** (hoặc tài khoản root)
- 💾 **Dung lượng trống**: ~2GB

---

## 🚀 Cài đặt nhanh

```bash
# Bước 1: Tải script
curl -O https://raw.githubusercontent.com/DKhoa25/arch-xfce-installer/xfce.sh

# Bước 2: Cấp quyền thực thi
chmod +x xfce.sh

# Bước 3: Chạy script
./xfce.sh

# Bước 4: Khởi động lại hệ thống
sudo reboot
