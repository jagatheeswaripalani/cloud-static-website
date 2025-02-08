# 🖥️ Static Website Hosting on AWS S3  

## 🌟 Overview  
This project demonstrates how to host a **static website** (HTML, CSS, JavaScript) on **Amazon S3** and make it publicly accessible. The setup includes configuring **S3 bucket policies**, enabling **static website hosting**, and optionally integrating **CloudFront (CDN)** and **Route 53 (custom domain)**.  

## 🚀 Technologies Used  
- **AWS S3** – Storage & static website hosting  
- **AWS IAM** – Access management  
- **AWS CloudFront** – (Optional) Content Delivery Network (CDN)  
- **AWS Route 53** – (Optional) Custom domain mapping  

---

## 📌 Setup Instructions  

### **1️⃣ Create an S3 Bucket**  
1. Log in to [AWS S3 Console](https://s3.console.aws.amazon.com/s3).  
2. Click **"Create Bucket"** and enter a unique bucket name (e.g., `my-website-bucket`).  
3. Choose a region (e.g., `us-east-1`).  
4. Uncheck **"Block all public access"** to allow website access.  
5. Click **"Create Bucket"**.  

---

### **2️⃣ Upload Website Files**  
1. Open the newly created **S3 bucket**.  
2. Click **"Upload"** and select your **index.html, style.css, and other static files**.  
3. Click **"Upload"** to store them in S3.  

---

### **3️⃣ Enable Static Website Hosting**  
1. Go to the **"Properties"** tab of your bucket.  
2. Scroll down to **"Static website hosting"** and click **"Edit"**.  
3. Select **"Enable"**.  
4. Set the **index document** as `index.html`.  
5. Save the changes.  

✅ **Your website is now hosted!** You can find your **Bucket Website Endpoint URL** in this section.  

---

### **4️⃣ Make Files Public (Update Permissions)**  
1. Go to the **"Permissions"** tab of your bucket.  
2. Scroll down to **"Bucket policy"** and click **"Edit"**.  
3. Paste the following JSON policy (replace `your-bucket-name` with your actual bucket name):  

   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::your-bucket-name/*"
       }
     ]
   }
