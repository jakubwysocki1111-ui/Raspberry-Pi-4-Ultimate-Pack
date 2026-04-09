
# Kompletny zestaw do postawienia własnego serwera domowego na Raspberry Pi 4 oraz Pi 5.

## Wymagania sprzętowe

| Typ        | RAM  |
|------------|------|
| Minimalne  | 4 GB |
| Zalecane   | 8 GB |
___
## Struktura folderu
```
pi-kit/
├── KOMENDY.txt                    ← START TUTAJ — wszystkie komendy
├── README.md                      ← ten plik
├── docker/
│   ├── docker-compose.yml         ← definicja wszystkich serwisów
│   ├── .env                       ← twoje hasła i konfiguracja
│   ├── pihole/                    ← dane Pi-hole
│   ├── homeassistant/             ← konfiguracja Home Assistant
│   ├── n8n/                       ← workflow n8n
│   ├── portainer/                 ← dane Portainer
│   ├── zigbee2mqtt/               ← konfiguracja Zigbee
│   ├── wireguard/                 ← konfiguracja VPN
│   ├── nginx-proxy/               ← dane Nginx Proxy Manager
│   ├── homepage/config/           ← konfiguracja dashboardu
│   ├── glances/                   ← konfiguracja monitora
│   └── retropie/                  ← ROMs i konfiguracja emulatora
├── scripts/
│   ├── 00_install.sh              ← instalacja Docker i systemu
│   ├── 01_configure.sh            ← konfiguracja IP i plików
│   ├── 02_start.sh                ← start wszystkich kontenerów
│   ├── 03_verify.sh               ← weryfikacja czy wszystko działa
│   └── manage.sh                  ← zarządzanie na co dzień
└── docs/
    └── INSTRUKCJA_SERWISOW.md     ← szczegóły każdego serwisu
```
___
## Szybki start (TL;DR)
```bash
# 1. Skopiuj folder na Pi
scp -r pi-kit pi@TWOJE_IP:~/pi-kit

# 2. Na Pi — instalacja
chmod +x ~/pi-kit/scripts/*.sh
bash ~/pi-kit/scripts/00_install.sh

# 3. Wyloguj się i zaloguj ponownie, potem:
nano ~/docker/.env          # wpisz hasła
bash ~/pi-kit/scripts/01_configure.sh
bash ~/pi-kit/scripts/02_start.sh
bash ~/pi-kit/scripts/03_verify.sh

## Wszystkie szczegóły znajdują sie w plikach KOMENDY.txt i docs/INSTRUKCJA_SERWISOW.md
```

##  Serwisy

| Serwis           | Port        | Opis                          |
|------------------|------------|-------------------------------|
| Homepage         | 3000       | Strona startowa — launcher    |
| Home Assistant   | 8123       | Smart home hub                |
| Pi-hole          | 8080       | DNS adblocker                 |
| n8n              | 5678       | Automatyzacja workflow        |
| Portainer        | 9000       | Zarządzanie Dockerem          |
| Zigbee2MQTT      | 8081       | Urządzenia Zigbee             |
| Nginx Proxy      | 81         | Reverse proxy                 |
| Glances          | 61208      | Monitor systemu               |
| WireGuard        | 51820/UDP  | VPN                           |
