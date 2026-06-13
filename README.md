# 🛡️ OverTheWire: Bandit Wargame Solutions & Cybersecurity Study Logs
Welcome to my security repository! This project serves as a comprehensive archive tracking my hands-on progress through the OverTheWire Bandit wargame (Levels 0–13), alongside my structured foundational logs covering networking architecture, Linux systems engineering, and Python automation.

---

## 🚀 Part 1: Bandit Wargame Solutions (Levels 0 - 13)
*Focus: Hands-on Linux privilege escalation, advanced text filtering, and command-line data discovery.*

### 📂 Level 0 ➔ Level 1: Basics & The Dash Filename
* **Concepts:** Initiating remote SSH connections, basic file listing, and handling unusual file naming conventions.
* **Commands Used:** `ssh`, `ls`, `cat`
* **Key Takeaway:** To read a file explicitly named `-` (which `cat` mistakes for an options switch), you must pass its relative path descriptor: `cat ./-`.

### 🔍 Level 1 ➔ Level 2: Spaces in Filenames
* **Concepts:** Handling spaces in filenames without breaking the terminal argument parser.
* **Commands Used:** `cat`
* **Key Takeaway:** Enclose the target string in literal double quotes (e.g., `cat "spaces in this filename"`) or leverage shell tab-completion to auto-escape characters.

### 🙈 Level 2 ➔ Level 3: Hidden Infrastructure Assets
* **Concepts:** Discovering administrative and flag files hidden from normal directory listing views.
* **Commands Used:** `ls -la`
* **Key Takeaway:** In Linux, system files starting with a period `.` are hidden by default. Running `ls -la` forces the file system to reveal all contents.

### 🕵️‍♂️ Level 3 ➔ Level 5: File Profiling & Targeted Discovery
* **Concepts:** Sifting through human-readable vs. compiled binary configurations, and crawling nested directory tracks using exact metadata parameters.
* **Commands Used:** `file`, `find`, `du`
* **Key Takeaway:** Located an exact file hidden deep across subfolders by filtering on size, type, and specific attributes: `find . -type f -size 1033c ! -executable`.

### 🧹 Level 5 ➔ Level 6: Global Metadata Scanning & Stream Redirection
* **Concepts:** Searching across the root directory system for explicit administrative tags (users, groups, and exact sizing counters).
* **Commands Used:** `find`, `grep`
* **Key Takeaway:** Muted endless screens of terminal access noise by redirecting standard error streams to the system black hole: `find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`.

### 📝 Level 6 ➔ Level 9: Text Aggregation, Sorting, & Binary Inspection
* **Concepts:** Grouping disorganized log entries, pulling matches out of compressed strings, and parsing compiled binary environments.
* **Commands Used:** `grep`, `sort`, `uniq`, `strings`
* **Key Takeaways:** * Appended pipelines together (`sort | uniq -u`) to pinpoint a single password data entry that occurred exactly once.
  * Executed `strings` on a binary file layout to filter out executable code garbage, allowing `grep` to successfully track text targets.

### 🔐 Level 9 ➔ Level 11: Cryptographic Transposition & Encoding Filters
* **Concepts:** Identifying packaging systems vs. obfuscation ciphers.
* **Commands Used:** `base64`, `tr`
* **Key Takeaways:** * Restored clean plain-text payloads out of data blocks using the base64 decoding switch: `base64 -d`.
  * Cracking character manipulation streams (ROT13) by aligning and substituting standard alphabet tracks using translation maps: `tr 'A-Za-z' 'N-ZA-Mn-za-m'`.

### 📦 Level 11 ➔ Level 13: Nested Decompression Loops & Hex Recovery
* **Concepts:** Reversing structural multi-layered archives (gzip, bzip2, tar) and inspecting structural magic bytes.
* **Commands Used:** `xxd`, `mv`, `gzip`, `bzip2`, `tar`
* **Key Takeaway:** Rebuilt an executable file out of a raw hex dump via `xxd -r`, then iteratively verified extensions and true structures via `file` to systematically extract a multi-layered archive file.

---

## 🌐 Part 2: Core Networking & Architecture Fundamentals
*Theoretical engineering tracking how data fragments route over local and global networks.*

