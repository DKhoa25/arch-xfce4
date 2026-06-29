<img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" width="40" height="40"/> Arch Linux Xfce4 Auto Install Script

    Script tự động cài đặt Xfce4 Desktop + LightDM + OpenSSH trên Arch Linux.

https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white
https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white
https://img.shields.io/badge/License-MIT-green?style=for-the-badge
https://img.shields.io/github/stars/DKhoa25/arch-xfce-installer?style=for-the-badge&color=yellow
📋 Mục lục

    ✨ Tính năng

    📋 Yêu cầu

    🚀 Cài đặt nhanh

    📖 Tạo script thủ công

    🔧 Cấu hình sau cài đặt

    ❗ Xử lý lỗi thường gặp

    🛠️ Tùy chỉnh script

    ❓ Hỏi đáp

    🤝 Đóng góp

    📄 Giấy phép

✨ Tính năng
Tính năng	Mô tả
🚀 Xfce4	Môi trường desktop nhẹ, nhanh và ổn định
🔌 xfce4-goodies	Plugin và công cụ mở rộng
🖥️ LightDM	Màn hình đăng nhập đồ họa (chỉ Xfce4)
🔒 OpenSSH	Kết nối từ xa, tự động khởi động
⚡ Tự động hóa	Cài đặt với 1 script duy nhất
🎨 Tùy chỉnh sẵn	Cấu hình LightDM tối ưu cho Xfce4
📋 Yêu cầu

    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/archlinux/archlinux-original.svg" width="16" height="16"/> Arch Linux (hoặc các bản phân phối dựa trên Arch)

    🌐 Kết nối Internet (để tải các gói từ kho)

    🔑 Quyền sudo (hoặc tài khoản root)

    💾 Dung lượng trống: ~2GB

🚀 Cài đặt nhanh
bash

# Bước 1: Tải script
curl -O https://raw.githubusercontent.com/DKhoa25/arch-xfce-installer/main/xfce.sh

# Bước 2: Cấp quyền thực thi
chmod +x xfce.sh

# Bước 3: Chạy script
./xfce.sh

# Bước 4: Khởi động lại hệ thống
sudo reboot

📖 Tạo script thủ công

Nếu bạn muốn tự tạo script thay vì tải về:
bash

# Tạo file script
nano ~/xfce.sh

Nội dung script:
<details> <summary><b>📄 Click để xem toàn bộ script</b></summary>
bash

#!/bin/bash

set -e

echo "=========================================="
echo "  CAI DAT XFCE4 + LIGHTDM + OPENSSH"
echo "=========================================="

echo "[1/6] Dang cap nhat he thong..."
sudo pacman -Syu --noconfirm

echo "[2/6] Dang cai dat X Server..."
sudo pacman -S xorg-server xorg-xinit xorg-apps --noconfirm

echo "[3/6] Dang cai dat Xfce4 va xfce4-goodies..."
sudo pacman -S xfce4 xfce4-goodies --noconfirm

echo "[4/6] Dang cai dat LightDM..."
sudo pacman -S lightdm lightdm-gtk-greeter lightdm-gtk-greeter-settings --noconfirm

echo "[5/6] Dang cau hinh LightDM..."
sudo tee /etc/lightdm/lightdm.conf > /dev/null << 'EOF'
[Seat:*]
autologin-user=
autologin-session=xfce
session-wrapper=/etc/lightdm/Xsession
greeter-session=lightdm-gtk-greeter
user-session=xfce
EOF

sudo tee /etc/lightdm/lightdm-gtk-greeter.conf > /dev/null << 'EOF'
[greeter]
background=/usr/share/backgrounds/xfce/xfce-shapes.svg
font-name=Sans 11
theme-name=Adwaita
icon-theme-name=Adwaita
show-indicators=~language;~session;~power
screensaver-timeout=60
clock-format=%H:%M
EOF

sudo mkdir -p /usr/share/xsessions
sudo tee /usr/share/xsessions/xfce.desktop > /dev/null << 'EOF'
[Desktop Entry]
Name=Xfce Session
Comment=Use this session to run Xfce as your desktop environment
Exec=startxfce4
Type=Application
DesktopNames=XFCE
EOF

sudo systemctl enable lightdm

echo "[6/6] Dang cai dat va cau hinh OpenSSH..."
sudo pacman -S openssh --noconfirm
sudo systemctl enable sshd
sudo systemctl start sshd

