# ORM Project - Therapy Management System

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Database Schema](#database-schema)
- [Setup Instructions](#setup-instructions)
- [Sample Data](#sample-data)
- [Technologies Used](#technologies-used)
- [Contributing](#contributing)
- [License](#license)

---

## Project Overview
This is a **Therapy Management System** built using **Java, Hibernate ORM, MySQL**, and **JavaFX**.  

It allows managing:

- Patients  
- Therapists  
- Therapy Programs  
- Therapy Sessions  
- Payments  
- User Accounts (Admins, Staff, Therapists)

The system demonstrates **CRUD operations** with ORM and **relationships between entities**.
<img width="1366" height="768" alt="Screenshot (22)" src="https://github.com/user-attachments/assets/c6df01c7-27c2-423f-bf1a-491f39a8e31e" />

After login, the dashboard displays the encrypted password at the top for verification, while keeping the password secure and demonstrating encryption works correctly.
<img width="1366" height="768" alt="Screenshot (25)" src="https://github.com/user-attachments/assets/10f7af3c-83f5-4fe6-956f-e1a64f63b067" />
<img width="1366" height="768" alt="Screenshot (24)" src="https://github.com/user-attachments/assets/3f538dd3-08ef-4558-8440-2dfffb2344ba" />

The system generates detailed reports for patients, therapists, sessions, and payments, providing a clear summary of all data in the application.
<img width="1366" height="768" alt="Screenshot (23)" src="https://github.com/user-attachments/assets/e252fccd-79d9-441c-bc7e-f44ddfa0f828" />
<img width="1366" height="768" alt="Screenshot (33)" src="https://github.com/user-attachments/assets/7d1b78a6-d859-434f-a777-a191b2618e3f" />

Users can view and update their login credentials securely through a simple and user-friendly interface.
<img width="1366" height="768" alt="Screenshot (29)" src="https://github.com/user-attachments/assets/c40365b8-0b13-4753-a708-9cdcf7513efd" />


---

## Features
- **Patient Management**: Add, update, view, delete patients.  
- **Therapist Management**: Add, update, view, delete therapists.  
- **Program Management**: Add therapy programs with cost, duration, and description.  
- **Session Scheduling**: Link sessions to patients, therapists, and programs.  
- **Payment Tracking**: Track payments with status.  
- **User Management**: Admins manage user accounts with roles.

---

## Database Schema

| Table Name        | Fields |
|------------------|--------|
| **patients**      | id, cost, description, duration, name |
| **therapists**    | id, name, program, status |
| **therapyprograms** | id, cost, description, duration, name |
| **therapysessions** | id, cost, description, patients_id, therapists_id, therapyPrograms_id |
| **payments**      | id, payment, status, patients_id, therapists_id |
| **users**         | id, username, password, role, jobRole |

**Relationships**:  
- `therapysessions` references `patients`, `therapists`, and `therapyprograms`  
- `payments` references `patients` and `therapists`

---

## Setup Instructions

1. **Clone Repository**
```bash
git clone https://github.com/namal1230/ORM-Project.git
````

2. **Install Dependencies (Maven)**

```bash
mvn clean install
```

3. **Set up MySQL Database**

```sql
CREATE DATABASE therapy_db;
USE therapy_db;
```

4. **Create Tables** (see [Database Schema](#database-schema))
5. **Insert Sample Data** (see [Sample Data](#sample-data))
6. **Configure `hibernate.cfg.xml`** with your DB credentials.
7. **Run the Project** via IDE or command line.

---

## Sample Data

### Patients

```sql
INSERT INTO patients (cost, description, duration, name) VALUES
(200.0, 'Initial consultation', '30 mins', 'Alice Perera'),
(350.0, 'Follow-up therapy', '45 mins', 'Rohan Silva'),
(150.0, 'Short session therapy', '20 mins', 'Nimal Fernando');
```

### Therapists

```sql
INSERT INTO therapists (name, program, status) VALUES
('Dr. Sunil Jayasinghe', 'Physical Therapy', 'ACTIVE'),
('Dr. Chamara Weerasinghe', 'Occupational Therapy', 'ACTIVE'),
('Dr. Nadeeka Fernando', 'Speech Therapy', 'INACTIVE');
```

### Therapy Programs

```sql
INSERT INTO therapyprograms (cost, description, duration, name) VALUES
(500.0, 'Program for managing chronic back pain', '8 weeks', 'Back Pain Therapy'),
(300.0, 'Program for improving daily activity skills', '6 weeks', 'Occupational Therapy'),
(400.0, 'Program for improving speech and communication', '10 weeks', 'Speech Therapy');
```

### Therapy Sessions

```sql
INSERT INTO therapysessions (cost, description, patients_id, therapists_id, therapyPrograms_id) VALUES
(200.0, 'Initial assessment and plan', 1, 1, 1),
(350.0, 'Follow-up therapy session', 2, 2, 2),
(150.0, 'Short corrective session', 3, 1, 1),
(400.0, 'Speech improvement session', 1, 3, 3);
```

### Payments

```sql
INSERT INTO payments (payment, status, patients_id, therapists_id) VALUES
(200.0, 'PAID', 1, 1),
(350.0, 'PENDING', 2, 2),
(150.0, 'PAID', 3, 1);
```

### Users

```sql
INSERT INTO users (username, password, role, jobRole) VALUES
('admin', 'admin123', 'ADMIN', 'Administrator'),
('therapist1', 'pass123', 'THERAPIST', 'Therapist'),
('staff1', 'staff123', 'STAFF', 'Receptionist');
```

---

## Technologies Used

* Java 17
* Hibernate ORM
* MySQL
* JavaFX
* Maven

---

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -m "Add new feature"`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

---

## License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.
