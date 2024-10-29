# Medical_appointment_portal
This project is an appointment scheduling web application for a healthcare entity. It features a landing page with three options: log in as a patient, log in as a doctor/admin, and register as a patient. The frontend is built with Vue.js, and the backend uses MySQL

# Autenticación
## Registro de Usuarios (Pacientes)

+ URL: http://localhost:5000/auth/register
+ Método: POST
+ Descripción: Permite a los pacientes registrarse en la plataforma.
Cuerpo de la Solicitud (JSON):
`JSON
{
  "nombre": "Nombre del Paciente",
  "email": "paciente@example.com",
  "password": "password123",
  "tipo": "paciente"
}`
AI-generated code. Review and use carefully. More info on FAQ.
Inicio de Sesión
URL: http://localhost:5000/auth/login
Método: POST
Descripción: Permite a los usuarios (pacientes y médicos) iniciar sesión.
Cuerpo de la Solicitud (JSON):
```JSON
{
  "email": "usuario@example.com",
  "password": "password123"
}
AI-generated code. Review and use carefully. More info on FAQ.
Gestión de Citas
Agendar Cita (Pacientes)
URL: http://localhost:5000/citas
Método: POST
Descripción: Permite a los pacientes agendar una cita.
Cuerpo de la Solicitud (JSON):
```json
  {
    "paciente_id": 1,
    "fecha": "2024-11-01",
    "hora": "10:00:00",
    "descripcion": "Consulta general"
}

AI-generated code. Review and use carefully. More info on FAQ.
Aprobar Cita (Médicos)
URL: http://localhost:5000/citas/:id/aprobar
Método: PUT
Descripción: Permite a los médicos aprobar una cita pendiente.
Parámetro de URL: :id es el ID de la cita que se va a aprobar.
Obtener Citas
URL: http://localhost:5000/citas
Método: GET
Descripción: Permite a los usuarios obtener citas. Los pacientes solo pueden ver sus propias citas, mientras que los médicos pueden ver todas las citas.
Parámetros de Consulta:
usuario_id: ID del usuario que solicita las citas.
tipo: Tipo de usuario (paciente o medico).
