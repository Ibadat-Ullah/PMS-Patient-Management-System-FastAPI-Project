# 🏥 Patient Management System API

A RESTful **Patient Management System API** built with **FastAPI** and **Pydantic**. This project demonstrates how to build a backend API that performs CRUD (Create, Read, Update, Delete) operations on patient records while automatically calculating each patient's **BMI (Body Mass Index)** and corresponding health status.

The application uses a **JSON file as a lightweight database**, making it ideal for learning FastAPI, API development, data validation, and REST principles.

---

## ✨ Features

- ✅ Create new patient records
- ✅ Retrieve all patients
- ✅ Retrieve a patient by ID
- ✅ Update existing patient information
- ✅ Delete patient records
- ✅ Sort patients by Height, Weight, or BMI
- ✅ Automatic BMI calculation
- ✅ Automatic BMI health classification
- ✅ Input validation using Pydantic
- ✅ Proper HTTP status codes and error handling
- ✅ Interactive Swagger API documentation

---

# 📂 Project Structure

```
patient-management-api/
│
├── main.py               # FastAPI application
├── patients.json         # JSON database
├── requirements.txt      # Project dependencies
└── README.md             # Documentation
```

---

# 🚀 Technologies Used

- Python 3.10+
- FastAPI
- Pydantic v2
- Uvicorn
- JSON

---

# 📦 Installation

## 1. Clone the repository

```bash
git clone https://github.com/yourusername/patient-management-api.git

cd patient-management-api
```

---

## 2. Create a virtual environment (Recommended)

### Windows

```bash
python -m venv venv

venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv

source venv/bin/activate
```

---

## 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## 4. Run the application

```bash
uvicorn main:app --reload
```

If your file has a different name, replace `main` with your filename.

Example:

```bash
uvicorn app:app --reload
```

---

# 🌐 API URL

Once running:

```
http://127.0.0.1:8000
```

---

# 📚 API Documentation

FastAPI automatically generates interactive documentation.

### Swagger UI

```
http://127.0.0.1:8000/docs
```

### ReDoc

```
http://127.0.0.1:8000/redoc
```

---

# 📋 Patient Model

Each patient contains the following fields:

| Field | Type | Description |
|---------|------|------------|
| id | String | Unique Patient ID |
| name | String | Patient name |
| city | String | City of residence |
| age | Integer | Patient age |
| gender | male / female / others | Patient gender |
| height | Float | Height in meters |
| weight | Float | Weight in kilograms |
| bmi | Float | Automatically calculated |
| verdict | String | Automatically calculated health category |

---

# ⚖️ BMI Classification

BMI is calculated automatically using:

```
BMI = Weight / Height²
```

| BMI Range | Verdict |
|------------|----------|
| < 18.5 | UnderWeight |
| 18.5 - 24.9 | Normal |
| 25.0 - 29.9 | OverWeight |
| ≥ 30 | Obese |

---

# 🔗 API Endpoints

---

## 1. Home

### GET /

Returns a welcome message.

Response

```json
{
    "message": "Patient Management System API"
}
```

---

## 2. About

### GET /about

Returns API information.

Response

```json
{
    "message": "A fully functional API to manage your patient records"
}
```

---

## 3. View All Patients

### GET /view

Returns every patient stored in the database.

---

## 4. View Patient by ID

### GET

```
/patient/{patient_id}
```

Example

```
/patient/P001
```

Returns the patient information.

If the patient does not exist:

```json
{
    "detail":"Patient Not Found"
}
```

---

## 5. Create Patient

### POST

```
/create
```

Request Body

```json
{
    "id":"P001",
    "name":"John Doe",
    "city":"New York",
    "age":25,
    "gender":"male",
    "height":1.75,
    "weight":70
}
```

Successful Response

```json
{
    "message":"Patient created successfully"
}
```

---

## 6. Update Patient

### PUT

```
/edit/{patient_id}
```

Example

```
/edit/P001
```

Only send the fields you want to update.

Example

```json
{
    "weight":82
}
```

BMI and Verdict are automatically recalculated after every update.

Response

```json
{
    "message":"patient updated"
}
```

---

## 7. Delete Patient

### DELETE

```
/delete/{patient_id}
```

Response

```json
"Patient deleted successfully"
```

---

## 8. Sort Patients

### GET

```
/sort
```

Query Parameters

| Parameter | Description |
|------------|------------|
| sort_by | height, weight, bmi |
| order | asc or desc |

Example

```
/sort?sort_by=bmi&order=desc
```

---

# 📁 Database

This project uses a local JSON file as its database.

Example:

```json
{
    "P001": {
        "name": "John Doe",
        "city": "New York",
        "age": 25,
        "gender": "male",
        "height": 1.75,
        "weight": 70,
        "bmi": 22.86,
        "verdict": "Normal"
    }
}
```

---

# ❗ Error Handling

The API returns appropriate HTTP status codes.

| Status Code | Meaning |
|-------------|----------|
| 200 | Success |
| 201 | Resource Created |
| 400 | Invalid Request |
| 404 | Patient Not Found |

Example:

```json
{
    "detail":"Patient already exists"
}
```

---

# 🛠 Validation

The API validates all incoming data using **Pydantic**.

Validation includes:

- Positive age
- Age less than 120
- Positive height
- Positive weight
- Required fields
- Valid gender values
- Automatic type conversion

---

# 📌 Future Improvements

Some possible enhancements include:

- SQLite or PostgreSQL database
- SQLAlchemy ORM integration
- User authentication with JWT
- Pagination
- Search patients by city or age
- Docker support
- Unit testing with Pytest
- Environment variable configuration
- Logging
- API versioning

---

# 📜 Requirements

```
fastapi
pydantic
uvicorn
```

Install using

```bash
pip install -r requirements.txt
```

---

# 👨‍💻 Learning Objectives

This project demonstrates:

- FastAPI fundamentals
- REST API development
- CRUD operations
- Request validation
- Response models
- Path parameters
- Query parameters
- Exception handling
- Computed fields in Pydantic
- JSON file storage
- API documentation generation

---

# 📄 License

This project is open-source and available under the **MIT License**.

---

## ⭐ If you found this project useful, consider giving it a star on GitHub!
