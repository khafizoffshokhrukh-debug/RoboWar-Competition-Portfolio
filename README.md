# 🤖 RoboWar — Competition Robot

<p align="center">

**🥇 6× 1st Place   |   🥈 2× 2nd Place**

**Combat Robotics • CAD Design • Engineering • Programming**

</p>

---

## 🏆 Project Highlights

> A competition robot developed by a three-member robotics team for RoboWar competitions.

### Results

* 🥇 **6× 1st Place**
* 🥈 **2× 2nd Place**
* 🤖 Multiple RoboWar competitions
* 🛠️ Custom CAD-designed robot
* ⚙️ Mechanical engineering and assembly
* 💻 Custom control software
* 🎥 Real competition battle footage

---

## 👥 Team

This RoboWar project was developed by a **3-member robotics team**, with each member responsible for a different part of the robot development process.

| Member                   | Role                    | Main Responsibilities                                |
| ------------------------ | ----------------------- | ---------------------------------------------------- |
| **Shoxruxmirzo Xafizov** | 🛠️ CAD Designer        | CAD design, technical drawings and mechanical design |
| **Nazarov Asadbek**      | ⚙️ Engineer + 🎮 Driver | Robot assembly, engineering and competition driving  |
| **Narziyev Akbarshox**   | 💻 Coder                | Programming and robot control system                 |

### Team Photo

![Team Photo](Team/team-photo.jpg)

---

# 🛠️ My Role

## CAD Designer — Shoxruxmirzo Xafizov

My main responsibility in this project was the **CAD and mechanical design of the robot**.

I worked on:

* 📐 Creating the robot's CAD model
* 🧩 Designing mechanical components
* 🏗️ Developing the robot structure
* 📏 Preparing technical dimensions
* 🔩 Designing component placement
* 🔄 Improving the mechanical design
* 🛠️ Supporting the team during assembly and testing

### CAD Design
<img width="1224" height="707" alt="Снимок экрана 2026-09-08 121204" src="https://github.com/user-attachments/assets/20d1371b-7fd2-48fc-86b4-e96a33119e66" />
<img width="1378" height="908" alt="Снимок экрана 2026-09-08 121214" src="https://github.com/user-attachments/assets/4a7854a6-e144-41a8-86c8-d8cd01c7c4b6" />
<img width="1292" height="763" alt="Снимок экрана 2026-09-08 121225" src="https://github.com/user-attachments/assets/0e4052b3-39cc-4ffe-99f0-5bf0b12df4ec" />

---

# 🤖 Robot

The RoboWar robot was designed specifically for competition conditions.

The development focused on:

* Mechanical strength
* Compact construction
* Reliable movement
* Effective control
* Fast response
* Easy maintenance
* Competition durability

### Final Robot

![Final Robot](Robot/final-robot.jpg)

### Front View

![Robot Front](Robot/robot-front.jpg)

### Side View

![Robot Side](Robot/robot-side.jpg)

### Top View

![Robot Top](Robot/robot-top.jpg)

---

# ⚙️ Engineering

## Mechanical Development

The robot went through several stages of development before reaching the final competition configuration.

### Development Process

```text
💡 Concept
     ↓
📐 CAD Design
     ↓
🧩 Component Selection
     ↓
🔩 Manufacturing
     ↓
⚙️ Assembly
     ↓
🧪 Testing
     ↓
🔄 Improvements
     ↓
🤖 Final Competition Robot
```

---

# ⚡ Electronics

The robot's electronic system was designed to provide reliable control during competition.

### Main Components

| Component       | Purpose                    |
| --------------- | -------------------------- |
| Microcontroller | ESP 32 WROOM               |
| Motor Driver    | BTS 7960                   |
| Motors          | JGB-370 600rpm             |
| Battery         | Ovonic 4s 1750mah          |
| Wiring          | Silicone Wiring            |
| Bearings        | Go Bilda bearings          |

