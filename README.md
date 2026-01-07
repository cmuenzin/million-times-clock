# Million-Times-Clock

Meine eigene Version von „A Million Times“, der kinetischen Uhren-Installation
von [Humans since 1982](https://en.wikipedia.org/wiki/Humans_since_1982):
24 Uhren mit je zwei Zeigern, jeder Zeiger an einem eigenen Schrittmotor, die
zusammen die Uhrzeit schreiben.

**Stand:** angefangen 2025. Die Trennung zwischen Uhrenlogik und Hardware
steht, das Rendering der Simulation und der Treiber für die Schrittmotoren
fehlen noch.

**Technik:** Python mit Pygame für die Simulation, MicroPython auf einem ESP32
für die Hardware.

## Aufbau

| Datei | Inhalt |
|---|---|
| `core/clock_controller.py` | Uhrenlogik: Zeigerwinkel in Motorschritte umrechnen, beide Zeiger bewegen |
| `hal/base_stepper.py` | Schnittstelle für einen Schrittmotor |
| `hal/sim_stepper.py` | Schrittmotor in der Simulation |
| `hal/hw_stepper.py` | Schrittmotor auf dem ESP32 (noch leer) |
| `sim/main.py` | Simulation der 24 Uhren mit Pygame |
| `hw/flash.py` | lädt Logik und Treiber per `mpremote` auf den ESP32 |

Dieselbe Uhrenlogik läuft gegen beide Implementierungen der Schnittstelle,
in der Simulation und auf der Hardware.

## Simulation starten

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python sim/main.py
```
