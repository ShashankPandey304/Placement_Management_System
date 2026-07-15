# Placement Management System (Multi-DSA Platform)

An enterprise-grade, desktop-based Placement Management Portal built in Java Swing, utilizing the premium **FlatMacDark Look-and-Feel** for a modern Slate/Neon Indigo Dark Mode UI. 

This platform acts as a unified hub for **Students**, **Recruiters**, and **Administrators** to manage placements, corporate schedules, student records, and application pipelines.

---

## 🛠️ Technological Stack
*   **Language:** Java (JDK 17 or higher)
*   **GUI Framework:** Java Swing
*   **Design & Theme:** FlatLaf (specifically `FlatMacDarkLaf` for macOS-inspired dark mode styling)
*   **Database:** MySQL Server (Port `3306`)
*   **Build System:** Maven (for dependency resolution: MySQL Connector, FlatLaf)

---

## 💡 Integrated Data Structures and Algorithms (DSA)
This project is designed to demonstrate how core computer science data structures and algorithms optimize operations in a real-world enterprise pipeline:

### 1. Trie (Prefix Tree) — *Shivam*
*   **Usage:** Quick Company Search (Trie autocomplete in Companies tab).
*   **Explanation:** Company names are loaded into a character-linked Trie prefix tree. When the admin searches for a prefix (e.g., "G"), the Trie scans down the prefix path and returns matching results (e.g., "Google") in **O(L)** time complexity, where $L$ is the length of the query string.

### 2. Binary Search Tree (BST) — *Shivam*
*   **Usage:** CGPA Indexing and Range Search (Students tab).
*   **Explanation:** Students are indexed in a Binary Search Tree using their CGPA as the key. This allows the system to run **O(log N)** range filters (e.g., show all students with a CGPA between 8.5 and 10.0). It also implements node deletion (handling leaf nodes, single-child, and double-child cases) to temporarily hide records.

### 3. HashMap — *Ayush*
*   **Usage:** O(1) Constant Time Lookup by Student ID.
*   **Explanation:** To instantly verify credentials and retrieve profiles without scanning the SQL database continuously, student objects are indexed in a Java `HashMap`. This achieves **O(1) average constant-time complexity** retrieval.

### 4. Merge Sort — *Ayush*
*   **Usage:** Leaderboard Generation.
*   **Explanation:** To generate an academic leaderboard of eligible students, the system implements a custom divide-and-conquer **Merge Sort** utility. It orders records in **O(N log N)** time complexity, which is stable and optimal for larger datasets.

### 5. Doubly Linked List (DLL) — *Shashank*
*   **Usage:** Bidirectional Drive Browsing (Drives tab).
*   **Explanation:** Active company drives are loaded into a Doubly Linked List. The administrator can traverse the drives sequentially using "Next Node" and "Prev Node" pointers, enabling fast cache navigation without repeated SQL query latency.

### 6. Stack — *Shashank*
*   **Usage:** Undo Application Status Changes (Applications tab).
*   **Explanation:** History changes are tracked using an `UndoStack` (`java.util.Stack`). When an administrator updates a status, the change is pushed onto the stack. Pressing "Undo Last Change" pops the action off the stack and rolls back the database status instantly.

### 7. FIFO Queue — *Shashank*
*   **Usage:** Pending Application Approval Backlog (Applications tab).
*   **Explanation:** Incoming applications are queued in a First-In, First-Out (FIFO) queue backlog. The approval pipeline processes candidates in the exact order they applied, ensuring fairness.

### 8. Adjacency List Graph & BFS — *Ayush*
*   **Usage:** Overlapping Placements Network Mapping.
*   **Explanation:** Students and companies form a graph structure represented via an Adjacency List. Running a **Breadth-First Search (BFS)** starting from a student node traverses the network to list all connected corporate partners and groups related students with overlapping application interests.

### 9. Singly Linked List (SLL) — *Shashank*
*   **Usage:** Candidate Application History Timeline.
*   **Explanation:** Every time a candidate's application status updates (e.g., `applied` -> `shortlisted` -> `interview_scheduled`), a transition node is appended to a Singly Linked List. This forms a sequential timeline displayed on the student's dashboard.

---

## 🗄️ Database Setup
The project contains a pre-configured database schema with a large mock dataset (45 users, 42 student profiles, 15 companies, 25 drives, and 100+ application records) to demonstrate the DSA features.

1.  Open your MySQL Client (like MySQL Workbench, DBeaver, or MySQL Command Line).
2.  Import and execute the SQL script **`recreate_schema_and_seed_large.sql`** located in the root of the project.
    *   **Via Command Line:**
        ```bash
        mysql -u root -p < recreate_schema_and_seed_large.sql
        ```
3.  Navigate to `src/main/resources/` directory.
4.  Copy `db.properties.example` to `db.properties` and replace the credentials with your local MySQL password:
    ```properties
    db.url=jdbc:mysql://localhost:3306/placement_management_system
    db.username=root
    db.password=YOUR_LOCAL_MYSQL_PASSWORD
    ```

---

## 🚀 How to Run the Application

You do **NOT** need to install Maven globally on your system to run this project. Modern IDEs handle Maven dependencies automatically.

### Method A: Using an IDE (Recommended)
1.  Open this project folder in **Visual Studio Code** (with the *Extension Pack for Java* installed) or **IntelliJ IDEA**.
2.  The IDE will automatically read the `pom.xml` and download the required libraries (FlatLaf, MySQL Connector) in the background.
3.  Open `src/main/java/com/placement/Main.java`.
4.  Click the **Run** button above the `main` method (or right-click and select **Run**).

### Method B: Using Local Command Line Maven
If you have Maven installed on your system:
```bash
mvn clean compile exec:java -Dexec.mainClass="com.placement.Main"
```

---

## 👤 Default Login Credentials (for Testing)

### 1. Admin Accounts
*   **Username:** `admin` (or `admin1`, `admin2`)
*   **Password:** `admin123`

### 2. Student Accounts
*   **Username:** `shashank` (or `shivam`, `ayush`, `aditya`, `rahul`)
*   **Password:** `pass123`

### 3. Recruiter Accounts
*   **Username:** `tcs` (or `google`, `microsoft`, `amazon`, `infosys`)
*   **Password:** `pass123`
