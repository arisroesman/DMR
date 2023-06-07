SETTING UPDATE DATABASE SERVER KRAP DAN DATABASE 10.28

Supaya kita mendapat Database KRAP, DMRID dan BM DMR yang selalu up to date pada Pi-star MMDVM, berikut ini adalah cara untuk mendapatkannya :
Jalankan SSH pada menu [Configuration] [Expert]
    Login     : pi-star
    Password  : raspberry

Kemudian ketik :

rpi-rw
sudo nano /usr/local/sbin/HostFilesUpdate.sh

(untuk memudahkan, copy baris tulisan yang dikehendaki dari README ini, lalu pada kursor SSH editing klik kanan, lalu Ctrl+v di “Paste from Browser” lalu tekan enter)

Yang Pertama, Untuk menyederhanakan Host List pada DMR Configuration dan menambah DMR Server HB_KRAP_DMR, Server HB_DMRID1 dan Server HB_DMRID2 Cari tulisan di baris yang seperti ini:
curl --fail -o ${DMRHOSTS} -s http://www.pistar.uk/downloads/DMR_Hosts.txt

Tambahkan symbol pagar (#) didepannya seperti dibawah ini
#curl --fail -o ${DMRHOSTS} -s http://www.pistar.uk/downloads/DMR_Hosts.txt

Tambahkan tulisan dibaris dibawah nya
curl --fail -o ${DMRHOSTS} -s https://raw.githubusercontent.com/arisroesman/DMR/main/DMR_Hosts.txt

Akan terlihat seperti ini
#curl --fail -o ${DMRHOSTS} -s http://www.pistar.uk/downloads/DMR_Hosts.txt
curl --fail -o ${DMRHOSTS} -s https://raw.githubusercontent.com/arisroesman/DMR/main/DMR_Hosts.txt

Yang kedua, memindahkan source database ke server kita yang akan selalu up-to-date
Cari tulisan di baris yang seperti ini:

curl --fail -o ${DMRIDFILE} -s http://www.pistar.uk/downloads/DMRIds.dat

Tambahkan symbol pagar (#) didepannya seperti ini
#curl --fail -o ${DMRIDFILE} -s http://www.pistar.uk/downloads/DMRIds.dat

Tambahkan tulisan berikut dibawah nya
curl --fail -o ${DMRIDFILE} -s https://raw.githubusercontent.com/arisroesman/DMR/main/DMRIds.dat

Hingga akan terlihat seperti ini:
#curl --fail -o ${DMRIDFILE} -s http://www.pistar.uk/downloads/DMRIds.dat
curl --fail -o ${DMRIDFILE} -s https://raw.githubusercontent.com/arisroesman/DMR/main/DMRIds.dat

Jika sudah selesai dan di cek ulang, tekan ctrl-x untuk keluar, pastikan dengan mengetik “y“ untuk menyimpan file SSH nya, tekan enter untuk tetap menggunakan nama file yang sama.
Lalu jalankan :

sudo pistar-update

atau

sudo HostFilesUpdate.sh

Tunggu proses update hingga dipastikan selesai (tanda sudah selesai proses layar kembali ke tampilan seperti awal login)

Klik menu [Configuration] dan konfirmasi meninggalkan pengeditan ssh.

Proses ini cukup sekali saja, untuk selanjutnya kita bisa memilih server HB_KRAP_DMR atau BM Server langsung tanpa harus berulang-ulang merubah lagi SSH lagi.
