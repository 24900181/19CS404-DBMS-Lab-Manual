# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Darshini B

## Scenario Chosen:
University 

## ER Diagram:

![WhatsApp Image 2025-05-25 at 18 24 08_84038b5c](https://github.com/user-attachments/assets/698b5883-d03f-4e8f-bf9f-9a7ff45abf4a)

 
# University ER Diagram Breakdown

## Entities and Attributes

- **DEPARTMENT**
  - `DEPARTMENT_ID`
  - `DEPARTMENT_NAME`
  - `DEPARTMENT_HEAD`

- **ENROLLMENT**
  - `ENROLLMENT_ID`
  - `COURSE_ID`
  - `ENROLLMENT_DATE`

- **STUDENT_DETAILS**
  - `STUDENT_NAME`
  - `REGISTER_NO`
  - `EMAIL_ID`
  - `PHONE_NUMBER`
  - `PROGRAM_ID`
  - `DOB`

- **PRE_REQUISITE**
  - `COURSE_ID`
  - `PRE_REQUISITE_COURSE_ID`

---

## Relationships and Constraints

- **UNIVERSITY–DEPARTMENT**
  - **Cardinality**: One-to-Many (1:N)
  - **Participation**: Total on `DEPARTMENT` side

- **UNIVERSITY–ENROLLMENT**
  - **Cardinality**: One-to-Many (1:N)
  - **Participation**: Total on `ENROLLMENT` side

- **UNIVERSITY–STUDENT_DETAILS**
  - **Cardinality**: One-to-Many (1:N)
  - **Participation**: Total on `STUDENT_DETAILS` side

- **UNIVERSITY–PRE_REQUISITE**
  - **Cardinality**: One-to-Many (1:N)
  - **Participation**: Total on `PRE_REQUISITE` side

---

## Extension: Prerequisite Modeling

The **PRE_REQUISITE** entity captures prerequisite relationships between courses:
- `COURSE_ID`: Course that requires a prerequisite
- `PRE_REQUISITE_COURSE_ID`: The course that must be completed first

This design supports many-to-many prerequisite relationships using self-referencing.

> **Note**: Billing is not represented in the current ER diagram.

---

## Design Choices

- **Entity Separation**: Distinct entities for department, enrollment, student, and prerequisite for clarity and normalization.
- **Data Normalization**: Related attributes are grouped to reduce redundancy.
- **Prerequisite Logic**: Modeled as a separate entity for flexibility and scalability.
- **Assumptions**:
  - Students can enroll in multiple courses.
  - Courses can have multiple students and prerequisites.
  - Every department belongs to a university.

## RESULT
A normalized, scalable ER model capturing the academic structure of a university, ready for relational database implementation.

