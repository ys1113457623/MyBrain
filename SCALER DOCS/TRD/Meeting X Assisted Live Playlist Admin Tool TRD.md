## **Project Overview**
This document outlines the trd for developing a admin tool that will help user in generating assisted live playlist .

---

## **System Architecture**

### **Components**

1. **Frontend (React):**
    - A web-based admin interface for file uploads.        
    - Communicates with the backend for signed URL generation and uses the URL to upload files directly to AWS S3.
2. **Backend (Ruby on Rails):**
    - Handles authentication and generates pre-signed URLs for secure file uploads.
3. **AWS Services:**
    - **S3:** Stores uploaded files securely.
    - **Lambda:** Processes the uploaded files upon S3 event notifications.

---

## **Functional Requirements**

1. **File Upload:**
    - Support for files up to 4GB in size.
    - Upload progress tracking on the frontend.
2. **File Processing:**
    - Trigger AWS Lambda upon file upload completion.
    - Preprocess files (e.g., unzip, validate, or analyze) and store results in S3.
3. **Admin Interface:**
    - User-friendly interface with drag-and-drop file upload support.
    - Feedback on upload status (e.g., success or failure notifications).
        

---
## **Non-Functional Requirements**
1. **Scalability:**
    - Handle concurrent uploads without performance degradation.
2. **Security:**
    - Secure S3 bucket access using pre-signed URLs and bucket policies.
    - Encrypt data at rest (S3 encryption) and in transit (HTTPS).
3. **Availability:**
    - High availability through reliable AWS services (S3, Lambda, etc.).
4. **Performance:**
    - Minimize upload time using multipart uploads and parallel processing.

---

## **Technical Design**

### **High-Level Architecture**

1. **React Frontend:**
    - File input and drag-and-drop functionality.
    - Makes API calls to the Rails backend for signed URLs.        
    - Directly uploads file to S3 using signed URLs.
        
2. **Rails Backend:**
    - Exposes an API endpoint to generate signed URLs.

3. **AWS Services:**
    - **S3 Bucket:** Configured for private access with event notifications enabled.
    - **Lambda Function:** Preprocess files after upload and stores results back in S3 and then call `https://www.scaler.com/admin/meetings/playlists` to scaler.

---

### **Workflow**

1. **Frontend Interaction:**
    - Admin uploads a file through the React interface.
    - React requests a signed URL from the backend.
2. **Backend Processing:**
    - Rails generates a signed URL and returns it to the frontend.
3. **Direct S3 Upload:**
    - React uses the signed URL to upload file chunks directly to S3.
4. **S3 Event Notification:**
    - Upon upload completion, S3 triggers a Lambda function.
5. **Lambda Processing:**
    - Lambda downloads the file, processes it (e.g., extracts content), and uploads results back to S3.
    - Lambda calls the API `https://www.scaler.com/admin/meetings/playlists` to ingest the processed video into Scaler.

---

## **Key APIs**

1. **Generate Signed URL (Backend):**
    - **Endpoint:** `POST /api/uploads/signed_url`
    - **Input:** `{ file_name: string }`
    - **Output:** `{ signed_url: string }`        

---

## **Risks and Mitigation**

1. **File Upload Failures:**
    - Use multipart uploads to resume failed uploads.
    - Implement retry logic in the frontend.
2. **Security Vulnerabilities:**
    - Restrict S3 access with IAM policies.
    - Validate file types and sizes on the backend.
3. **Performance Bottlenecks:**
    - Use parallel uploads for file chunks.
    - Optimize Lambda function execution time.
4. **Pre-Signed URL Expiration:**
	- Ensure the signed URL expiration time is sufficiently long for large file uploads
	- Implement logic in the frontend to request a new signed URL if the current one expires during upload.

![[Pasted image 20250122163806.png]]

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-best-practices.html#which-spot-request-method-to-use