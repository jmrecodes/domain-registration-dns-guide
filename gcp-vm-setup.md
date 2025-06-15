# 3. Setting Up a Google Cloud VM

[![hackmd-github-sync-badge](https://hackmd.io/ezm_7KU1QkSkNvwOoqwkuA/badge)](https://hackmd.io/ezm_7KU1QkSkNvwOoqwkuA)

This guide will walk you through creating a virtual machine (VM) using Google Cloud Platform's (GCP) Compute Engine. A VM is your own private server in the cloud, which you can use to host a website, run an application, or anything else you'd need a server for.

[< Back to Main Menu](./README.md)

---

## Why Google Cloud Platform?

GCP is a powerful and widely-used cloud provider. Its Compute Engine service offers a generous "Free Tier," which includes a small `e2-micro` VM running 24/7 at no cost (subject to Google's terms). This makes it an excellent, cost-effective choice for learning and for hosting small, personal projects.

### Prerequisites

-   A Google Account (like a Gmail account).
-   You may need to provide billing information to activate your GCP account, but you will not be charged as long as you stay within the Free Tier limits.

---

## Step-by-Step Guide to Creating a VM

### Step 1: Create a GCP Project

Everything in GCP is organized into projects.

1.  Go to the [Google Cloud Console](https://console.cloud.google.com/).
2.  In the top navigation bar, click the project selector dropdown (it might say "Select a project").
3.  In the dialog that appears, click **"NEW PROJECT"**.
4.  Give your project a descriptive name (e.g., "My First Web Server") and click **"CREATE"**.

### Step 2: Navigate to Compute Engine

Once your project is created, you need to enable the Compute Engine API and go to the right service.

1.  Make sure your new project is selected in the top project selector.
2.  Click the navigation menu (☰) in the top-left corner.
3.  Scroll down to **"Compute Engine"** and click on it.
4.  If this is your first time, you may need to click **"ENABLE"** to activate the Compute Engine API. This can take a minute or two.

### Step 3: Configure Your VM Instance

This is where you'll define the specifications for your server.

1.  In the Compute Engine dashboard, click **"CREATE INSTANCE"**.
2.  You'll see a form with many options. Here are the most important ones for a beginner:
    *   **Name**: Give your VM a simple, lowercase name (e.g., `web-server-1`).
    *   **Region and Zone**: Choose a region that is geographically close to your target audience to reduce latency. For example, `us-west1` (Oregon) or `europe-west2` (London). The zone doesn't matter as much, so you can leave the default.
    *   **Machine Configuration**:
        *   **Series**: Select `E2`.
        *   **Machine Type**: Select `e2-micro` or `e2-small`. The `e2-micro` is typically included in the GCP Free Tier.
    *   **Boot Disk**: This is your VM's hard drive and operating system.
        *   Click **"Change"**.
        *   **Operating System**: Select `Debian` or `Ubuntu`. A recent LTS (Long Term Support) version of Ubuntu is an excellent choice for beginners (e.g., Ubuntu 22.04 LTS).
        *   **Version**: Choose a standard version (not the "minimal" one).
        *   Click **"Select"**.
    *   **Firewall**: This is a critical step! To allow web traffic to reach your server, you must check both:
        *   **[✓] Allow HTTP traffic**
        *   **[✓] Allow HTTPS traffic**
3.  Review the other settings (you can leave them as default for now) and click **"CREATE"**.

Google will now provision and start your new virtual machine. This usually takes less than a minute.

### Step 4: Find Your VM's External IP Address

Once the VM is created, you'll be taken back to the Compute Engine instance list. You will see your new VM with a green checkmark next to it.

Look for the column named **"External IP"**. You will see a string of numbers (e.g., `34.12.123.45`).

**This is the public IP address of your server.** It's the "computer-friendly" address that we talked about in the DNS guide. Copy this IP address and save it somewhere safe. You will need it in the final step to link your domain to this server.

---

## Beyond the VM: Other Ways to Run Code on GCP

You've just learned how to create a VM with **Compute Engine**. This approach gives you maximum control and is considered **Infrastructure as a Service (IaaS)**. It's like renting an empty plot of land—you can build anything, but you're responsible for everything from the foundation up.

However, GCP offers a spectrum of services for running applications, where Google manages more of the underlying infrastructure for you. It's useful to know what they are and when you might choose them over a raw VM.

| Service                   | What You Provide                               | When to Use It                                                                 | Analogy                    |
| :------------------------ | :--------------------------------------------- | :----------------------------------------------------------------------------- | :------------------------- |
| **Compute Engine** (IaaS) | A full Virtual Machine with an OS              | For full control, legacy applications, or custom server setups.                | Renting an empty plot of land |
| **Google Kubernetes Engine (GKE)** | Docker Containers                              | For complex, microservice-based applications that need to scale efficiently. | Managing an apartment building |
| **App Engine** (PaaS)         | Your application code (e.g., Python, Node.js)  | For web applications and APIs where you don't want to manage servers at all. | Leasing a pre-built storefront |
| **Cloud Run** (Serverless)    | A stateless Docker Container                   | For event-driven services or APIs that can scale down to zero.                 | Using a hotel room        |
| **Cloud Functions** (FaaS)  | A single function or snippet of code           | For small, single-purpose tasks that respond to events (like a file upload).   | Renting a tool for one job |

**In summary:**

-   **Easiest to start with (for traditional web hosting):** `Compute Engine`. The skills you learn here are fundamental.
-   **Most powerful for modern, large-scale apps:** `GKE` and `Cloud Run`.
-   **Simplest for deploying web apps without server knowledge:** `App Engine`.

This guide focuses on Compute Engine because it's the foundational layer. Understanding how a VM works will give you a much better appreciation for what the other, more abstract services are doing for you behind the scenes.

---

## What's Next?

You now have a live, running server in the cloud! The next step is to configure your domain's DNS records to point to this server's IP address.

**Next Guide: [4. Configuring DNS on Squarespace](./squarespace-dns-setup.md)**

[< Back to Main Menu](./README.md)