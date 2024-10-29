# Medical_appointment_portal_backend
# Theory

## How the Backend Works
### Overview
This backend is built using Node.js, Express, and MySQL. It provides endpoints for user authentication and appointment management. The backend is structured to handle two types of users: patients and doctors. Patients can register, log in, and schedule appointments, while doctors can approve appointments and view all scheduled appointments.

### Key Components
#### Database Configuration:
The database is configured using MySQL. The database.js file initializes the database and creates the necessary tables (usuarios and citas).
#### Routes:
Authentication Routes (authRoutes.js): Handles user registration and login.
Appointment Routes (citasRoutes.js): Manages appointment scheduling, approval, and retrieval.
#### Controllers:
Auth Controller (authController.js): Contains the logic for user registration and login.
Citas Controller (citasController.js): Contains the logic for scheduling, approving, and retrieving appointments.
#### Models:
User Model (userModel.js): Interacts with the usuarios table.
Citas Model (citasModel.js): Interacts with the citas table.
### Workflow
User Registration:
Patients can register by sending a POST request to /auth/register with their details. The backend validates the data and creates a new user in the usuarios table.
#### User Login:
Users (patients and doctors) can log in by sending a POST request to /auth/login with their email and password. The backend verifies the credentials and returns the user data if valid.
#### Scheduling Appointments:
Patients can schedule appointments by sending a POST request to /citas with the appointment details. The backend saves the appointment in the citas table with a status of “pending”.
#### Approving Appointments:
Doctors can approve appointments by sending a PUT request to /citas/:id/aprobar with the appointment ID. The backend updates the appointment status to “approved”.
#### Retrieving Appointments:
Users can retrieve appointments by sending a GET request to /citas with their user ID and type (patient or doctor). Patients can only see their own appointments, while doctors can see all appointments.

# Practice
## About requests and how they are handled:

## Authentication
### User (Patient) Registration

+ URL: http://localhost:5000/auth/register
+ Method: POST
+ Description: Allows patients to register on the platform.
+ Request Body (JSON):
+JSON
`{
"name": "Patient Name",
"email": "patient@example.com",
"password": "password123",
"type": "patient"
}`

### Login
+ URL: http://localhost:5000/auth/login
+ Method: POST
+ Description: Allows users (patients and doctors) to log in.
+ Request Body (JSON):
+ JSON
`{
"email": "user@example.com",
"password": "password123"
}`
## Appointment Management
### Schedule Appointment (Patients)
+ URL: http://localhost:5000/appointments
+ Method: POST
+ Description: Allows patients to schedule an appointment.
+ Request Body (JSON):
+ JSON
`{
"patient_id": 1,
"date": "2024-11-01",
"time": "10:00:00",
"description": "General consultation"
}`
### Approve Appointment (Doctors)
+ URL: http://localhost:5000/appointments/:id/approve
+ Method: PUT
+ Description: Allows doctors to approve a pending appointment.
+ URL Parameter: :id is the ID of the appointment to be approved.
### Get Appointments
+ URL: http://localhost:5000/appointments
+ Method: GET
+ Description: Allows users to get appointments. Patients can only see their own appointments, while doctors can see all appointments.
+ Query Parameters:
user_id: ID of the user requesting the appointments.
type: Type of user (patient or doctor).
