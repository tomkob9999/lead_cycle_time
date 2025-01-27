# Throughput Time and Cycle Time in Pipelined Systems: A Comprehensive Framework

## Abstract
This paper presents a detailed framework for understanding **throughput time** and **cycle time** in pipelined systems, emphasizing their roles in system performance and efficiency. **Cycle time**, as the primary determinant of throughput, is analyzed using bottleneck principles, while **throughput time** offers insight into the system's total latency. The latter half of the paper explores the impact of input flow rates on system behavior, highlighting how exceeding the system throughput throughputs to queue growth and linear increases in total cycle time. Applications span domains such as manufacturing, networking, and software systems.

---

## Introduction
Pipelined systems enhance efficiency by breaking processes into sequential stages. In such systems:
- **Cycle time** determines throughput, governed by the slowest stage or bottleneck.
- **Throughput time** measures total latency, representing the time taken for a single unit to traverse the pipeline.

While cycle time and throughput time are interrelated, they serve distinct purposes:
- **Cycle time** is crucial for analyzing throughput.
- **Throughput time** provides a latency perspective, particularly important for real-time applications.

This paper provides a unified framework to analyze these metrics, emphasizing cycle time as the primary determinant of throughput and exploring input flow dynamics as a critical factor in system behavior.

---

## Definitions

### 1. Cycle Time
- **Cycle Time of a Stage**: The time required to complete one unit of work at a single stage.
- **Cycle Time of a Subsystem**: The slowest cycle time among its stages (the bottleneck).
- **Cycle Time of a System**: The slowest cycle time among all subsystems.

Mathematically:

$$
\text{Cycle Time of Subsystem} = \max(\text{Cycle Times of Stages})
$$

$$
\text{Cycle Time of System} = \max(\text{Cycle Times of Subsystems})
$$

### 2. Throughput Time
- **Throughput Time of a Stage**: The time it takes for one unit to traverse the stage.
- **Throughput Time of a Subsystem**: The sum of the throughput times of its stages.
- **Throughput Time of a System**: The sum of the throughput times of its subsystems.

Mathematically:

$$
\text{Throughput Time of System} = \sum_{i} \text{Throughput Time of Subsystem}_i
$$

---

## Framework for Analysis

### 1. Bottleneck Principle for Cycle Time
The cycle time of a system is dictated by its slowest process or subsystem. For any pipelined system:
- **Subsystem Level**: The bottleneck cycle time among stages determines the subsystem’s cycle time.
- **System Level**: The bottleneck cycle time among subsystems determines the system’s cycle time.

$$
\text{Cycle Time of System} = \max(\text{Cycle Times of Subsystems})
$$

### 2. Throughput Time as Additive Latency
Throughput time represents the total time for a unit to traverse all subsystems. In a sequential pipeline, throughput time is calculated as the sum of throughput times across all subsystems:

$$
\text{Throughput Time of System} = \sum_{i} \text{Throughput Time of Subsystem}_i
$$

---

## Input Flow Dynamics and System Behavior

The relationship between **input flow rate**, **queue growth**, and **cycle time** reveals critical system behaviors:

### 1. Input Rate Below System Throughput
When the rate of input flow ($R_{\text{in}}$) is less than or equal to the system throughput rate ($R_{\text{system}}$):
- The system processes inputs as they arrive:
  
$$
R_{\text{out}} = R_{\text{in}}
$$

- No queue builds up, and the system operates at steady-state throughput.
- Total cycle time remains constant and equals the system cycle time:

$$
\text{Total Cycle Time} = \text{Cycle Time}_{\text{system}}
$$

### 2. Input Rate Exceeds System Throughput
When $R_{\text{in}} > R_{\text{system}}$:
- The system cannot process inputs as fast as they arrive.
- A queue builds up at a rate proportional to the difference between input and system throughput rates:

$$
\text{Queue Growth Rate} = R_{\text{in}} - R_{\text{system}}
$$

- Over time $t$, the queue length $Q(t)$ grows linearly:

$$
Q(t) = (R_{\text{in}} - R_{\text{system}}) \cdot t
$$

- The output rate remains constant at the system throughput rate:

$$
R_{\text{out}} = R_{\text{system}}
$$

### 3. Impact on Total Cycle Time
As the queue grows, the total cycle time for an input includes:
- The **system cycle time** ($\text{Cycle Time}_{\text{system}}$).
- The **wait time**, which grows linearly with the queue length:

$$
\text{Wait Time} = Q(t) \cdot \text{Cycle Time}_{\text{system}}
$$

The total cycle time is given by:

$$
\text{Total Cycle Time} = \text{Cycle Time}_{\text{system}} 
$$

$$
 \cdot (1 + (R_{\text{out}} = R_{\text{system}})) \cdot t)
$$

This equation shows that the total cycle time grows linearly with $t$, with a growth rate proportional to $R_{\text{in}} - R_{\text{system}}$.

---

## Example: System Behavior with Input Flow

### Problem Setup
Consider a system with:
- System throughput rate: $R_{\text{system}} = 5 \, \text{units/s}$.
- System cycle time: $\text{Cycle Time}_{\text{system}} = 0.2 \, \text{s/unit}$.
- Input rate: $R_{\text{in}} = 7 \, \text{units/s}$ (exceeds system throughput).

### Calculations
1. **Queue Growth Rate**:
   
$$
\text{Queue Growth Rate} = R_{\text{in}} - R_{\text{system}} = 7 - 5 = 2 \, \text{units/s}.
$$

3. **Queue Length After 10 Seconds**
   
$$
Q(10) = (R_{\text{in}} - R_{\text{system}}) \cdot t = 2 \cdot 10 = 20 \, \text{units}.
$$

5. **Total Cycle Time After 10 Seconds**:
 
$$
\text{Total Cycle Time} = \text{Cycle Time}_{\text{system}} 
$$
   
$$
\cdot \left(1 + (R_{\text{in}} - R_{\text{system}}) \cdot t \right)
$$

$$
= 0.2 \cdot \left(1 + 2 \cdot 10 \right) = 0.2 \cdot 21 = 4.2 \, \text{s/unit}.
$$

---

## Applications

### 1. Manufacturing Systems
- Predict queue growth and total cycle time under varying input rates.
- Optimize throughput by controlling input flow to match system capacity.

### 2. Networking
- Analyze packet processing rates and buffer overflows in routers under high input traffic.
- Implement rate-limiting to prevent excessive queue growth.

### 3. Software Systems
- Identify bottlenecks in data processing pipelines with high input rates.
- Use dynamic load balancing to adjust input flow rates and prevent delays.

---

## Conclusion
This paper provides a comprehensive framework for analyzing **cycle time** and **throughput time** in pipelined systems, emphasizing cycle time as the primary determinant of throughput. It further explores the impact of input flow rates, showing how exceeding system throughput throughputs to queue growth and linear increases in total cycle time. By integrating these principles, this framework offers practical tools for optimizing complex systems across various domains, including manufacturing, networking, and software systems.

---
