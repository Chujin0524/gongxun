# Core Technology Introduction of Intelligent Inspection System

This project develops an intelligent inspection system based on a high-performance microcontroller, achieving technological breakthroughs and optimizations in several key areas including hardware design, attitude control, visual perception, and human-machine interaction, aiming to enhance system stability, expandability, navigation accuracy, and intelligence level.

## 1. Meticulously Designed Hardware Platform

With the **STM32F407VET6** microcontroller as the core, we led and completed the optimized design of the hardware circuit board. By redrawing the power and peripheral circuits, we effectively addressed the issue of insufficient interface resources and significantly boosted the system's overall stability and expandability, laying a solid foundation for the smooth operation of upper-level applications.

## 2. High-Precision Attitude Sensing and Control

To achieve precise motion control, the system deeply integrates the **HWT101 gyroscope sensor**. This is combined with a **PID control algorithm** and a **Kalman Filter** for data fusion and attitude determination. This combination ensures high-precision attitude correction capability, enabling the robot to maintain straight-drive heading deviation within a range of **±1°**, meeting the requirements for high-accuracy navigation.

## 3. Efficient and Robust Visual Recognition Capability

In the realm of environmental perception, particularly for digit recognition tasks, we demonstrated strong computer vision application capabilities. Based on the **Maxicam** platform, we trained a **YOLOv5s** lightweight object detection model. Through meticulous annotation and training on **4507 local images**, the model achieved an impressive **97% recognition accuracy** on the validation set and reached a real-time recognition rate of **100fps**, ensuring the system can quickly and accurately perceive key information in the environment.

## 4. Intuitive and User-Friendly Human-Machine Interface

To optimize user operational experience and task execution efficiency, we designed and implemented a touchscreen-based human-machine interface. This interface supports ward task selection and progress display, facilitating stable communication between the STM32 and the touchscreen via **serial redirection** technology. Furthermore, the system integrates the **JQ8900 voice module**, enabling timely voice feedback in scenarios such as ward navigation, enhancing the system's intelligence and usability.

---

By synergistically optimizing and innovating across the hardware, control, perception, and interaction layers, this project successfully created a powerful, stable, and highly intelligent autonomous inspection system, providing a reliable solution for robot applications in complex environments.
