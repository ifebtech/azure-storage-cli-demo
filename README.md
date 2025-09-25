# Azure Blob Storage Project with Azure CLI  

## 📌 Introduction  
This project demonstrates how to use **Azure Storage (Blob Service)** to store, manage, and retrieve files in the cloud.  

It shows the process of:  
- Creating a storage account  
- Creating a container  
- Uploading and downloading files  
- Adding and verifying metadata  
- Listing blobs with metadata  

By completing this project, I gained **hands-on practice** with Azure CLI commands and understood how storage resources are created and managed in the cloud.  

---

## 🛠️ Prerequisites  
Before starting, ensure you have:  
- An **Azure account** with access to Cloud Shell  
- **Azure CLI** (pre-installed in Cloud Shell)  
- Basic knowledge of using the terminal  

---

## 🚀 Step-by-Step Implementation  

### 1️⃣ Create a Storage Account  
A storage account is the top-level resource that provides a unique namespace to store and access your data.  

```bash
az storage account create --name ifeanyistorage --resource-group <your-resource-group> --location <your-location> --sku Standard_LRS

Screenshot:

3.2 Create a Container

A container organizes blobs within a storage account, similar to a folder in a file system. In this project, the container will store our project files.

Command:
az storage container create --name projectfiles --account-name ifeanyistorage --auth-mode login

Screenshot:

3.3 Upload a File (hello.txt)

A blob is an individual file stored inside a container. Here, we upload a simple text file (hello.txt) to test the upload functionality.

Command:
az storage blob upload --account-name ifeanyistorage --container-name projectfiles --name hello.txt --file hello.txt --auth-mode login

Screenshots:

3.4 Download and Verify the File

To confirm the upload worked, the file is downloaded again from Azure storage and compared locally.

Command:
az storage blob download --account-name ifeanyistorage --container-name projectfiles --name hello.txt --file downloaded-hello.txt --auth-mode login

Screenshots:

3.5 Add Metadata to the File

Metadata provides extra information about a blob in key-value pairs. In this project, metadata identifies the file owner and project name.

Command:
az storage blob metadata update --account-name ifeanyistorage --container-name projectfiles --name hello.txt --metadata owner=ifeanyi project=azurebootcamp --auth-mode login

Screenshot:

4. Full Command Reference

Here is the full list of commands used:

az storage account create --name ifeanyistorage --resource-group <your-resource-group> --location <your-location> --sku Standard_LRS

az storage container create --name projectfiles --account-name ifeanyistorage --auth-mode login

az storage blob upload --account-name ifeanyistorage --container-name projectfiles --name hello.txt --file hello.txt --auth-mode login

az storage blob download --account-name ifeanyistorage --container-name projectfiles --name hello.txt --file downloaded-hello.txt --auth-mode login

az storage blob metadata update --account-name ifeanyistorage --container-name projectfiles --name hello.txt --metadata owner=ifeanyi project=azurebootcamp --auth-mode login

az storage blob show --account-name ifeanyistorage --container-name projectfiles --name hello.txt --auth-mode login --query "metadata"

az storage blob list --account-name ifeanyistorage --container-name projectfiles --auth-mode login --query "[].{name:name, metadata:metadata}" --output json

5. Challenges and Fixes

File not found error (No such file or directory: 'hello.txt')

Cause: Tried uploading a file that was not present in the current directory.

Fix: Created the hello.txt file locally before running the upload command.

Metadata not showing after update

Cause: Needed to re-run az storage blob show with --query "metadata".

Fix: Confirmed the metadata was successfully stored.

These challenges helped me understand the importance of verifying each step and checking file paths carefully.

6. Conclusion

In this project, I successfully:

Created a storage account and container in Azure.

Uploaded and downloaded files (blobs).

Added and verified metadata.

Learned to troubleshoot common issues in Azure CLI.

This project gave me practical exposure to managing Azure Storage resources, which is a foundational skill for cloud computing.