### The 7 Layers of the OSI Model
1. **Layer 7: Application** – User-facing software and communication tools (Google Chrome, Discord, HTTP, DNS).
2. **Layer 6: Presentation** – Handles format translations, string compression algorithms, and SSL/TLS data encryption.
3. **Layer 5: Session** – Controls connection sessions, checkpointing, and separate communication streams.
4. **Layer 4: Transport** – Chooses shipment pathways. **TCP** (Connection-oriented; prioritizes reliability over speed by verifying missing packets) or **UDP** (Connectionless; prioritizes speed over reliability for fast streaming feeds).
5. **Layer 3: Network** – Determines data routing across global infrastructures using logical **IP Addresses**.
6. **Layer 2: Data Link** – Groups data into local frames and handles hop-to-hop physical delivery using burned-in **MAC Addresses**.
7. **Layer 1: Physical** – The physical infrastructure medium (fiber-optic flashes, copper voltage spikes, Wi-Fi waves).

### Data Encapsulation Matrix
As a message descends through the networking stacks, it is wrapped in functional address envelopes at every tier:
$$\text{Data} \rightarrow \text{Segment (TCP)/Datagram (UDP)} \rightarrow \text{Packet (IP)} \rightarrow \text{Frame (MAC)} \rightarrow \text{Bits}$$
> ⚠️ **Security Distinction:** Encapsulation is strictly for *formatting and delivery routing*, not security. Headers remain plain text. True information confidentiality requires encryption (like TLS/SSL) at the upper layers.

### The TCP 3-Way Handshake
To negotiate sequence synchronization maps safely before exchanging data payloads, connection paths follow a three-step authorization protocol:
1. **`SYN` (Synchronize):** Client sends a random tracking sequence number to the host.
2. **`SYN/ACK` (Synchronize/Acknowledge):** Server acknowledges the client's position and passes back its synchronization counter.
3. **`ACK` (Acknowledge):** Client logs the data connection as live.
* *Teardown:* Graceful exits utilize a `FIN` sequence flow; unexpected fatal failures instantly sever paths via a `RST` (Reset) instruction flag.

### Core Architecture Protocols
* **DNS (Domain Name System):** Resolves human strings into logical IP nodes. Follows a chain starting from the local hosts file, checking local short-term cache memory, and escalating to Recursive, Root, TLD, and Authoritative Name Servers.
* **DHCP (Dynamic Host Configuration Protocol):** Dynamically provisions system settings to network arrivals using the four-step **DORA** sequence (**D**iscover, **O**ffer, **R**equest, **A**cknowledge).
* **ARP (Address Resolution Protocol):** The local finder layer that queries the network to map a known logical software IP address to an absolute physical hardware MAC address.
* **ICMP (Ping Tool):** Network diagnostic framework used to track round-trip connectivity latency (ms) and monitor the Time To Live (TTL) hop counter to block infinite loops.

---

## 🐧 Part 3: Linux CLI Operations & Flow Operators
*Mastering headless servers through conditional execution logic and path syntax.*

### The System Administrator's Toolkit
* `pwd` – Prints current absolute path coordinates. Use this to re-orient yourself during errors.
* `cd ~` – Instant home folder directory teleportation.
* `cat` – Concatenates file data and outputs standard text straight onto the screen terminal.

### Shell Flow Operators Reference
| Operator | Name | Behavioral Logic Rule |
| :--- | :--- | :--- |
| `&` | Background Task | Fork-executes a slow process into the background, returning immediate terminal prompt access. |
| `&&` | Logical AND | Chains commands; Step 2 executes **only** if Step 1 returns a successful `Exit 0` status flag. |
| `||` | Logical OR | Fallback conditional logic; Step 2 triggers **only** if Step 1 crashes or fails out. |
| `>` | Redirection (Overwrite) | Dumps terminal text output straight into a target file, wiping out old context cleanly. |
| `>>` | Redirection (Append) | Safely opens a file path and tacks terminal output onto the bottom line without overwriting. |
| `|` | The Pipe | Channels data streams; bridges the standard output of Command A into the input of Command B. |

---

## 🐍 Part 4: Automated Data Ingestion & Scripting Fundamentals
*Parsing technical records and debugging string exceptions using Python.*

### Data Type Isolation & Parsing Log Operations
* **The Concatenation Trap:** Ingesting system logs natively reads numeric inputs as text strings (`str`). Adding text parameters together `"5" + "2"` joins them into `"52"` instead of running math logic.
* **Type Casting:** Forcing string configurations into readable mathematical calculations by packaging variables inside `int()` operators.
* **Debugging Variables:** Injecting `print(type(variable_name))` commands inside loops to diagnose and verify data types during automated filtering execution.

```
