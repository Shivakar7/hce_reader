
# HCE Reader (Android)

This project demonstrates how to build an **NFC Reader** that communicates with an Android device running **Host Card Emulation (HCE)**.

The reader sends APDU commands to an HCE-enabled phone and receives responses from the emulated card.

This project is designed to work with:

👉 https://github.com/<your-username>/hce_card

---

## Overview

The application uses Android's **NFC Reader Mode** to detect ISO-DEP compatible devices and communicate with them using APDU commands.

When a phone running the `hce_card` app is tapped, the reader:

1. Detects the NFC device
2. Sends a SELECT AID APDU command
3. Receives a response APDU from the emulated card

---

## Architecture


HCE Card (Android Phone)
↑
NFC
↓
Reader App (Android)
↓
IsoDep API
↓
APDU Commands


Communication happens through the **ISO-DEP protocol**, which supports structured APDU command exchanges.

---

## Project Structure


hce_reader/
├── app/
│ ├── src/main/java/.../MainActivity.kt
│ ├── NFCReader.kt
│ └── AndroidManifest.xml
└── README.md


Key components:

| Component | Description |
|---|---|
| `NfcAdapter` | Enables NFC reader mode |
| `IsoDep` | Communicates using APDU commands |
| `MainActivity` | Handles NFC detection |

---

## Requirements

- Android device with **NFC support**
- Android **5.0+**
- NFC enabled

---

## Setup

1. Clone the repository

```bash
git clone https://github.com/<your-username>/hce_reader.git
```

2. Open in Android Studio

3. Run the app on an Android device with NFC.

## Usage

Launch the reader app.

Tap the phone running the hce_card app.

The reader sends APDU commands.

The HCE card app responds with APDU responses.

## Example APDU Communication

Reader sends:

00 A4 04 00 <AID>

Card responds:

90 00

Sample flow:

Reader → SELECT AID
Card   → OK

Reader → REQUEST DATA
Card   → RESPONSE DATA
Debugging

Enable logs to monitor APDU communication.

## Example:

Sending APDU: 00A40400...
Received: 9000

## Related Project

Card implementation:

👉 https://github.com/
<your-username>/hce_card
