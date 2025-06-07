# Photoz Spring Boot File Upload Example

This project is a simple **Spring Boot** application demonstrating how to upload photos (files) through a web interface and store them in a database. The backend is implemented in Java with Spring Boot, and the frontend uses a basic HTML form.

---

## Features

- Upload images via a web page (`upload.html`)
- Store file metadata (name, content type) and binary data in a database table
- RESTful API endpoint for handling file uploads
- Example error handling for invalid requests

---

## Requirements

- Java 17+ (or your project's required version)
- Maven or Gradle
- H2 database (in-memory, for demo)
- Spring Boot

---

## Getting Started

### 1. **Clone the repository**

```bash
git clone https://github.com/yourusername/photoz-springboot-upload.git
cd photoz-springboot-upload
```

### 2. **Run the application**

```bash
./mvnw spring-boot:run
# or
./gradlew bootRun
```

### 3. **Open the upload page**

Go to [http://localhost:8080/upload.html](http://localhost:8080/upload.html) in your browser.

---

## File Upload Endpoint

- **POST** `/photoz`
  - Accepts: `multipart/form-data`
  - Parameter: `file` (the file to upload)

**Example HTML form:**
```html
<form action="/photoz" method="post" enctype="multipart/form-data">
  <input type="file" name="file" />
  <button type="submit">Upload</button>
</form>
```

---

## Database Table

The uploaded files are stored in the `photoz` table:

| Column        | Type           | Description              |
|---------------|----------------|--------------------------|
| id            | BIGINT (auto)  | Primary key              |
| file_name     | VARCHAR(255)   | Name of the uploaded file|
| content_type  | VARCHAR(255)   | MIME type                |
| data          | BLOB           | File binary data         |

---

## Troubleshooting

- **400 Bad Request**:  
  - Ensure your HTML form uses `enctype="multipart/form-data"` and the input name is `file`.
  - Your backend controller should use `@RequestParam("file") MultipartFile file`.

---


## Author

Aziz Sfaihi
