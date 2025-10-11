# Types of Error and Hamming Distance


## 🧩 **1. Types of Errors in Computer Networks**

When data is transmitted over a communication channel (like a wire, fiber, or wireless medium), **errors** can occur due to noise, interference, or signal distortion.

There are mainly **two types of errors**:

### 🔹 **A. Single-bit Error**

* **Definition:** Only **one bit** in the data unit (like a byte or frame) is altered (flipped from 0→1 or 1→0).
* **Example:**

  * Sent: `1011001`
  * Received: `1001001`  ← (the 2nd bit got changed)
* **Usually happens:** in **wired channels**, where noise bursts are short.

---

### 🔹 **B. Burst Error**

* **Definition:** **Two or more consecutive bits** are changed during transmission.
* **Example:**

  * Sent: `1011001`
  * Received: `1000111`  ← (bits 2, 3, and 4 got altered)
* **Usually happens:** in **wireless channels**, where interference lasts longer.
* **Burst length:** is the number of bits from the **first corrupted bit to the last corrupted bit**, including both.

---

There are also **classifications** based on error detection/correction concepts:

| Type                 | Description                                             | Example                              |
| -------------------- | ------------------------------------------------------- | ------------------------------------ |
| **Random Error**     | Bits are changed at random positions                    | `1010101 → 1110001`                  |
| **Systematic Error** | A pattern or repeated disturbance affects specific bits | Signal distortion or faulty hardware |
| **Detected Error**   | Error detected by the receiver using parity, CRC, etc.  | Receiver requests retransmission     |
| **Undetected Error** | Error that slips past detection mechanism               | Dangerous in critical systems        |

---

## 🧮 **2. Hamming Distance**

### 🔹 **Definition**

The **Hamming Distance** between two binary strings of equal length is the **number of bit positions where the bits differ**.

👉 It measures **how different two codewords are**.

### 🔹 **Formula**

[
\text{Hamming Distance (d)} = \text{Number of positions where bits differ}
]

### 🔹 **Example**

Compare `1011101` and `1001001`
Positions that differ: (2nd, 4th, 6th) → 3 differences
✅ **Hamming Distance = 3**

---

## 🧠 **Use of Hamming Distance in Error Detection and Correction**

| Purpose              | Requirement                                                                                              | Explanation                                     |
| -------------------- | -------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| **Error Detection**  | Code must have a minimum Hamming distance **≥ 2**                                                        | It can detect **single-bit errors**             |
| **Error Correction** | Code must have a minimum Hamming distance **≥ 3**                                                        | It can **detect and correct single-bit errors** |
| **General Formula**  | To detect up to *d* errors → ( d_{min} = d + 1 ) <br> To correct up to *t* errors → ( d_{min} = 2t + 1 ) | Used to design error-correcting codes (ECC)     |

---

### 🔹 **Example — Hamming Code**

Suppose we design a code with a **minimum Hamming distance of 3**:

* If one bit flips (error), we can **detect and correct** it.
* If two bits flip, we can **detect** but not **correct** them.

---

### 🧩 **Quick Summary**

| Concept              | Meaning                                      | Example                         |
| -------------------- | -------------------------------------------- | ------------------------------- |
| **Single-bit Error** | Only one bit changed                         | `1010 → 1110`                   |
| **Burst Error**      | Multiple consecutive bits changed            | `1010 → 1100`                   |
| **Hamming Distance** | Number of bit differences                    | `1011` vs `1001` → 1 difference |
| **d_min = 3**        | Can detect 2-bit errors, correct 1-bit error | Used in Hamming codes           |