> The exact components and wiring diagrams are documented in the `Electronics/` folder.

### Radio

<img width="750" height="1000" alt="6f8c0b66-2b55-43e9-a0b4-ee9f98cc9c03" src="https://github.com/user-attachments/assets/5eac0b63-1f07-43f7-aea7-a4a18663b42e" />

### ExpressLRS

<img width="807" height="807" alt="H40ced46e7fe44687a9d74ddbcd711ed5t" src="https://github.com/user-attachments/assets/2f973de5-2879-4366-94cc-73f9f185cfa3" />


---

# 💻 Programming

The robot's control software was developed by **Narziyev Akbarshox**.

The programming was responsible for controlling the robot's electronic and movement systems.

### Code Structure

The source code is available in: Arduino ide

#include <ESP32Servo.h>

#define L_RPWM 25
#define L_LPWM 26

#define R_RPWM 27
#define R_LPWM 14

#define ESC_PIN 13

Servo esc;

#define PWM_FREQ 20000
#define PWM_RES 8

void setup() {
  ledcAttach(L_RPWM, PWM_FREQ, PWM_RES);
  ledcAttach(L_LPWM, PWM_FREQ, PWM_RES);
  ledcAttach(R_RPWM, PWM_FREQ, PWM_RES);
  ledcAttach(R_LPWM, PWM_FREQ, PWM_RES);

  esc.attach(ESC_PIN, 1000, 2000);

  stopMotors();
  
  esc.writeMicroseconds(1000);
  delay(3000);
}

void loop() {


  forward(150);
  delay(2000);

  stopMotors();
  delay(1000);

  backward(150);
  delay(2000);
  
  stopMotors();
  delay(1000);

  turnRight(150);
  delay(1000);

  stopMotors();
  delay(1000);

  turnLeft(150);
  delay(1000);

  stopMotors();
  delay(2000);
}


void forward(int speed) {
  speed = constrain(speed, 0, 255);

  ledcWrite(L_RPWM, speed);
  ledcWrite(L_LPWM, 0);

  ledcWrite(R_RPWM, speed);
  ledcWrite(R_LPWM, 0);
}


void backward(int speed) {
  speed = constrain(speed, 0, 255);

  ledcWrite(L_RPWM, 0);
  ledcWrite(L_LPWM, speed);

  ledcWrite(R_RPWM, 0);
  ledcWrite(R_LPWM, speed);
}


void turnRight(int speed) {
  speed = constrain(speed, 0, 255);

  ledcWrite(L_RPWM, speed);
  ledcWrite(L_LPWM, 0);

  ledcWrite(R_RPWM, 0);
  ledcWrite(R_LPWM, speed);
}


void turnLeft(int speed) {
  speed = constrain(speed, 0, 255);

  ledcWrite(L_RPWM, 0);
  ledcWrite(L_LPWM, speed);

  ledcWrite(R_RPWM, speed);
  ledcWrite(R_LPWM, 0);
}


void stopMotors() {
  ledcWrite(L_RPWM, 0);
  ledcWrite(L_LPWM, 0);

  ledcWrite(R_RPWM, 0);
  ledcWrite(R_LPWM, 0);
}
# 🧪 Testing & Development

Before competitions, the robot went through multiple testing stages.

### 01 — Concept

![Concept](Development/01-concept.jpg)

### 02 — CAD

![CAD](Development/02-cad.jpg)

### 03 — Parts

![Parts](Development/03-parts.jpg)

### 04 — Assembly

![Assembly](Development/04-assembly.jpg)

### 05 — Testing

![Testing](Development/05-testing.jpg)

### 06 — Final Robot

![Final Robot](Development/06-final-robot.jpg)

---

# 🥊 Competition

The robot was tested and improved through multiple RoboWar competitions.

Competition experience helped us improve:

* Robot reliability
* Mechanical design
* Driving strategy
* Control system
* Reaction time
* Repair and troubleshooting
* Competition preparation

