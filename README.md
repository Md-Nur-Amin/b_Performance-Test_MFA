# Performance Testing Setup – Login & OTP Flow

## 📌 Overview

This project contains a performance testing setup for a **Login + OTP (One-Time Password) authentication flow** using **Apache JMeter (.jmx file)**.
It simulates real-world user behavior where multiple users attempt to log in and verify OTPs concurrently, helping evaluate system performance under load.

---

## 🎯 Objectives

* Measure system performance during login and OTP verification
* Identify bottlenecks in authentication flow
* Validate response times under concurrent user load
* Ensure system stability and scalability

---

## 🧰 Setup & Configuration

* **Apache JMeter Installation** – Ensure JMeter is installed and properly configured on the system
* **Test Plan Configuration** – Define the overall structure of the test plan
* **Thread Group Setup** – Configure number of users, ramp-up time, and loop count
* **HTTP Request Configuration** – Set up API endpoints, methods, headers, and payloads
* **Data Configuration (CSV Data Set Config)** – Provide dynamic input data such as user credentials
* **Extractors Configuration** – Configure JSON/Regex extractors to capture OTP from responses
* **Listeners Setup** – Configure result listeners for monitoring and analysis

---

## ⚙️ Test Flow

### 1. Login Request

* User sends login credentials (e.g., email/phone + password)
* Server validates credentials
* OTP is generated and sent to user

### 2. OTP Verification

* User submits received OTP
* Server validates OTP
* On success → user authenticated

---

## 🧪 Test Plan Structure

```
Test Plan
│
├── Thread Group
│   ├── HTTP Request - Login API
│   ├── Extract OTP (Regex / JSON Extractor)
│   ├── HTTP Request - OTP Verification API
│   └── Listeners (Results)
```

---

## 👥 Thread Configuration

| Parameter       | Description                   |
| --------------- | ----------------------------- |
| Number of Users | Concurrent virtual users      |
| Ramp-Up Period  | Time to start all users       |
| Loop Count      | Number of iterations per user |

---

## 🔁 Data Handling

* **Dynamic Inputs**:

  * Username / Phone number
  * Password
* **OTP Extraction**:

  * Extracted from response using:

    * JSON Extractor (for API response)
    * Regex Extractor (if needed)

---

## 📊 Key Metrics to Monitor

* Response Time (Login & OTP APIs)
* Throughput (requests/sec)
* Error Rate (%)
* Latency
* CPU & Memory usage (server-side)

---

## 🚀 How to Run the Test

1. Install Apache JMeter
2. Open JMeter GUI
3. Load the `.jmx` file:

   ```
   File → Open → b_ip.jmx
   ```
4. Configure:

   * Thread Group (users, ramp-up, loops)
   * API endpoints (if needed)
5. Run the test:

   ```
   Click ▶ (Start)
   ```
6. Analyze results using Listeners

---

## ⚠️ Best Practices

* Avoid running heavy tests in GUI mode (use CLI for large loads)
* Use realistic data and think time (Timers)
* Gradually increase load instead of sudden spikes
* Monitor backend logs during testing
* Use distributed testing for high-scale scenarios

---

## 📈 Example Test Scenario

* Users: 100
* Ramp-Up: 50 seconds
* Loop Count: 5

👉 Simulates 100 users logging in and verifying OTP multiple times

---

## 🧩 Possible Enhancements

* Add **Timers** to simulate user delay
* Integrate **CSV data** for unique users
* Add **Assertions** for response validation
* Use **Distributed Load Testing**
* Integrate with CI/CD pipeline

