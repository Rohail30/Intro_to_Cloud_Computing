Here’s a detailed and well-explained version of the notes based on your PPT titled **"Storage and Content Delivery"**. I’ve broken it down into clear sections and simplified where needed, while keeping technical accuracy and depth.

---

## **Lecture 07: Storage and Content Delivery – AWS S3, CloudFront & EFS**

---

### **1. Amazon Simple Storage Service (Amazon S3)**

#### **Overview**

* Amazon S3 is an **internet-scale object storage service**.
* It allows you to **store and retrieve any amount of data** anytime, from anywhere using a web-based interface (API).
* It is **highly scalable, reliable, fast, and inexpensive**.
* You get access to the same infrastructure Amazon uses for its own global services.

---

### **2. Object Storage in S3**

#### **What is Object Storage?**

* Data is stored as **objects**, not files or blocks.
* Each object = data + metadata + unique identifier.
* Metadata is customizable and improves searchability.
* Stored in a **flat address space** – no folder hierarchy.

  * Easier to scale and retrieve data across regions.

---

### **3. Security in S3**

#### **Authorization & Access Control**

* **Identity Policies**: Attach to AWS IAM users/roles.
* **Bucket Policies**: Define who can do what on the bucket level.
* **ACLs (Access Control Lists)**: Legacy method, object-level permissions.

#### **CORS (Cross-Origin Resource Sharing)**

* Allows a web app from one domain to access resources in another.
* Useful for web applications that fetch data from S3 across domains.

#### **Encryption Types**

* **In Transit**: Encrypted via HTTPS (TLS).
* **At Rest**: Several options:

  * **SSE-S3**: Server-side encryption with S3 managed keys.
  * **SSE-KMS**: Server-side with AWS Key Management Service.
  * **SSE-C**: Server-side with customer-provided keys.
  * **Client-Side Encryption**: You encrypt data before uploading.

---

### **4. Versioning in S3**

* Can be **enabled per bucket**.
* Once enabled:

  * Any change creates a **new version** of the object.
  * Can't be turned off – only suspended.
* Helps in **data recovery** and rollback.

---

### **5. Presigned URLs**

* Grants temporary access to an object.
* Created using someone’s valid AWS credentials.
* Encoded with permissions and **expiry time**.
* Useful for secure, time-limited downloads/uploads.

---

### **6. S3 Storage Classes**

| Storage Class            | Use Case                    | Durability | Availability | Notes                              |
| ------------------------ | --------------------------- | ---------- | ------------ | ---------------------------------- |
| **Standard**             | Frequent access             | 11 9’s     | 99.99%       | Default, no minimums               |
| **Standard-IA**          | Infrequent but quick access | 11 9’s     | 99.9%        | Cheaper, 30-day & 128KB min.       |
| **One Zone-IA**          | Non-critical data           | 11 9’s     | 99.5%        | Only 1 AZ, cheaper                 |
| **Glacier**              | Archival (cold/warm)        | 11 9’s     | Varies       | Slow retrieval, 90-day min.        |
| **Glacier Deep Archive** | Long-term archival          | 11 9’s     | Varies       | Slowest but cheapest, 180-day min. |

---

### **7. Lifecycle Management**

* Automate **object transitions** between storage classes.
* Can also **expire/delete** objects automatically.
* Controlled using **lifecycle rules** at bucket level.

---

### **8. Cross-Region Replication (CRR)**

* Replicates objects **from one region to another**.
* Needs:

  * **Versioning enabled** on both source and destination buckets.
  * An **IAM role** for replication permissions.
* You can:

  * Keep the same storage class, owner, permissions.
  * Or override them during replication.

---

## **Amazon CloudFront – Content Delivery Network (CDN)**

### **What is CloudFront?**

* A CDN that delivers content via a **global network of edge locations**.
* Reduces latency and increases performance.

#### **Benefits**

* Lower latency
* Faster transfer
* Reduces load on origin servers

### **CloudFront Components**

* **Origin**: Where the original content lives (S3, EC2, etc.).
* **Distribution**: A configuration of how CloudFront delivers content.
* **Edge Location**: Local cache node to serve users quickly.
* **Regional Edge Cache**: Larger than edge locations; for wider area.

### **How It Works**

1. User accesses CloudFront URL.
2. It checks nearest **edge location** for cached content.
3. If found → content is served immediately.
4. If not → pulls from **regional cache** or **origin server**, caches it.

---

## **Amazon EFS (Elastic File System)**

### **What is EFS?**

* AWS-managed version of **Network File System (NFSv4)**.
* Can be mounted across **multiple Linux EC2 instances** simultaneously.

### **Performance Features**

* **Thousands of concurrent connections**
* **Up to 10Gbps throughput**
* **Petabyte-scale storage**
* Ideal for **shared file storage** in real-time apps

---

## ✅ Summary / Key Takeaways:

* **Amazon S3**: Great for storing static objects, scalable, supports security, versioning, and various storage classes.
* **Lifecycle Rules & Replication**: Allow automation of object management and cross-region backups.
* **CloudFront**: Distributes content closer to users for better speed and reduced load.
* **EFS**: Shared file storage for EC2 instances with scalable and high performance.

---

Would you like this in PDF format or as a Word doc for easy printing or submission?
