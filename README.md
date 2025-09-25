Azure Blob Storage Project with Azure CLI

📌 Overview

The Azure Blob Storage Project demonstrates how to use Azure CLI in Cloud Shell to perform real-world cloud storage operations. Blob storage is a service for storing large amounts of unstructured data, such as text or binary files.

In this project, I worked with the following key steps:

 - **Creating a Storage Account – A storage account is the foundational resource in Azure that provides a unique namespace to store data.

- **Creating a Container – A container acts like a folder inside the storage account, helping organize and group blobs.

- **Uploading Files – Files (blobs) such as text documents and PDFs were uploaded to the container to simulate real use cases.

- **Verifying and Downloading Files – Uploaded files were verified and downloaded to ensure data integrity.

- **Adding Metadata – Metadata was attached to blobs in the form of key–value pairs to provide extra information, such as ownership and project name.

- **Listing Blobs – Finally, the container was queried to list blobs and confirm that metadata was successfully applied.

By completing this project, I gained hands-on experience with Azure storage services and learned how to manage cloud resources using the CLI. This is an essential foundation for more advanced cloud computing tasks.
---

## 🛠️ Technologies Used
- **Microsoft Azure**
- **Azure CLI** (Cloud Shell)
- **Azure Blob Storage**
- **GitHub** (for documentation & portfolio)

---

## 📂 Project Files
- `README.md` → Documentation of the project (this file).  
- `log.txt` → Raw terminal session log (commands + outputs).  
- `screenshots/` → Screenshots of key steps for reference.  

---

## 📸 Screenshots

Here are some screenshots from the process (replace with your actual images):

🚀 Step-by-Step Implementation
1️⃣ Create a Storage Account

A storage account is the top-level resource in Azure that provides a unique namespace for storing data.


### 2️⃣. Container Created 

A container organizes blobs inside a storage account (like a folder in a file system).
![Container Created](container%20created.JPG)  

### 3. Hello.txt File Upload Successful  
A blob is an individual file stored inside a container.
Here, a simple text file (hello.txt) is uploaded.
![Hello.txt Upload](hello%20txt%20file%20upoad%20succesful.JPG) 

### 4. Hello.txt File Check After Upload  
To confirm the upload worked, the file is downloaded again and verified locally.
![Hello.txt Check](hello%20txt%20file%20check%20after%20upload.JPG) 

### 5. After Uploading PDF & Verification  
To further test blob uploads, a PDF file was uploaded and verified in the container.
![PDF Upload Verification](after%20uploadind%20pdf,%20verification.JPG)  

### 6.  Add Metadata to the File  
Metadata provides extra information about a blob in key-value pairs.
![Metadata Added](metadata%20added%20successfully.JPG)  

### 7. Hello.txt Download and Verification (Part 1) 
Download the file back and confirm it matches the original.
![Download Verification 1](hellotxt%20download%20and%20verification.1.JPG)  

### 8. Hello.txt Download and Verification (Part 2)  
![Download Verification 2](hellotxt%20download%20and%20verification.2.JPG)  

**⚡ Challenges faced and Fixes**

File not found error (No such file or directory: 'hello.txt')

Cause: Tried uploading a file that was not in the current directory.

Fix: Created the hello.txt file locally before running the command.

Metadata not showing after update

Cause: Needed to re-run az storage blob show --query "metadata".

Fix: Confirmed metadata was successfully stored.

✅ **Conclusion**

In this project, I successfully:

Created a storage account and container in Azure

Uploaded and downloaded blobs

Added and verified metadata

Documented the process with screenshots and logs

Learned how to troubleshoot common issues

**This project gave me practical exposure to managing Azure Blob Storage, which is a foundational cloud skill.**
---

## 💻 Scripts / Commands Used

```bash
# Upload a file to storage
az storage blob upload \
  --account-name ifeanyistorage \
  --container-name projectfiles \
  --name hello.txt \
  --file hello.txt \
  --auth-mode login

# Download a blob
az storage blob download \
  --account-name ifeanyistorage \
  --container-name projectfiles \
  --name hello.txt \
  --file downloaded-hello.txt \
  --auth-mode login

# Update blob metadata
az storage blob metadata update \
  --account-name ifeanyistorage \
  --container-name projectfiles \
  --name hello.txt \
  --metadata owner=ifeanyi project=azurebootcamp \
  --auth-mode login

# Show blob metadata
az storage blob show \
  --account-name ifeanyistorage \
  --container-name projectfiles \
  --name hello.txt \
  --auth-mode login \
  --query "metadata"

# List blobs in the container
az storage blob list \
  --account-name ifeanyistorage \
  --container-name projectfiles \
  --auth-mode login \
  --query "[].{name:name, metadata:metadata}" \
  --output json 


