# JMeter - Performance Testing

This project consists of two JMeter collections (booking.jmx, dmoney.jmx) created for Test creation, Test debugging and Performance testing. Also for CSV data handling that how to read data from csv file through JMeter and make several threads for each opeartions.

## Project Overview

### 1. Booking (Load and Stress Testing)
- A **JMeter collection** (booking.jmx) was created using the provided API endpoints:
  - **Login URL**: `https://restful-booker.herokuapp.com/auth`
  - **Create Booking URL**: `https://restful-booker.herokuapp.com/booking`
  - **Search Booking URL**: `https://restful-booker.herokuapp.com/booking/<booking_id>`
  
- The collection performs the following tasks:
  - **Scenario:** 120,000 users over a 12-hour period log in, create a booking, and search for the booking.
  - **Load Testing** and **Stress Testing** on these API endpoints using both **GUI mode** (for test creation, test debugging) and **Non-GUI mode** (for perform testing and generating HTML reports).
  - After successfully passed the **load test**,Then **stress test** identifies the server’s bottleneck throughput under maximum stress.

- Screenshots for the test results of **Load Test Report**, **Stress Test Report** and the **HTML reports** are included in [**Analyze Reports**](#analyze-reports) secion.

### 2. Dmoney (CSV Data Handling and Transactions)
- A **JMeter collection** (dmoney.jmx) was created using the **Dmoney API**, with the following CSV files:
  - `deposit.csv`, `withdraw.csv`, `sendMoney.csv`, and `payment.csv`, located in the **Dmoney** folder.
  
- The collection performs the following tasks:
  - **Reading data from the CSV files** in JMeter and executing deposit, withdrawal, send money, and payment transactions.
  ### Scenario:
  - **5 agents** perform deposits for **10 customers**.
  - **5 customers** send money to **10 other customers**.
  - **5 customers** make payments to **2 merchants**.
  - The withdrawal amounts were generated using **Boundary Value Analysis (BVA)**, and the amounts for other transactions were dynamic using the **Random Variable Controller**.
  - Each transaction is executed in both **GUI mode** (for validation) and **Non-GUI mode** (to generate HTML reports).
  
- Screenshots for the **HTML report** are included in [**Analyze Reports**](#analyze-reports) section.
---

## Prerequisites

Before running these tests, make sure to have the following installed:

- [Apache JMeter](https://jmeter.apache.org/)
- Java Development Kit (JDK 11)
- Git (to clone the repository)

---

## How to Run the Tests

### Step 1: Clone the Repository
```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```
## Step 2: Running the Booking Collection (Load and Stress Testing)

### GUI Mode:
- Open JMeter in **GUI mode** using the `jmeter` command.
- Open the `.jmx` file located in the **Booking** folder.
- Run the test in **GUI mode** to validate that the API endpoints (**Login**, **Create Booking**, and **Search Booking**) are working correctly.
- Verify the test results using **View Results Tree**.

### Non-GUI Mode (Load Test):
- Open the Booking folder and run through command prompt.
- Run the test in **Non-GUI mode** and generate a **load test report** with the following command:
    ```bash
    jmeter -n -t .\booking.jmx -l .\booking.jtl -e -o load-report
    ```
- Review the generated **HTML report** in the `load-report` folder.

### Non-GUI Mode (Stress Test):
- Conduct a **stress test** to find bottlenecks and generate a report:
    ```bash
    jmeter -n -t .\booking.jmx -l .\booking.jtl -e -o stress-report
    ```
- Review the generated **HTML report** in the `stress-report` folder.

---

## Step 3: Running the Dmoney Collection (CSV Data Handling)

### GUI Mode:
- Open JMeter in **GUI mode** and load the `.jmx` file from the **dmoney** folder.
- Ensure the **CSV files** (`deposit.csv`, `sendMoney.csv`, `payment.csv`, `withdraw.csv`) are properly linked to the corresponding **CSV Data Set Config** in the test plan.
- Run the test in **GUI mode** to verify correct data handling.

### Non-GUI Mode:
- Run the test in **Non-GUI mode** and generate the **HTML report**:
    ```bash
    jmeter -n -t .\dmoney.jmx -l .\dmoney.jtl -e -o Reports
    ```
- Review the generated **HTML report** in the `Reports` folder.

---

## <a name="analyze-reports"></a>Step 4: Analyze Reports

- Open the **HTML reports** generated in **Non-GUI mode** for both the **Booking** and **Dmoney** collections to analyze the performance data.

---

## Screenshots
There include the following results after successfully run the booking.jmx collection and dmoney.jmx collection.
### Booking Collection:
- **Load Test Report**
  - For the mentioned scenario the load test is performed for 20 min.
![image](https://github.com/user-attachments/assets/02886240-77dd-4281-8942-ce02e523fab4)

- **Requests Summary** of Load Test
![image](https://github.com/user-attachments/assets/df118306-ec75-43cc-8c5d-1cb84f28a663)

- **Statistics** of Load Test
![image](https://github.com/user-attachments/assets/c368e8dc-e356-4824-9305-a6fddc87ecb3)

- **Stress Test Report**
  - The testing time start from 20 min as it was the passed time for the load test.
![image](https://github.com/user-attachments/assets/0da48974-7965-463c-88cb-56d9c2803656)

- **Requests Summary** of Stress Test
![image](https://github.com/user-attachments/assets/65314fc9-163c-4837-b579-e0062c961d74)

- **Statistics** of Stress Test
![image](https://github.com/user-attachments/assets/e255b387-9115-43a3-838b-8e8d049f8b05)

### Dmoney Collection:
- **Requests Summary**
![image](https://github.com/user-attachments/assets/04d6c546-912b-49f9-babe-69edd9462e16)

- **Statistics**
![image](https://github.com/user-attachments/assets/49caa7cf-267b-43b9-8ae9-4c2ef2a57082)
