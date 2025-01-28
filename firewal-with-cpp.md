## Firewal with cpp
Firewall ini akan berbasis pada pemfilteran IP dan port, dan akan menggunakan socket programming untuk memonitor lalu lintas jaringan. Firewall ini akan memeriksa apakah koneksi masuk dan keluar dibolehkan atau diblokir berdasarkan daftar IP dan port yang sudah ditentukan.
**Langkah-langkah Pembuatan:**

### 1. Persiapan dan Instalasi

**Bergantung pada OS yang digunakan**, berikut adalah langkah-langkah instalasi perangkat yang diperlukan:

#### Untuk Linux (Ubuntu/Debian):
- Pastikan C++ dan alat pengembangan sudah terpasang.

```bash
sudo apt update
sudo apt install g++ make libpcap-dev
```

`libpcap` digunakan untuk menangkap paket jaringan.

#### Untuk Windows:
1. Install **MinGW** atau **MSYS2** untuk compiler C++.
2. Install **WinPcap** untuk menangkap paket jaringan.

---

### 2. Struktur Folder

Proyek ini akan memiliki struktur folder berikut:
```
simple-firewall/
│
├── src/                  # Kode sumber C++
├── bin/                  # File hasil kompilasi
├── include/              # Header files
├── README.md             # Dokumentasi proyek
└── Makefile              # Skrip build (hanya jika menggunakan make)
```

---

### 3. Kode C++ untuk Firewall

#### a. File Header (`firewall.h`)
**`firewall.h`** akan berisi deklarasi fungsi dan struktur yang diperlukan.

```cpp
#ifndef FIREWALL_H
#define FIREWALL_H

#include <pcap.h>
#include <netinet/in.h>
#include <netinet/ip.h>
#include <arpa/inet.h>
#include <iostream>
#include <vector>
#include <string>

class Firewall {
public:
    Firewall();
    ~Firewall();

    // Fungsi untuk memulai firewall dan menangkap paket
    void startFirewall(const std::string& interface);

    // Fungsi untuk memblokir atau mengizinkan IP dan port tertentu
    void allowIP(const std::string& ip);
    void blockIP(const std::string& ip);
    void allowPort(int port);
    void blockPort(int port);

private:
    pcap_t* handle;
    std::vector<std::string> allowedIPs;
    std::vector<std::string> blockedIPs;
    std::vector<int> allowedPorts;
    std::vector<int> blockedPorts;

    // Fungsi untuk memproses paket yang diterima
    static void packetHandler(u_char* userData, const struct pcap_pkthdr* pkthdr, const u_char* packet);
    
    // Fungsi untuk memeriksa apakah paket boleh diteruskan atau diblokir
    bool isAllowed(const struct ip* ipHeader, int port);
};

#endif
```

#### b. Implementasi Firewall (`firewall.cpp`)
**`firewall.cpp`** mengimplementasikan fungsi-fungsi yang dideklarasikan di `firewall.h`.

```cpp
#include "firewall.h"

Firewall::Firewall() {
    // Inisialisasi firewall
}

Firewall::~Firewall() {
    // Menutup koneksi pcap
    if (handle) {
        pcap_close(handle);
    }
}

void Firewall::allowIP(const std::string& ip) {
    allowedIPs.push_back(ip);
}

void Firewall::blockIP(const std::string& ip) {
    blockedIPs.push_back(ip);
}

void Firewall::allowPort(int port) {
    allowedPorts.push_back(port);
}

void Firewall::blockPort(int port) {
    blockedPorts.push_back(port);
}

bool Firewall::isAllowed(const struct ip* ipHeader, int port) {
    std::string srcIP = inet_ntoa(ipHeader->ip_src);

    // Cek apakah IP ini diblokir
    for (const auto& ip : blockedIPs) {
        if (srcIP == ip) return false;
    }

    // Cek apakah IP ini diizinkan
    for (const auto& ip : allowedIPs) {
        if (srcIP == ip) return true;
    }

    // Cek apakah port ini diizinkan
    for (const auto& allowedPort : allowedPorts) {
        if (port == allowedPort) return true;
    }

    // Jika tidak ada aturan, blokir
    return false;
}

void Firewall::packetHandler(u_char* userData, const struct pcap_pkthdr* pkthdr, const u_char* packet) {
    const struct ip* ipHeader = reinterpret_cast<const struct ip*>(packet + 14);  // Skip Ethernet header

    // Cek port untuk TCP
    if (ipHeader->ip_p == IPPROTO_TCP) {
        const struct tcphdr* tcpHeader = reinterpret_cast<const struct tcphdr*>(packet + 14 + (ipHeader->ip_hl << 2));
        int port = ntohs(tcpHeader->th_sport);
        
        if (!static_cast<Firewall*>(userData)->isAllowed(ipHeader, port)) {
            std::cout << "Blocked packet from IP: " << inet_ntoa(ipHeader->ip_src) << " on port: " << port << std::endl;
        }
    }
}

void Firewall::startFirewall(const std::string& interface) {
    char errbuf[PCAP_ERRBUF_SIZE];
    handle = pcap_open_live(interface.c_str(), BUFSIZ, 1, 1000, errbuf);
    if (handle == nullptr) {
        std::cerr << "Error opening interface " << interface << ": " << errbuf << std::endl;
        return;
    }

    std::cout << "Firewall running on interface " << interface << std::endl;
    pcap_loop(handle, 0, packetHandler, reinterpret_cast<u_char*>(this));
}
```

