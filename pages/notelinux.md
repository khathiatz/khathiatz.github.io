#Trải nghiệm Linux

Lỗi lúc cài đặt
debian-12.5.0-amd64-DVD-1.iso
linux-lite-6.6-64bit.iso
inuxmint-21.3-cinnamon-64bit.iso
lubuntu-22.04.4-desktop-amd64.iso
ubuntu-22.04.4-desktop-amd64 (dkpg)
ubuntucinnamon-23.10-desktop-amd64.iso (cài được, hết 100GB ổ cứng không kịp xóa cache)
xubuntu-22.04.4-desktop-amd64.iso (cài đặt quá chậm, đứng hình lúc chọn time zone)

Xài tốt, hơi lag
kubuntu-22.04.4-desktop-amd64.iso

Linux Kubuntu


1  THAO TÁC ==============================
Hien file an Ctrl + H
Copy paste Ctrl + Shift  + C / V





2  TẮT SYSTEM LOG  ĐỂ GIẢM DUNG LƯỢNG Ổ CỨNG ===========================
service rsyslog stop
systemctl disable rsyslog
sudo truncate -s 0 /var/log/syslog

Cài đặt STACER để xóa ngay cache vừa cài đặt
sudo add-apt-repository ppa:oguzhaninan/stacer -y
sudo apt update
sudo apt install stacer -y

sudo apt update
sudo apt -y install stacer




0 TẮT LINIX SỬA THỜI GIAN BIOS  ============================
sudo timedatectl set-local-rtc 1

NTP time sync:
sudo apt-get update && sudo apt-get upgrade # For fix bug
sudo apt install -f #Thử xóa soft broken
sudo apt install ntp -y
Copy file ntp.conf vào /etc/ntp.conf
systemctl enable ntp.service
systemctl restart ntp.service
systemctl status ntp.service # For check


FLATHUB ===========================================
sudo apt install flatpak
sudo apt install software-properties-common -y
sudo add-apt-repository ppa:flatpak/stable (skip if error)
sudo apt update
sudo apt install flatpak
sudo apt install gnome-software-plugin-flatpak -y
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo


- Mission Center: flatpak install flathub io.missioncenter.MissionCenter -y
- Extension Manager: flatpak install flathub com.mattjakeman.ExtensionManager -y
(Resource Manager by NormalUser69)
- OnlyOffice: flatpak install flathub org.onlyoffice.desktopeditors -y
- LibreCAD: flatpak install flathub org.librecad.librecad -y
- GNOME Network Display: flatpak install flathub org.gnome.NetworkDisplays -y
- Volume Control: flatpak install flathub org.pulseaudio.pavucontrol -y
- Surfshark: flatpak install flathub com.surfshark.Surfshark -y
- Standarnote: flatpak install flathub org.standardnotes.standardnotes -y
- Brave: flatpak install flathub com.brave.Browser -y
- Firefox: flatpak install flathub org.mozilla.firefox -y
- Telegram: flatpak install flathub org.telegram.desktop -y
- Nomacs - picture : flatpak install flathub org.nomacs.ImageLounge -yy
- PeaZip: flatpak install flathub io.github.peazip.PeaZip -y
- Wine: flatpak install flathub org.winehq.Wine -y
flatpak install flathub org.phoenicis.playonlinux -y
- Steam: flatpak install com.valvesoftware.Steam -y
- RetroDESK: flatpak install flathub net.retrodeck.retrodeck -y


* UNINSTALL:
flatpak uninstall --delete-data <appid>
flatpak uninstall --delete-data org.standardnotes.standardnotes -y
flatpak uninstall --delete-data io.github.jorchube.monitorets -y
flatpak uninstall --delete-data -y com.valvesoftware.Steam
flatpak uninstall --delete-data org.freecad.FreeCAD -y
flatpak uninstall --delete-data com.google.AndroidStudio -y







3  CÀI SOFTWARE CENTER ====================================
Cai software center
https://linuxconfig.org/gui-software-installers-for-kali-linux

