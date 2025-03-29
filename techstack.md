# 🧵 Fashion Design Web App – Tech Stack Guide

This document lists the actual technologies we will use based on the finalized features of our 3-week project.

---

## 🔧 Backend (Flask API)

| Technology       | Purpose                                           |
|------------------|---------------------------------------------------|
| **Flask**        | Main backend framework for API and logic         |
| **Flask-CORS**   | Allow frontend (React) to access backend APIs    |
| **SQLite**       | Lightweight database to store data               |
| **python-dotenv**| Environment config management                    |

---

## 🌐 Frontend (React)

| Technology           | Purpose                                               |
|----------------------|-------------------------------------------------------|
| **React.js**         | Main frontend framework for SPA                      |
| **Tailwind CSS**     | Styling and layout with utility classes               |
| **React Router DOM** | Page routing (e.g., /sketch, /measurements)           |
| **Axios**            | Handle HTTP requests to Flask backend                 |

---

## 🎨 Sketching Tool

| Technology     | Purpose                                       |
|----------------|-----------------------------------------------|
| **Fabric.js**  | Canvas drawing library for garment sketches   |
| **HTML5 Canvas** | Base canvas rendering (used by Fabric.js)    |

---

## 📏 Measurement Input

| Technology          | Purpose                                       |
|---------------------|-----------------------------------------------|
| **React Forms**     | Capture body measurements manually            |
| *(No extra libs)*   | Use built-in form handling + validation       |

---

## 📐 Pattern Drafting

| Technology         | Purpose                                                    |
|--------------------|------------------------------------------------------------|
| **SVG (Scalable Vector Graphics)** | Generate 2D digital garment patterns          |
| **React + inline SVG** | Render and preview pattern layout in the browser       |
| **Custom Math Logic** | Use formulas to scale pattern to body measurements       |

> ❌ **Note**: We are NOT using full CAD software (like CLO3D, AutoCAD) due to complexity and licensing. Our approach is a lightweight SVG-based simulation of CAD pattern drafting.

---

## 🧵 Virtual Sewing (Preview Mockup)

| Technology          | Purpose                                                    |
|---------------------|------------------------------------------------------------|
| **Static Preview Images** | Show garment with pattern mockup (flat layout)       |
| *(Optional)* **Three.js** | If time allows: basic 3D mockup preview (not physics) |

---

## 📦 Supporting Tools

| Tool          | Purpose                          |
|---------------|----------------------------------|
| **VS Code**   | Code editor                      |
| **Git/GitHub**| Version control                  |
| **Browser DevTools** | UI + network request testing     |
| **Postman / Thunder Client** | API testing tool         |

---

## ✅ Summary Table

| Feature               | Technology Used                           |
|-----------------------|--------------------------------------------|
| UI Framework          | React.js                                  |
| Styling               | Tailwind CSS                              |
| Drawing / Sketching   | Fabric.js, HTML5 Canvas                   |
| Measurements Input    | React Forms                               |
| Pattern Generation    | React + SVG                               |
| Virtual Sewing Mockup | Static preview / Optional Three.js        |
| Backend API           | Flask, Flask-CORS                         |
| Database              | SQLite                                    |
| HTTP Client (Frontend)| Axios                                     |

