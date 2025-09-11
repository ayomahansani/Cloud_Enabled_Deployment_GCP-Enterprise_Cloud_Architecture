# Cloud Enabled Deployment In Action with Google Cloud Provider

This repository contains four projects:

- course-service (Spring Boot + MySQL)
- student-service (Spring Boot + MongoDB)
- media-service (Spring Boot + Local file storage, can be extended to S3/MinIO)
- frontend-app (React + TypeScript)

## Backend Services

### 1. course-service
- **Entity**: `Course(id, name, duration)`
- **Endpoints**:
  - `GET /courses`
  - `GET /courses/{id}`
  - `POST /courses`
  - `DELETE /courses/{id}`
- **Default port**: `8081`

#### ⚙️ GCP MySQL Configuration
The service is configured to connect to a **Google Cloud-hosted MySQL instance:**

```properties
spring.datasource.host=35.225.80.61
spring.datasource.port=3306
spring.datasource.url=jdbc:mysql://${spring.datasource.host}:${spring.datasource.port}/eca_courses?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=mysql-ECA-12
```


### 2. student-service
- Document: Student(registrationNumber, fullName, address, contact, email)
- Endpoints:
  - GET /students
  - GET /students/{id}
  - POST /students
  - DELETE /students/{id}
- Default port: 8082
- Configure MongoDB settings

### 3. media-service
- Resource: files
- Endpoints:
  - POST /files (multipart/form-data: file)
  - GET /files (list)
  - GET /files/{id} (fetch)
  - DELETE /files/{id} (delete)
- Default port: 8083
- Uses local disk storage at `./data/media` by default (override with env var `MEDIA_STORAGE_DIR`).

## Frontend (frontend-app)
- React + TypeScript + MUI + Axios + Vite app with 3 sections: Courses, Students, Media
- Scripts:
  - npm run dev (Vite dev server)
  - npm run build (TypeScript build + Vite build)
  - npm run preview (Preview built app)

## Build

- Backend: run `mvn -q -e -DskipTests package` at repo root to build services.
- Frontend: run `npm install` then `npm run dev` inside `frontend-app`.

## Resources

- Check out how the project works in this demo video on Google Drive:
  https://drive.google.com/file/d/10odRfqssuUkCpaBhnToJQcQdMXa65VNZ/view?usp=sharing

## License

- This project is licensed under the MIT License. 
- Feel free to reuse, extend, or modify it for educational or commercial purposes.