#### c. Fungsi Utama (`main.cpp`)

**`main.cpp`** akan menjalankan firewall dan mengatur konfigurasi.

```cpp
#include <iostream>
#include "firewall.h"

int main() {
    Firewall firewall;

    // Menambahkan aturan firewall
    firewall.allowIP("192.168.1.10");
    firewall.blockIP("192.168.1.20");
    firewall.allowPort(80); // HTTP
    firewall.blockPort(22); // SSH

    // Memulai firewall pada interface 'eth0' (ganti sesuai dengan interface yang digunakan)
    firewall.startFirewall("eth0");

    return 0;
}
```

---

### 4. Kompilasi dan Build

#### Makefile (Jika menggunakan `make`)

```make
CXX = g++
CXXFLAGS = -std=c++11 -Wall
LDFLAGS = -lpcap

SRC = src/firewall.cpp src/main.cpp
OBJ = $(SRC:.cpp=.o)
EXEC = bin/firewall

all: $(EXEC)

$(EXEC): $(OBJ)
	$(CXX) -o $(EXEC) $(OBJ) $(LDFLAGS)

%.o: %.cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@

clean:
	rm -f $(OBJ) $(EXEC)
```

Dengan menggunakan `make`, cukup jalankan perintah berikut di terminal:
```bash
make
```

---

### 5. Dokumentasi `README.md`

Berikut adalah contoh `README.md` yang mendokumentasikan cara menggunakan firewall ini.

```markdown
# Simple Firewall in C++

## Deskripsi
Ini adalah implementasi firewall sederhana menggunakan C++ yang memfilter koneksi berdasarkan alamat IP dan port. Firewall ini menggunakan pustaka `libpcap` untuk menangkap dan memeriksa paket jaringan.

## Persyaratan
- C++11
- `libpcap` (Linux) atau `WinPcap` (Windows)

### Instalasi (Linux)
1. Instal `g++` dan `libpcap-dev`:
   ```bash
   sudo apt update
   sudo apt install g++ make libpcap-dev
   ```

2. Kompilasi program:
   ```bash
   make
   ```

### Instalasi (Windows)
1. Instal **MinGW** atau **MSYS2**.
2. Instal **WinPcap**.
3. Kompilasi dengan MinGW/MSYS2.

## Penggunaan

1. Jalankan firewall dengan mengganti interface `eth0` di `main.cpp` dengan interface yang kamu gunakan (misalnya `wlan0` untuk Wi-Fi).
2. Untuk menambahkan aturan firewall:
   - Gunakan `allowIP("192.168.1.10")` untuk mengizinkan IP.
   - Gunakan `blockIP("192.168.1.20")` untuk memblokir IP.
   - Gunakan `allowPort(80)` untuk mengizinkan port.
   - Gunakan `blockPort(22)` untuk memblokir port.

3. Jalankan program:
   ```bash
   ./bin/firewall
   ```


### 6. Menjalankan dan Menguji

Untuk menjalankan firewall, pastikan kamu memiliki hak istimewa yang cukup (misalnya `sudo` di Linux). Setelah itu, jalankan program dengan perintah berikut:

```bash
sudo ./bin/firewall
```

Firewall akan mulai menangkap paket dan memeriksa apakah koneksi diizinkan atau diblokir berdasarkan aturan yang telah ditetapkan.

---

### 7. Kesimpulan

Dengan langkah-langkah di atas, kamu dapat membangun firewall sederhana menggunakan C++ dan `libpcap`, serta mengonfigurasi aturan berbasis IP dan port. Jangan lupa untuk menguji program di berbagai jaringan dan memverifikasi apakah aturan yang kamu buat berjalan dengan baik!