sudo apt update
sudo apt install gnome-software

Open root access and edit "/etc/apt/sources.list"
add
deb http://kali.download/kali/ kali-rolling main non-free contrib
deb http://ftp.debian.org/debian stable main contrib non-free
deb http://http.kali.org/kali kali-rolling main non-free contrib
deb http://http.kali.org/kali kali-last-snapshot main non-free contrib
deb http://http.kali.org/kali kali-experimental main non-free contrib
deb-src http://http.kali.org/kali kali-rolling main non-free contrib

sudo apt update
sudo apt install synaptic

Find "Software"
Done.






3.1  CÀI GÕ TIẾNG VIỆT (UBUNTU) ====================================
sudo apt install ibus-unikey
ibus restart
ibus-setup


3.1  CÀI GÕ TIẾNG VIỆT ====================================
Kali Linux Live: Chạy Fcitx để cài Bamboo
(https://debian.pkgs.org/12/debian-main-arm64/fcitx5-bamboo_1.0.2-1_arm64.deb.html)
sudo apt-get update
sudo apt-get install fcitx5-bamboo -y
# Config cho hệ thống dùng fcitx thay cho ibus.
im-config -n fcitx
mkdir -p ~/.config/autostart && cp /usr/share/applications/org.fcitx.Fcitx5.desktop ~/.config/autostart
Logout rồi vào lại
Thiết lập cách gõ

sudo apt-get -y install fcitx
sudo apt-get install make golang libx11-dev libxtst-dev libgtk-3-dev
sudo apt install git -y
git clone https://github.com/BambooEngine/ibus-bamboo.git
cd ibus-bamboo
sudo make install

3.2 CÀI GÕ TIẾNG VIỆT ====================================
(https://tinhte.vn/thread/fix-loi-khi-cai-dat-va-su-dung-bo-go-tieng-viet-ibus-bamboo-tren-moi-truong-kde-plasma-desktop.3131791)

Fix Lỗi Khi Cài Đặt Và Sử Dụng Bộ Gõ Tiếng Việt Ibus-Bamboo Trên Môi Trường KDE Plasma Desktop

1. Cài đặt các gói cần thiết và cài đặt ibus-bamboo

Mở Konsole (Terminal) lên và nhập vào những lệnh sau:

sudo apt install im-config ibus ibus-gtk ibus-gtk3 -y
sudo add-apt-repository ppa:bamboo-engine/ibus-bamboo
sudo apt-get update
sudo apt-get install ibus-bamboo && ibus restart
Khi ibus restart, lúc này sẽ bị lỗi, thoát ra và làm các bước tiếp theo.

2. Mở duyệt file (Dolphin)

Ctrl + H để hiện những file ẩn.
Thêm những dòng sau đây vào file /home/<username>/ .bashrc và save lại.
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus

3. Khởi động Ibus Prefences

Tab General:
- Keyboard Shortcuts: Thiết lập phím tắt để chuyển đổi giữa các bộ gõ (thiết lập thế nào tùy vào thói quen của bạn)
- Candidates orientation: chọn Horizontal
- Show property panel: Ẩn hoặc hiện thanh điều khiển của ibus (chọn ẩn đi cho tiện, sau này muốn tùy chỉnh cứ click vào icon ibus trên taskbar là được rồi)
- Show icon on system tray: hiện icon ibus trên Widget system tray (nên bật)
- Embed preedit text in application windows: nên bật
Chuyển qua tab Input Method > Chọn "Add" > Chọn dấu "..." > Chọn "Vietnamese" > add bộ gõ ibus-bamboo vào > Close

4. Khởi động app Input Method (không phải tab Input Method của Ibus nhé)
Chọn OK > Chọn Yes > chọn hàng "activate Intelligent Input Bus (Ibus)" > OK > OK lần nữa

5. Khởi động lại máy! Từ bây giờ Ibus-Bamboo sẽ luôn khởi động cùng hệ thống, tiện lợi.
Lưu ý: Khi bị lỗi gạch chân hoặc nhảy chữ, dùng Shift + ~ để thay đổi chế độ gõ khác cho phù hợp!



PULSE AUDIO: ENABLE FRONT 3.5 AUDIO JACK ===========================================
/// SAI
sudo apt install git -y
git clone git://anongit.freedesktop.org/pulseaudio/pulseaudio
OR: git clone http://anongit.freedesktop.org/git/pulseaudio/pulseaudio.git
cd pulseaudio
sudo make install
//SAI

sudo apt install pavucontrol (hoặc gõ pavucontrol để Terminal tự gợi ý)
	OR: sudo apt-get install pavucontrol -y
  OR: (Volume Control) flatpak install flathub org.pulseaudio.pavucontrol -y
open - PulseAudio Volume Control.
tap - Configuration tab.
Select profile - Analog Stereo Duplex (unplugged).
tap - Output Devices.
Select Port - Headphones (unplugged).
Done.


SURFSHARK ===========================================
sudo snap install curl 
curl -f https://downloads.surfshark.com/linux/debian-install.sh --output surfshark-install.sh #gets the installation script
cat surfshark-install.sh #shows script's content
sh surfshark-install.sh #installs surfshark
Lỗi thì tách ra chạy riêng: apt-get install -y surfshark


UBUNTU: TRÌNH CHIẾU LÊN TV ===========================
Cài app "GNOME Network Display"
Cài add onon âm thanh (https://gstreamer.freedesktop.org/documentation/installing/on-linux.html?gi-language=c), copy nguyên đoạn code
apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio



UBUNTU: THÊM TÙY CHỌN "ADD TO DESKTOP" ===========================
https://ubuntuhandbook.org/index.php/2020/05/shortcut-desktop-ubuntu-20-04/
sudo apt install gnome-shell-extension-manager
Tìm app "extension" -> chọn Browse -> tìm từ "add to desktop" -> bấm install


UBUNTU: CHUYỂN TOP PANEL XUỐNG DƯỚI CÙNG =============================
(https://extensions.gnome.org/extension/949/bottompanel/)
(https://github.com/Thoma5/gnome-shell-extension-bottompanel)
git clone https://github.com/Thoma5/gnome-shell-extension-bottompanel.git
cp -r gnome-shell-extension-bottompanel ~/.local/share/gnome-shell/extensions/bottompanel@tmoer93


WAYDROID
===========================================
Link: https://docs.waydro.id/usage/install-on-desktops
sudo apt install curl ca-certificates -y
curl -s https://repo.waydro.id | sudo bash
sudo apt install waydroid -y
* If need autostart: sudo systemctl enable --now waydroid-container

* Google Play Certification:
sudo waydroid shell
ANDROID_RUNTIME_ROOT=/apex/com.android.runtime ANDROID_DATA=/data ANDROID_TZDATA_ROOT=/apex/com.android.tzdata ANDROID_I18N_ROOT=/apex/com.android.i18n sqlite3 /data/data/com.google.android.gsf/databases/gservices.db "select * from main where name = \"android_id\";"
- Use the string of numbers printed by the command to register the device on your Google Account at https://www.google.com/android/uncertified
- Give the Google services some minutes to reflect the change, then restart waydroid


* Set Phone Type or Device Model:
sudo nano /var/lib/waydroid/waydroid.cfg
- Add or modify the following properties under the [properties] section:
ro.product.waydroid.brand=samsung
ro.product.waydroid.device=a50
ro.product.waydroid.manufacturer=samsung
ro.product.waydroid.model=SM-A550F
ro.product.waydroid.name=a50dd
- Save and type:
sudo waydroid upgrade -o


* Reinstalling Waydroid:
waydroid session stop
sudo waydroid container stop
sudo apt remove waydroid -y
--> After you removed Waydroid, reboot.
Then on
