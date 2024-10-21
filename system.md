# System Design for DOCSPOT

## 1. Client-Side (Frontend)
   - **Framework**: React (using React Bootstrap for views, Material-UI icons)
   - **Key Libraries**:
     - **Routing**: `useRoutes` for routing management
     - **Form Handling**: Formik
     - **Date/Time Management**: Moment.js
     - **State Management**: React Context API (no Redux)
   - **UI Components**:
     - **Navbar and Sidebar**: Separate components using React Bootstrap
     - **Dashboard**: Display top doctors list, appointments, and profile information
     - **Forms**: Doctor availability, appointment scheduling, profile editing using Bootstrap components and Formik
     - **WebSocket Integration**: Notifications count and list display for doctors
     - **Appointment Cards**: Cards with doctor's picture, experience, booking details, and actions

## 2. Backend (Server-Side)
   - **Framework**: Express.js
   - **Structure**:
     - **Controllers**: Handle incoming API requests, e.g., appointment booking, doctor availability
     - **Services**: Business logic for each feature, e.g., validating doctor slots, updating status
     - **WebSocket Implementation**: `wss` WebSocket server for real-time notifications
     - **File Uploads**: Endpoint for handling multiple file uploads related to appointments
   - **Database Interaction**: Mongoose for MongoDB operations

## 3. Database
   - **Database Type**: MongoDB
   - **Schemas**:
     - **Doctor**: Information like name, role, experience, specialization, availability (morning, afternoon, evening)
     - **Patient**: Name, contact info, and medical history
     - **Appointment**: Includes doctor ID, patient ID, appointment date, time slot, status, and reason for visit
     - **Files**: Stores uploaded files linked to appointments
   - **Indexes**: Optimize queries for frequently accessed data (e.g., doctor availability, upcoming appointments)

## 4. API Layer
   - **RESTful Endpoints**:
     - **Doctor Management**: CRUD operations for doctor information and availability
     - **Patient Management**: Patient registration and profile management
     - **Appointment Scheduling**: Book, edit, cancel appointments
     - **File Uploads**: Endpoints for uploading and retrieving appointment files
   - **Authentication**: JSON Web Tokens (JWT) for secure user sessions (doctors and patients)

## 5. WebSocket Server
   - **Real-Time Features**:
     - **Notifications**: Real-time status updates for doctors when appointments are booked, modified, or canceled
     - **Communication**: Manage WebSocket connections and events through `notifyUser` function in the `server.js`
