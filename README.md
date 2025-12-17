# 🏕️Kheyma: Camping Reservation System Website
Discover, review, and book campsites across Egypt! KHEYMA is a full-stack reservation system, combining a **Spring Boot + MongoDB backend** with a **React + Vite frontend** to deliver a seamless user experience.

---

<p align="center">
  <img src="https://img.shields.io/badge/Java-SpringBoot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Java Badge">
  <img src="https://img.shields.io/badge/React-Vite.js-61DAFB?style=for-the-badge&logo=react&logoColor=black">
  <img src="https://img.shields.io/badge/MongoDB-Atlas-47a248?style=for-the-badge&logo=mongodb&logoColor=white">
  <img src="https://img.shields.io/badge/TailwindCSS-Documentation-38B2AC?style=for-the-badge&logo=tailwindcss&logoColor=white">
</p>

---

## 📖 **About the Project**  
KHEYMA allows users to:  
- **Search and filter** campsites, complete with reviews and ratings.  
- **Securely book reservations** with a dynamic transaction lifecycle.  
- **Manage listings** via a role-based access system (USER/Admin).  
- **View dynamic stats** using an admin dashboard, backed by AOP-logged metrics.  
The platform also includes **system diagrams (UML, ERD)** and an **SRS document** for seamless onboarding.

---

## 🛠️ **Tech Stack**

### 🔹 **Backend**
![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=java&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47a248?style=for-the-badge&logo=mongodb&logoColor=white)  
🔑 **JWT-based Authentication**, **AOP Logging**, **CORS Preconfiguration**

### 🔹 **Frontend**
![React](https://img.shields.io/badge/React-61dafb?style=for-the-badge&logo=react&logoColor=black)
![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-38b2ac?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=FFD020)  
☁️ Scalable SPA with responsive design and optimized development server

### 🔹 **Tools & Services**
![Postman](https://img.shields.io/badge/API%20Testing-Postman-orange?style=for-the-badge&logo=postman&logoColor=white)  
⚙️ Endpoint testing, **Error Tracking**, and flow validation

---

## 🏗️ **Quick Setup**

### 🔸 **Backend Setup**
```bash
cd kheyma_backend
# Export environment variables (Optional)
export JWT_SECRET=your-jwt-secret
export MONGODB_URI=your-mongo-uri

mvn spring-boot:run
```
- Runs at `http://localhost:8080/api`.  
- Configuration files exist in: `src/main/resources/application.yml`.

### 🔸 **Frontend Setup**
```bash
cd kheyma_frontend

npm install
npm run dev -- --host --port 5173
```
- Serves app at `http://localhost:5173`.  
- Update `.env` configurations:
  ```
  VITE_API_BASE_URL=http://localhost:8080/api
  ```

---

## ⚙️ **Key Features**

- **Secure Authentication with JWT**:
  - Login, registration, and token refresh workflows.
  - Role-based access (USER, ADMIN).
- **Campsite Listing Management**:
  - Full CRUD implementation, with search, pagination, and filters.
- **Reservation Booking System**:
  - End-to-end transaction lifecycle, with admin management support.
- **Dynamic Admin Dashboard**:
  - User analytics and proactive campground monitoring.
- **Preloaded Documentation**:
  - Core diagrams (UML, sequence, ERD) to aid contributors.

---

## 🏗️ **Project Structure**  

```
KHEYMA/
├─ README.md                    # Main README for the project
├─ docs/
│  ├─ API_ENDPOINTS.md          # API reference documentation
│  ├─ Activity_diagram.png      # Activity diagram
│  ├─ Class Diagram with OCL.svg # Class diagram with constraints
│  ├─ ERD.svg                   # Entity Relationship Diagram (ERD)
│  ├─ Sequence Diagram.svg      # Sequence diagram
│  ├─ Use Case Diagram with OCL.svg # Use case diagram with constraints
│  ├─ Software Requirements Specificiation.pdf # SRS document
├─ kheyma_backend/
│  ├─ README.md
│  ├─ pom.xml
│  └─ src/main/
│     ├─ java/com/kheyma/
│     │  ├─ aop/
│     │  ├─ config/
│     │  ├─ controller/
│     │  ├─ database/
│     │  ├─ dto/
│     │  ├─ exception/
│     │  ├─ model/
│     │  ├─ repository/
│     │  ├─ security/
│     │  ├─ service/
│     │  └─ util/
│     └─ resources/
│        └─ application.yml
└─ kheyma_frontend/
   ├─ package.json
   ├─ package-lock.json
   ├─ vite.config.js
   ├─ tailwind.config.js
   ├─ eslint.config.js
   ├─ public/
   └─ src/
      ├─ main.jsx
      ├─ App.jsx
      ├─ App.css / index.css
      ├─ assets/
      ├─ components/
      ├─ contexts/
      ├─ pages/
      └─ services/
```

## 💻 **Frontend Highlights**

- **TailwindCSS Styling**: Modern, scalable, and responsive.  
- **Routing**: Dynamic flow between search, booking, and dashboard.  
- **Modular Codebase**: Powered by components for easy scaling.

---

## 📊 **Backend Highlights**

- **MongoDB Collections**:
  - `users`, `locations`, `reviews`, `transactions`.  
- **Log Tracking with AOP**: Covers request/response logging.
- **Error Handling**: Centralized exceptions for better debugging.

---

<p align="center">
  <img src="https://github.com/JayantGoel001/JayantGoel001/blob/master/WEBP/footer.webp" alt="Footer Image"/>
</p>
