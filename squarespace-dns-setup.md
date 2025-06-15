# 4. Configuring DNS on Squarespace

[![hackmd-github-sync-badge](https://hackmd.io/Ce6Zq1gYSGSCrWBvvU9ZbQ/badge)](https://hackmd.io/Ce6Zq1gYSGSCrWBvvU9ZbQ)

If you registered your domain through Squarespace or are using their platform to manage it, this guide will show you exactly how to edit your DNS records. We'll add the necessary records to point your domain to the Google Cloud VM you set up in the previous step.

[< Back to Main Menu](./README.md)

---

## Prerequisites

-   You have a domain managed by Squarespace.
-   You have the **External IP Address** of your Google Cloud VM. (We found this at the end of the `gcp-vm-setup.md` guide).

---

## Step 1: Navigate to Your DNS Settings

First, you need to find the DNS control panel for your domain within your Squarespace account.

1.  Log in to your **Squarespace** account.
2.  From the main dashboard, go to **Settings**, and then click **Domains**.
3.  You will see a list of your domains. Click on the domain name you want to configure.
4.  A new panel will open with details about your domain. Click on **DNS Settings**.

You should now see a list of your current DNS records. It might look a bit intimidating, but we only need to add or edit one or two records. Squarespace often pre-fills this area with default records that point to their own services. It's safe to remove any default `A` records or `CNAME` records that you don't need, but be careful not to delete `MX` records if you use Squarespace for email.

## Step 2: Add an 'A' Record to Point to Your VM

The **`A` record** is the primary record that links your domain name (e.g., `yourdomain.com`) to your server's IP address.

In the **Custom Records** section of the DNS Settings panel, you will add a new record.

1.  Click the **ADD RECORD** button.
2.  Fill in the fields using the information from the table below.

| Field | Value                                                 | Description                                            |
| :---- | :---------------------------------------------------- | :----------------------------------------------------- |
| **Host**  | `@`                                                   | The `@` symbol is a standard way to represent your main domain itself. |
| **Type**  | `A`                                                   | Select "A" from the dropdown list for an Address Record. |
| **TTL**   | `1h`                                                  | Time To Live. You can leave this at the default (usually 1 hour). |
| **Data**  | `YOUR_VM_IP_ADDRESS`                                  | **Crucial:** Replace this text with the External IP of your GCP VM. |

3.  Click **Save** or **Add** to confirm the new record.

## Step 3: Add a 'CNAME' Record for the 'www' Subdomain (Recommended)

You likely want visitors to be able to reach your site using `www.yourdomain.com` as well as just `yourdomain.com`. You can achieve this with a `CNAME` record that points `www` to your main domain.

1.  Click **ADD RECORD** again.
2.  Fill in the fields like this:

| Field | Value | Description                                                              |
| :---- | :---- | :----------------------------------------------------------------------- |
| **Host**  | `www` | This specifies that the record is for the `www` subdomain.               |
| **Type**  | `CNAME` | Select "CNAME" from the dropdown for a Canonical Name.                   |
| **TTL**   | `1h`  | You can leave this at the default.                                       |
| **Data**  | `@`   | The `@` symbol tells the `www` address to point to your main domain. |

3.  Click **Save** or **Add**.

## A Note on DNS Propagation

DNS changes are not instant. It can take anywhere from a few minutes to **48 hours** for your new DNS settings to spread across the entire internet. This is called DNS propagation. If you try to visit your domain immediately and it doesn't work, be patient and give it some time.

---

## What's Next?

You've done the main configuration work! You've told the internet where to find your server. The final step is to put it all together and verify that everything is working as expected.

**Next Guide: [5. Linking Your Domain to Your VM](./linking-domain-to-vm.md)**

[< Back to Main Menu](./README.md)