### Competition Moments

![Competition](Competition/competition-01.jpg)

![Competition](Competition/competition-02.jpg)

![Competition](Competition/competition-03.jpg)

---

# 🏆 Competition Record

Our team achieved the following results across RoboWar competitions:

| Result           | Number |
| ---------------- | -----: |
| 🥇 **1st Place** |  **6** |
| 🥈 **2nd Place** |  **2** |

## 🥇 6× First Place
<img width="1920" height="2560" alt="photo_2026-07-18_19-14-18" src="https://github.com/user-attachments/assets/12ea847f-6971-4d68-a596-92a68a00ac0d" />


## 🥈 2× Second Place


<img width="1920" height="2560" alt="photo_2026-07-18_19-14-15" src="https://github.com/user-attachments/assets/1da90882-296b-44a8-b79c-557806ad5b86" />



# 🎥 Battle Highlights

Real competition footage and robot battles are available in the project media collection.

### Battle 01

[▶️ Watch Battle 01](https://www.youtube.com/watch?v=ttD957xNLTk)

### Battle 02

[▶️ Watch Battle 02](https://www.youtube.com/watch?v=o5U7KP0Lmo4)

### Competition Highlights

[▶️ Watch Competition Highlights](https://www.youtube.com/shorts/mWc8ZS2Xklg)

---

# 📸 Gallery

## Achieve
<img width="1920" height="2560" alt="photo_2026-07-09_23-42-53" src="https://github.com/user-attachments/assets/bc600847-e294-44f8-9815-2cfafbe4854c" />
ments



## Team

<img width="960" height="1280" alt="photo_2026-07-13_19-55-42" src="https://github.com/user-attachments/assets/77e740c8-f47a-4663-b24b-3537425b6aa8" />

## Competition

<img width="1280" height="960" alt="photo_2026-07-13_19-54-44" src="https://github.com/user-attachments/assets/edd56504-e785-4194-a9a0-41944a4a438e" />

---

# 🧠 Skills Developed

Through this project, I developed practical experience in:

### CAD & Design

* 3D CAD modeling
* Mechanical design
* Technical drawings
* Component positioning
* Design iteration

### Robotics

* Robot construction
* Mechanical assembly
* Electronics integration
* Testing and troubleshooting

### Competition

* Competition preparation
* Robot reliability testing
* Real-time problem solving
* Working under competition pressure

### Teamwork

* Working in a 3-person engineering team
* Dividing technical responsibilities
* Communicating during development
* Improving the robot through team feedback

---

# 🔄 What We Learned

RoboWar competitions taught us that a successful robot is not only about having a powerful design.

A competition robot needs:

* Reliable mechanical construction
* Stable electronics
* Responsive control
* Effective programming
* Good driving
* Fast troubleshooting
* Continuous testing and improvement

Every competition gave us new experience that we used to improve the robot for the next event.

---

# 📊 Project Summary

| Category       | Details                     |
| -------------- | --------------------------- |
| 🤖 Project     | RoboWar Competition Robot   |
| 👥 Team Size   | 3 members                   |
| 🛠️ My Role    | CAD Designer                |
| ⚙️ Engineering | Nazarov Asadbek             |
| 🎮 Driver      | Nazarov Asadbek             |
| 💻 Programming | Narziyev Akbarshox          |
| 🥇 1st Place   | 6×                          |
| 🥈 2nd Place   | 2×                          |
| 📐 CAD         | Custom Robot Design         |
| 🎥 Media       | Competition Photos & Videos |

---

# 🚀 Final Result

**6× First Place and 2× Second Place** across RoboWar competitions demonstrate the result of continuous engineering, design, programming, testing and teamwork.

This project represents practical experience in **robotics, CAD, mechanical engineering, electronics, programming and competition robotics**.

---

<p align="center">

## 🤖 Designed • Built • Tested • Competed

**RoboWar Competition Robot**

</p>
