# Modeling-Assignments

### **1. Newspaper Seller: Monte Carlo Integration & Profit Surface Analysis**

This project focuses on **Static Stochastic Modeling**. Unlike the other three, it does not use a "clock" because each day is an independent trial.

* **Data Structure (Probability Tables):** You must implement a nested lookup table.
* **Level 1:** A random number (0-1) selects the **Type of Newsday** (Good, Fair, Poor) based on user-defined weights.
* **Level 2:** A second random number selects the **Demand** from a cumulative distribution specific to that day type.


* **The "Scrap vs. Stockout" Conflict:**
* **Overstocking:** If , you incur a holding-like penalty where papers are sold at a **Salvage Value** (often < Cost Price), leading to a marginal loss.
* **Understocking:** If , you record **Lost Profit**, representing the opportunity cost of customers turned away.


* **Simulation Goal:** By iterating this process thousands of times for different "Paper Quantities," the student identifies the quantity that maximizes the **Expected Value of Profit**.

---

### **2. Inventory Simulation:  Policy and Lead-Time Risk**

This project introduces **Discrete Event Simulation (DES)** with state variables that persist across "Review Cycles."

* **State Variables:**
* **Inventory Position:** . This is the value used to decide how much to order.
* **Inventory On-Hand:** The physical stock available to satisfy customers.


* **The Order Process:** Every  days, an order is placed. The amount is .
* **Stochastic Lead Time:** The arrival of the order is a future event scheduled at . If the lead time is long and demand is high, the inventory drops into the negative, triggering **Shortage Costs**.
* **Metrics:** The primary goal is to minimize the **Total Cost**, which is the sum of Ordering, Holding, and Shortage costs.

---

### **3. Multi-Queue Simulation: Resource Contention & Queueing Theory**

This models a "Service System" where multiple entities compete for limited resources (servers).

* **The Future Event List (FEL):** The "engine" of this simulation is a chronological list of events.
* **Arrival Event:** Generates the next arrival and assigns a service time.
* **Service-End Event:** Releases a server and looks at the queue to see if another entity can be served immediately.


* **Server Selection Strategies:** Students must program logic for server assignment:
1. **Highest Priority:** Always picks Server 1 if available.
2. **Random:** Uniformly picks from available servers.
3. **Least Utilization:** Picks the server that has been idle the longest.


* **Analysis:** It calculates the **Probability of Waiting** and **Average Queue Length** to determine if the system is "stable" or if the queue will grow to infinity.

---

### **4. Time-Sharing CPU: Quantum Slicing & Context Overhead**

This is a high-fidelity model of an Operating System's scheduler.

* **The Preemption Logic:** * In **Round Robin (RR)**, the CPU "slices" time. If a job's `RemainingTime` exceeds the `Quantum` (e.g., 0.1s), the `EndCpuRunRoutine` deducts the quantum from the job and puts it back in the `JobQueue`.
* If the job is shorter than the quantum, it finishes, and the CPU becomes idle until the next job is selected.


* **The Swap Time Penalty:** Every time a job enters the CPU, a `SwapTime` (overhead) is added to the `EndTime`. This models the real-world OS cost of saving registers and switching memory contexts.
* **Shortest Job First (SJF):** This is a **Non-Preemptive** policy in this model. The system scans the `JobQueue`, finds the job with the minimum `RemainingTime`, and runs it to completion.
* **Statistics (Time-Weighted Averages):** * **Queue Area:** This is calculated as . If the queue has 5 jobs for 2 seconds, the `QueueArea` increases by 10.
* **Average Queue Length:** At the end of the simulation,  gives the average number of waiting jobs.


* **System Loop:** Terminals generate jobs, wait for them to finish, and then enter a "Think Time" state (Exponentially distributed) before starting over.
