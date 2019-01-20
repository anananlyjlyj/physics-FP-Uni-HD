# F01 Grundpraktikum Elektronik

- [E01 instrcution](https://www.physi.uni-heidelberg.de/Einrichtungen/FP/anleitungen/E01.pdf)
- Literatur: [elektronik_straumann](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/elektronik_straumann.pdf)

- [Protocol](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/Protocol.pdf)

## Teil I: Verstärkerschaltung mit einem Transistor in Emitterschaltung

- Bestimmung der Verstärkung und Phasenverschiebung: [Figure 0](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/First_tek00000.png)
- Messung des Frequenzgangs: [Frequenzgang_plot](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/Frequenzgang_plot.xlsx)

## Teil II: Verstärkerschaltung mit einem Transistor in Kollektorschaltung

- Bestimmung der Verstärkung und Phasenverschiebung: [Figure 1](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/Second_tek00001.png)
- Messung des Frequenzgangs: leider vergessen zu messen:(
- Messung der Länge eines Koaxialkabels: [Länge eines Koaxialkabels](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/L%C3%A4nge%20eines%20Koaxialkabels.jpg)
- Bestimmung der Wellenimpedanz eines Kabels: [Wellenimpedanz eines Kabels(vorher)](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/Wellenimpedanz%20eines%20Kabels(vorher).jpg) & [Wellenimpedanz eines Kabels(nachher)](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/Wellenimpedanz%20eines%20Kabels(nachher).jpg)

## Teil III: Aufbau eines PID-Reglers zur Drehzahlregelung eines Motors

![PID-Regler](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/PID-Regler.jpg)

- Inbetriebnahme der Schaltung - Überprüfung der Schaltung: 
  - [P-Regler an](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00000.png) 
  - [P-Regler aus, niedrige Spannung](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00001.png)
  - [P-Regler aus, hohe Spannung](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00002.png) 
  - [P-Regler an, 10 Skt](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00003.png) -> [bessere Aüflösung](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00004.png)
- PID-Regelung
  - P-Regelung:
    - [Skt = 0](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00005.png)
    - [Skt = 5](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00006.png)
    - [Skt = 10](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00007.png)
    - [Skt = 50](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00008.png)
    - Differenz zwei Kanäle 
      - [Skt = 50](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00009.png)
      - [Skt = 140](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00010.png)
  - PI-Regelung: 
    - [P-Skt = 0, I-Skt = 0](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00011.png)
    - [P-Skt = 0, I-Skt = 10](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00012.png)
    - [P-Skt = 10, I-Skt = 0](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00013.png)
    - [P-Skt = 50, I-Skt = 20](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00014.png)
    - [P-Skt = 5, I-Skt = 80](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00015.png)
  - PD-Regelung: 
    - [P-Skt = 0, D-Skt = 0](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00016.png)
    - [P-Skt = 10, D-Skt = 0](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00017.png)
    - [P-Skt = 0, D-Skt = 10](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00018.png)
    - [P-Skt = 50, D-Skt = 10](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00019.png)
    - [P-Skt = 10, D-Skt = 50](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00020.png)
    - [P-Skt = 50, D-Skt = 50](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00021.png)
  - PID-Regelung: 
    - [P-Skt = 0, I-Skt = 0, D-Skt = 0](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00022.png)
    - [P-Skt = 60, I-Skt = 0, D-Skt = 50](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00023.png)
- Bestimmung der optimalen Regelung
  - Einschaltung der Glühbirne:
    - [mit Reglung](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00024.png)
    - [ohne Reglung](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00025.png)
  - Modulation eines Sinussignals: 
    - f = 0.2 Hz
      - [mit Regelung](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00026.png)
      - [ohne Regelung](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00027.png)
    - f = 2 Hz
      - [mit Regelung](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00028.png)
      - [ohne Regelung](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/E01%20Grundpraktikum%20Elektronik/tek00029.png)
