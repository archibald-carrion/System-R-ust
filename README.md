# System-R-ust

## A few definitions
### 🧠 Understanding Non-Procedural Languages

A **non-procedural** (or **declarative**) language focuses on describing *what you want* instead of *how to get it*.
You specify the **desired result**, and the system determines the execution steps for you.

---

#### 🧩 Example: SQL (Non-Procedural)

In SQL, you simply describe **the outcome** you want:

```sql
SELECT name, salary 
FROM employees 
WHERE department = 'Engineering' AND salary > 100000;
```

Here, you're saying:

> “I want the names and salaries of engineers earning more than 100K.”

You’re **not** telling the system how to:

* Open the employee file
* Read each record sequentially
* Check if the department equals “Engineering”
* Compare salaries
* Extract and display the desired fields

SQL abstracts all of that logic away.

---

### ⚙️ Procedural Approach (Pre-Relational Databases)

In older, procedural systems (like **COBOL** or **IMS**), you had to specify *every single step* manually:

```cobol
OPEN employee-file
READ employee-record
IF department = 'Engineering' THEN
  IF salary > 100000 THEN
    DISPLAY name, salary
  END-IF
END-IF
...
```

This is the **navigational model** — you explicitly control how data is accessed, filtered, and processed.

---

### 🌐 The Concept of a Unified Language

Before SQL, different tasks required different tools and syntaxes:

* One language for **queries**
* Another for **updates**
* Separate tools for **schema creation**
* Different systems for **ad-hoc** vs. **programmatic** access

SQL changed that by **unifying all operations** (querying, updating, defining schemas) under a single, consistent language.

This allowed developers and analysts to focus on **business logic**, not low-level navigation logic — a massive leap in abstraction and productivity.

---

#### 💬 Ad-Hoc Access

**Ad-hoc access** means interactively querying data *on the fly* — usually by analysts, managers, or data scientists.
These users write and execute SQL queries directly, without writing formal programs.

**Example:**

```sql
SELECT product, SUM(sales) 
FROM orders 
WHERE date > '2025-01-01' 
GROUP BY product;
```

They can:

* Explore data
* Answer specific questions
* Generate reports dynamically

This type of access is **exploratory and interactive**.

---

#### 🧱 Programmatic Access

**Programmatic access** means embedding SQL queries into application code.
These queries are predefined and part of an application that users interact with indirectly.

**Example (Java):**

```java
String sql = "SELECT * FROM orders WHERE customer_id = ?";
PreparedStatement stmt = connection.prepareStatement(sql);
stmt.setInt(1, customerId);
ResultSet results = stmt.executeQuery();
// Process results and display in UI...
```

Here, the end user never sees SQL — they just click *“View My Orders”*, and the app executes the query behind the scenes.

---

### 💡 Why “Unified” Mattered

Before SQL:

* Ad-hoc tools and programmatic systems were **separate ecosystems**
* Each used **different syntax**, **logic**, and **access methods**
* Collaboration between DBAs and developers was **harder**

After SQL:

* Both ad-hoc users and programmers used **the same language**
* Queries could be tested interactively, then reused directly in application code
* This unified workflow **revolutionized database development**

---

#### 🧭 Summary

| Concept                     | Description                                                                           |
| --------------------------- | ------------------------------------------------------------------------------------- |
| **Procedural Language**     | You tell the computer *how* to perform a task (step-by-step instructions).            |
| **Non-Procedural Language** | You describe *what* result you want, and the system figures out *how* to achieve it.  |
| **SQL’s Role**              | Unified querying, updating, and schema definition into a single declarative language. |
| **Impact**                  | Simplified development, boosted productivity, and democratized data access.           |