echo "=========================================="
echo "  CAI DAT HOAN TAT!"
echo "=========================================="
echo ""
echo "📋 THONG TIN QUAN TRONG:"
echo "1. Khoi dong lai may: sudo reboot"
echo "2. Dang nhap bang LightDM (chi Xfce4)"
echo "3. Kiem tra SSH: sudo systemctl status sshd"
echo "4. Ket noi SSH: ssh user@ip-address"
echo ""

</details>
bash

# Cấp quyền thực thi và chạy
chmod +x ~/xfce.sh
./xfce.sh

🔧 Cấu hình sau cài đặt
Công việc	Lệnh
🔍 Kiểm tra LightDM	sudo systemctl status lightdm
🔍 Kiểm tra SSH	sudo systemctl status sshd
⚙️ Tùy chỉnh LightDM	sudo nano /etc/lightdm/lightdm.conf
🔑 Đổi mật khẩu	passwd
🌐 Kiểm tra IP	ip addr hoặc hostname -I
❗ Xử lý lỗi thường gặp
🚨 Lỗi	💡 Giải pháp
LightDM không khởi động	sudo systemctl start lightdm
Màn hình đen	Cài driver đồ họa: sudo pacman -S mesa
SSH không kết nối	Kiểm tra firewall: sudo systemctl stop firewalld
Lỗi pacman	Kiểm tra Internet: ping google.com
Không có quyền sudo	Chạy với tài khoản root: su -
🛠️ Tùy chỉnh script
📦 Thêm gói phần mềm
bash

sudo pacman -S xfce4 xfce4-goodies firefox vlc --noconfirm

🔄 Đổi sang SDDM
bash

sudo pacman -S sddm --noconfirm
sudo systemctl enable sddm
sudo systemctl disable lightdm

🔐 Tự động đăng nhập
bash

# Mở file cấu hình
sudo nano /etc/lightdm/lightdm.conf

# Thêm dòng dưới [Seat:*]
autologin-user=username
autologin-session=xfce

🎨 Đổi hình nền đăng nhập
bash

# Chỉnh sửa file cấu hình greeter
sudo nano /etc/lightdm/lightdm-gtk-greeter.conf

# Thay đổi dòng background
background=/path/to/your/image.jpg

❓ Hỏi đáp
<details> <summary><b>Script có chạy trên Manjaro/EndeavourOS không?</b></summary>

Có, nhưng có thể cần điều chỉnh nhẹ vì một số bản phân phối sử dụng kho riêng.
</details><details> <summary><b>Tại sao LightDM chỉ hiển thị Xfce4?</b></summary>

Script được thiết kế chỉ hiển thị Xfce4 để đơn giản hóa và tránh nhầm lẫn cho người dùng mới.
</details><details> <summary><b>Làm sao để gỡ bỏ hoàn toàn?</b></summary>
bash

sudo pacman -Rns xfce4 xfce4-goodies lightdm openssh
sudo systemctl disable lightdm sshd

</details><details> <summary><b>Có cần cài driver đồ họa riêng không?</b></summary>

Script cài Xorg cơ bản. Nếu dùng NVIDIA/AMD, cần cài driver riêng sau:

    NVIDIA: sudo pacman -S nvidia

    AMD: sudo pacman -S mesa xf86-video-amdgpu

</details>
🤝 Đóng góp

Mọi đóng góp đều được hoan nghênh!

    Fork repository

    Tạo branch mới (git checkout -b feature/AmazingFeature)

    Commit thay đổi (git commit -m 'Add some AmazingFeature')

    Push lên branch (git push origin feature/AmazingFeature)

    Mở Pull Request

📄 Giấy phép

Phân phối dưới giấy phép MIT License. Xem file LICENSE để biết thêm chi tiết.
🌟 Ủng hộ

Nếu bạn thấy dự án này hữu ích, hãy:

    ⭐ Star repository

    🍴 Fork và chia sẻ

    🐛 Báo lỗi hoặc gợi ý tính năng mới

👨‍💻 Tác giả: Khoa Phan
🐙 GitHub: DKhoa25
📧 Email: ddkhoa14086@gmail.com
<div align="center">

Made with ❤️ for Arch Linux community

⬆ Quay lại đầu trang
</div>
