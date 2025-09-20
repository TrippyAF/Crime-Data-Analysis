# 🚔 Crime Analysis Database

This project provides the **database schema and sample data** for a **Crime Analysis System**.  
It is designed to manage details of **criminals, crimes, victims, FIRs, police stations, police staff, and police records** in a structured relational database.

---

## 📋 Features
- Store **criminal profiles** with personal and contact information.
- Record **crimes** with type, time, location, and linked criminals.
- Maintain **victim information** and their association with criminals.
- Track **FIRs** with detailed descriptions of reported crimes.
- Manage **police stations and policemen** with postings and jurisdiction.
- Store **police records** linked to criminals, stations, and policemen.

---

## 🗄️ Database Schema

### 1. **Criminal**
| Column       | Type           | Description |
|--------------|---------------|-------------|
| id           | int (PK)      | Unique criminal ID |
| first_name   | varchar(255)  | First name |
| last_name    | varchar(255)  | Last name |
| phone_no1    | bigint        | Primary contact |
| phone_no2    | bigint        | Secondary contact |
| street_name  | varchar(255)  | Street address |
| city         | varchar(255)  | City |
| gender       | char          | Gender (M/F/T) |

---

### 2. **Crime**
| Column       | Type           | Description |
|--------------|---------------|-------------|
| id           | int (PK)      | Crime ID |
| type_        | varchar(255)  | Type of crime (murder, robbery, etc.) |
| time_        | datetime      | Date and time of crime |
| district     | varchar(255)  | District |
| locality     | varchar(255)  | Locality |
| street_name  | varchar(255)  | Street where crime occurred |
| criminal_id  | int (FK)      | References **criminal(id)** |

---

### 3. **Victim**
| Column      | Type           | Description |
|-------------|---------------|-------------|
| id          | int (PK)      | Victim ID |
| first_name  | varchar(255)  | First name |
| last_name   | varchar(255)  | Last name |
| street_name | varchar(255)  | Address street |
| city        | varchar(255)  | City |
| phone_no1   | bigint        | Primary contact |
| phone_no2   | bigint        | Secondary contact |
| gender      | char          | Gender |
| criminal_id | int (FK)      | References **criminal(id)** |

---

### 4. **FIR**
| Column       | Type           | Description |
|--------------|---------------|-------------|
| id           | int (PK)      | FIR ID |
| FIR_type     | varchar(255)  | Type of FIR (murder, theft, etc.) |
| FIR_descrip  | varchar(255)  | Description of FIR |
| victim_id    | int (FK)      | References **victim(id)** |
| crime_id     | int (FK)      | References **_crime(id)** |

---

### 5. **Police Station**
| Column       | Type           | Description |
|--------------|---------------|-------------|
| id           | int (PK)      | Station ID |
| station_name | varchar(255)  | Station name |
| phone_no     | bigint        | Contact number |
| email        | varchar(255)  | Official email |
| zone         | varchar(255)  | Police zone |
| pincode      | int           | Pincode |
| locality     | varchar(255)  | Locality |

---

### 6. **Policeman**
| Column       | Type           | Description |
|--------------|---------------|-------------|
| id           | int (PK)      | Policeman ID |
| first_name   | varchar(255)  | First name |
| middle_name  | varchar(255)  | Middle name (optional) |
| last_name    | varchar(255)  | Last name |
| address      | varchar(255)  | Address |
| phone_no     | bigint        | Phone number |
| post         | varchar(255)  | Post (Inspector, SI, Constable, etc.) |
| station_id   | int (FK)      | References **police_station(id)** |

---

### 7. **Police Record**
| Column       | Type           | Description |
|--------------|---------------|-------------|
| id           | int (PK)      | Record ID |
| past_record  | varchar(255)  | Past criminal record |
| record_type  | varchar(255)  | Record type (murder, robbery, etc.) |
| date_        | date          | Record date |
| criminal_id  | int (FK)      | References **criminal(id)** |
| station_id   | int (FK)      | References **police_station(id)** |
| policeman_id | int (FK)      | References **policeman(id)** |

---
