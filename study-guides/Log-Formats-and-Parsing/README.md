# 📜 Log Formats and Parsing Guide

This repository serves as a technical reference for understanding the most common log formats used in cybersecurity, system administration, and Security Information and Event Management (SIEM) solutions.

---

## 🔍 Why Log Formats Matter

Logs are the primary source of truth for investigating security incidents. However, different devices (firewalls, servers, applications) generate logs in different ways. Understanding these formats is crucial for **Log Parsing**—the process of extracting meaningful, structured fields (like IP addresses, usernames, and timestamps) from raw log data so a SIEM can analyze them.

---

## 1️⃣ Syslog

Syslog is more than just a format; it serves three primary functions in networking:
1. **Format:** A standardized structure for message logging.
2. **Service:** A background process/daemon (like `rsyslog` or `syslog-ng`) that collects logs.
3. **Protocol:** A network protocol (typically UDP port 514) used to send log messages to a centralized server.

**Example of a Syslog message:**
```text
<34>1 2022-12-20T08:20:38.921Z server.localdomain sshd 1234 - - User nuhara logged in successfully
```
* **Breakdown:** 
  * `<34>1`: Priority (Facility and Severity) and Version.
  * `2022-12-20T08:20:38.921Z`: Timestamp.
  * `server.localdomain`: Hostname.
  * `sshd`: App/Process generating the log.
  * `User nuhara logged in successfully`: Event Description.

---

## 2️⃣ JSON (JavaScript Object Notation)

JSON is a lightweight, human-readable data-interchange format. It is highly favored in modern cloud applications and SIEMs because it natively structures data in **key-value pairs**, making it incredibly easy to parse and query.

**Example of a JSON log:**
```json
{
  "timestamp": "2022-12-20T08:20:38.921Z",
  "hostname": "server.localdomain",
  "process": "sshd",
  "event": {
    "action": "login",
    "user": "nuhara",
    "status": "success"
  }
}
```

---

## 3️⃣ XML (eXtensible Markup Language)

XML is a flexible, text-based format that uses **tags** to structure data hierarchically (similar to HTML). While extremely structured, it tends to be more verbose and consumes more storage space than JSON. Windows Event Logs natively use an XML-based structure.

**Example of an XML log:**
```xml
<Event>
    <System>
        <TimeCreated SystemTime="2022-12-20T08:20:38.921Z"/>
        <Computer>server.localdomain</Computer>
        <Provider Name="sshd"/>
    </System>
    <EventData>
        <Data Name="User">nuhara</Data>
        <Data Name="Action">login</Data>
        <Data Name="Status">success</Data>
    </EventData>
</Event>
```

---

## 4️⃣ CSV (Comma-Separated Values)

CSV is a simple, flat-file format that uses commas to separate values. It is highly compact and easily readable by spreadsheet applications (like Excel) or data analysis scripts (using Python/Pandas). However, it lacks the hierarchical nesting capabilities of JSON or XML.

**Example of a CSV log:**
```csv
timestamp,hostname,process,user,action,status
2022-12-20 08:20:38,server.localdomain,sshd,nuhara,login,success
```

---

## 5️⃣ CEF (Common Event Format)

Created by ArcSight (now part of Micro Focus), CEF is an open log management standard specifically designed for SIEM interoperability. It ensures that security events from different vendors share a common structure, making correlation much easier.

**Example of a CEF log:**
```text
CEF:0|SecurityVendor|SecurityProduct|1.0|100|User Login|3|src=192.168.1.50 duser=nuhara msg=User nuhara logged in successfully
```
* **Breakdown of the CEF Header (separated by `|`):**
  * `CEF:0`: Version.
  * `SecurityVendor` & `SecurityProduct`: Device info.
  * `1.0`: Device version.
  * `100`: Signature ID.
  * `User Login`: Name of the event.
  * `3`: Severity.
  * `src=... duser=...`: Extensions (key-value pairs detailing the event).
