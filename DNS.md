**Domain Name System (DNS) - Notes**

### **DNS Basics**
- All computers on the Internet communicate using IP addresses.
- DNS translates human-readable domain names (e.g., www.example.com) into numeric IP addresses (e.g., 192.0.2.1).
- This process allows users to access websites without remembering complex IP addresses.
- **Amazon Route 53** is an example of an authoritative DNS service.
- The Internet’s DNS system works like a phone book, mapping domain names to IP addresses.

### **Types of DNS Services**

#### **1. Authoritative DNS**
- Maintains and provides official DNS records for a domain.
- Developers use it to manage public DNS names.
- It answers queries by translating domain names into IP addresses.
- **Amazon Route 53 is an authoritative DNS system.**

#### **2. Recursive DNS (Resolver DNS)**
- Acts as an intermediary between clients and authoritative DNS servers.
- When a user queries a domain, the recursive DNS service searches for the IP.
- If the answer is cached, it responds immediately.
- If not, it queries authoritative DNS servers to retrieve the information.

### **How DNS Routes Traffic to a Web Application**
The DNS resolution process involves multiple steps:

1. A user opens a web browser, enters **www.example.com**, and presses **Enter**.
2. The request is sent to a **DNS resolver** (usually provided by the ISP).
3. The DNS resolver forwards the request to a **root name server**.
4. The root name server directs the query to a **TLD (Top-Level Domain) name server** (e.g., for ".com" domains).
5. The TLD name server returns the **Amazon Route 53 name servers** associated with the domain.
6. The DNS resolver chooses one of the Route 53 name servers and requests the IP address.
7. The Route 53 name server looks in its **hosted zone** and returns the correct **IP address** (e.g., 192.0.2.44).
8. The DNS resolver caches the IP address and returns it to the user’s browser.
9. The web browser sends a request to the web server (e.g., an Amazon EC2 instance or an S3 bucket).
10. The web server responds with the requested website content.

### **DNS Records in Route 53**
- **A Record**: Maps a domain to an IPv4 address.
- **AAAA Record**: Maps a domain to an IPv6 address.
- **CNAME Record**: Aliases a domain name to another domain name.
- **MX Record**: Specifies mail servers for email delivery.
- **NS Record**: Specifies the authoritative name servers for a domain.
- **TXT Record**: Stores arbitrary text data (often used for verification purposes).
- **SOA Record**: Contains administrative information about the domain.

### **TTL (Time to Live) and Caching**
- TTL defines how long a DNS record is cached before it needs to be refreshed.
- High TTL values reduce query loads but can cause outdated records to persist longer.
- Low TTL values allow quicker updates but increase DNS query traffic.

### **Common DNS Issues and Troubleshooting**
- **Incorrect DNS records**: Ensure A/CNAME records point to the correct resources.
- **High TTL causing outdated cache**: Reduce TTL to allow faster updates.
- **Mismatched Name Servers**: Verify that NS records match the registrar's settings.
- **Domain Expiry**: Ensure domain is renewed and active.
- **Propagation Delay**: DNS updates may take time to reflect globally.
- **Firewall/Network Blocks**: Check security groups, firewalls, and network ACLs.

### **Best Practices for Managing DNS in AWS**
- Use **Route 53 Health Checks** to detect failures and switch traffic automatically.
- Enable **logging and monitoring** in Route 53 for tracking queries and errors.
- Implement **Failover Routing** to ensure high availability.
- Configure **Geo Routing** for regional content distribution.
- Keep TTL values optimized for performance and reliability.

This document provides a structured overview of DNS concepts and their relevance in AWS. Next, we will proceed with real-world troubleshooting scenarios to prepare for the AWS Cloud Support Associate role.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Now, let's go through some real-world DNS troubleshooting scenarios relevant to an AWS Cloud Support Associate role and how to handle them step by step.

1. Website Not Resolving to the Correct IP Address
Scenario: A user reports that their domain example.com is not resolving correctly, or they are getting an error like "DNS_PROBE_FINISHED_NXDOMAIN" in their browser.

Step-by-step troubleshooting:
Check Domain Registration & Expiry

Use whois example.com or check on AWS Route 53 to see if the domain is still registered.
Ensure the domain is not expired.
Verify DNS Configuration

Use nslookup example.com or dig example.com to check the authoritative name servers.
Ensure that the domain's NS (Name Server) records are correctly set to Route 53 name servers.
Check Route 53 Hosted Zone

Open AWS Route 53 Console → Go to Hosted Zones → Find example.com
Ensure an A Record exists and is pointing to the correct IP address of the web server.
Check for Propagation Issues

If DNS records were recently updated, it may take time to propagate. Use https://dnschecker.org/ to check if changes are reflected globally.
Verify TTL (Time-To-Live) Settings

If the TTL is set too high, users may still be seeing outdated DNS records. Reduce TTL for quick updates.
Clear Local DNS Cache

Ask the user to flush their DNS cache using:
arduino
Copy
Edit
ipconfig /flushdns  (Windows)  
sudo systemd-resolve --flush-caches  (Linux)  
They can also try using a different network or Google DNS (8.8.8.8) to see if the issue is local.
2. Subdomain Not Resolving
Scenario: A user has set up a subdomain blog.example.com, but it does not resolve.

Troubleshooting Steps:
Check for a CNAME or A Record in Route 53

Go to Route 53 → Hosted Zones → example.com
Ensure that a record exists for blog.example.com. It should either:
Be an A record pointing to an IP.
Be a CNAME record pointing to another domain.
Check Parent Domain's DNS Settings

Ensure that example.com itself is correctly resolving. If the parent domain is misconfigured, the subdomain may also fail.
Verify Web Server Configuration

If the subdomain is pointed to an EC2 instance, ensure the web server (Nginx, Apache) is configured to handle blog.example.com.
3. Incorrect SSL Certificate for a Domain
Scenario: A user reports that their domain secure.example.com is showing an SSL certificate error.

Troubleshooting Steps:
Check if the Domain is Using an AWS Certificate Manager (ACM) SSL

Open AWS ACM Console
Verify that the certificate includes secure.example.com.
Verify Load Balancer Configuration (If Any)

If using an Application Load Balancer (ALB), ensure that the listener for HTTPS (443) is correctly configured.
Check Certificate Expiry

Run openssl s_client -connect secure.example.com:443 and verify the certificate’s expiration date.
Check Browser Errors & Logs

Look at the specific browser error message:
"Certificate not trusted" → Check if it’s issued by a trusted CA.
"Mismatch error" → Ensure the certificate matches the domain name.
4. DNS Resolution Works Intermittently
Scenario: Some users can access the website, while others cannot.

Troubleshooting Steps:
Check for Multiple A Records (Load Balancer Issue)

If using a Load Balancer, ensure that all backend servers are healthy.
Check TTL Settings

If TTL is set too high, users may still be using an old cached DNS entry.
Verify Recursive DNS Server Issues

Ask the user to try dig example.com @8.8.8.8 (Google DNS) to check if their local ISP’s DNS resolver is the problem.
Check AWS Route 53 Health Checks

Go to Route 53 → Health Checks and verify that all endpoints are reachable.


