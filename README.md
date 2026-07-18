# Pet Feeder Web Application

> Forked from my other GitHub account for showcase on this profile.

Full-stack IoT pet feeder: schedule or manually dispense food via a Flask + MQTT backend, browser UI, and ESP8266 firmware.

<!-- screenshot: docs/screenshots/hero.png -->

## Overview

Users log in, manage feeding schedules, and trigger an immediate dispense. The Flask API talks to an MQTT broker; ESP8266 firmware listens and drives the feeder hardware. The ESP8266 can also run in AP mode for Wi-Fi setup.

## Links

- **Repo:** https://github.com/MS-Jahan/pet-feeder
- **Live demo:** self-hosted only (no public URL) — run Flask locally and point the ESP8266 at your MQTT broker

## Key Features

- User authentication
- CRUD feeding schedules
- Manual “Dispense” control
- MQTT realtime device control
- ESP8266 Wi-Fi configuration (AP mode)

## Tech Stack

| Layer | Stack |
| :--- | :--- |
| Backend | Python, Flask, Flask-CORS, Paho-MQTT, SQLite |
| Frontend | HTML/CSS/JS, Materialize CSS, SweetAlert2 |
| Firmware | C++ / Arduino on ESP8266 (`esp_pet_dispense.ino`) |

## Dependencies

Backend (`backend/requirements.txt`):

- `Flask`, `Flask-Cors`, `paho-mqtt`, `pytz`, `requests`

```bash
cd backend
pip install -r requirements.txt
```

Firmware: Arduino IDE + ESP8266 core + MQTT client library matching your sketch includes.

## Components

1. **Backend** (`backend/`) — auth, schedule CRUD, MQTT publish, SQLite
2. **Frontend** (`frontend/`) — login + main app pages
3. **ESP8266** (`esp_pet_dispense.ino`) — Wi-Fi, MQTT subscribe, hardware control

## How to Run Locally

1. Install backend deps (above).
2. Start the Flask app (creates SQLite DB on first run):

```bash
cd backend
python main.py
```

3. Flash `esp_pet_dispense.ino` to the ESP8266; configure Wi-Fi (AP mode) and MQTT broker host/credentials in firmware + backend.
4. Open the frontend in a browser (serve `frontend/` or open the HTML as your setup requires).

### Usage

1. Log in with your user ID and password.
2. Add / edit / delete feeding times.
3. Use **Dispense** for a manual feed.

## Security Notes

- Passwords are stored in plain text in the current implementation — hash them before any real deployment.
- Use strong credentials, HTTPS, and encrypted MQTT in production.

## License

See repository license / upstream fork terms.
