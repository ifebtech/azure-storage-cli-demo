# Azure Storage CLI Demo

## 📌 Overview
This project demonstrates how to use the **Azure CLI** in **Azure Cloud Shell** to perform common blob storage operations.  
It shows how to create, upload, download, update metadata, and list blobs inside an Azure Storage container.  

The goal of this project is to practice **hands-on cloud skills** and document the process clearly so others can follow along.  

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

![Upload Screenshot](screenshots/upload.png)  
*Uploading a file to Azure Blob Storage*

![Download Screenshot](screenshots/download.png)  
*Downloading a blob back to Cloud Shell*

![Metadata Screenshot](screenshots/metadata.png)  
*Updating and viewing blob metadata*

![List Blobs Screenshot](screenshots/list.png)  
*Listing blobs in the container with metadata*

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
