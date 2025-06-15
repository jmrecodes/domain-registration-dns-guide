# 2. DNS Fundamentals

Now that you have a domain name, it's time to understand how it communicates with the rest of the internet. This guide covers the basics of the Domain Name System (DNS), the service that translates your domain into something browsers and servers can use.

[< Back to Main Menu](./README.md)

---

## What is DNS?

DNS stands for **Domain Name System**. Its core job is to translate human-friendly domain names (like `www.example.com`) into computer-friendly IP addresses (like `93.184.216.34`). It's often called the "phonebook of the internet."

When you register a domain, your registrar provides you with a control panel to manage its DNS records. These records are like entries in the phonebook, telling the world where to send traffic for your domain.

## Common DNS Record Types

You'll encounter several types of DNS records. Here are the most common ones you'll need to know.

| Record Type | Name                     | Purpose                                                                                                 | Example Value                  |
| :---------- | :----------------------- | :------------------------------------------------------------------------------------------------------ | :----------------------------- |
| **A**       | Address Record           | Points a domain or subdomain to an **IPv4 address**. This is the most common record for a website.        | `93.184.216.34`                |
| **AAAA**    | IPv6 Address Record      | Points a domain or subdomain to an **IPv6 address**. It's the modern successor to the A record.           | `2606:2800:220:1:248:1893:25c8:1946` |
| **CNAME**   | Canonical Name Record    | Points a subdomain to another domain name (not an IP address). Useful for aliases, like `www` to `example.com`. | `example.com`                  |
| **MX**      | Mail Exchanger Record    | Directs email to a mail server. You'll use this if you set up a custom email address like `you@example.com`. | `10 mail.example.com`          |
| **TXT**     | Text Record              | Lets you store arbitrary text. Often used for verifying domain ownership with services like Google or Microsoft. | `google-site-verification=...` |

### Key DNS Terminology

-   **Nameservers (NS)**: These are the servers that hold the authoritative DNS records for your domain. When you manage your DNS with a provider like Squarespace or Cloudflare, you are using their nameservers. Changing your nameservers effectively "moves" your DNS management from one provider to another.
-   **Host / Name**: This is the part of the domain the record applies to. For your main domain (`example.com`), this is often represented by `@`. For a subdomain like `blog.example.com`, the host is `blog`.
-   **Value / Points to**: This is the destination data, such as an IP address or another domain name.
-   **TTL (Time To Live)**: This value, measured in seconds, tells DNS resolvers around the world how long to cache (store) the information for a DNS record. A common default is `3600` (1 hour). When you first set up a record, a lower TTL can be useful for faster updates.

## How Does a DNS Lookup Work?

In simple terms, when you type `www.example.com` into your browser:

1.  Your browser asks your computer's configured DNS resolver (often your ISP) for the IP address.
2.  The resolver checks its cache. If it doesn't have the answer, it queries the internet's DNS servers.
3.  It eventually finds the authoritative **nameservers** for `example.com`.
4.  It asks those nameservers for the `A` or `AAAA` record for `www.example.com`.
5.  The nameservers reply with the correct IP address.
6.  The resolver passes this IP address back to your browser.
7.  Your browser connects to the server at that IP address to load the website.

This entire process usually takes only milliseconds!

---

## What's Next?

You now understand the "what" and "how" of DNS. The next step is to create a server that you can point your domain to.

**Next Guide: [3. Setting Up a Google Cloud VM](./gcp-vm-setup.md)**

[< Back to Main Menu](./README.md)