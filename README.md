# 🚗 Realistic Car Website with 403 Forbidden Simulation and Manual Bypass

This project simulates a **real-world web access restriction (403 Forbidden)** on a realistic car advertisement website hosted locally on **Kali Linux Apache Server**. It demonstrates how **access restrictions** can be enforced using `.htaccess` and how attackers may attempt to **bypass** these protections using HTTP header spoofing.

---

## 📌 Features

- Responsive static car advertisement website (`HTML + CSS`)
- Custom `403 Forbidden` access protection using `.htaccess`
- Apache2 server setup on Kali Linux
- Manual bypass simulation via `curl` (e.g., spoofing `X-Forwarded-For` header)
- Educational use case for web security students and ethical hackers

---

## 🛠️ Technologies Used

- Kali Linux (Debian based)
- Apache2 Web Server
- HTML5 / CSS3
- .htaccess (Apache access control)
- `curl` for request spoofing (no Burp Suite used)

---

## 🔧 Step-by-Step Setup

### 🔹 Step 1: Install and Start Apache Server
            sudo apt update
            sudo apt install apache2
            sudo service apache2 start

# Access default Apache page: http://localhost/ OR firefox http://localhost/carweb/

### 🔹 Step 2: Create Website Directory
            sudo mkdir /var/www/html/carweb
            cd /var/www/html/carweb

### 🔹 Step 3: Add Website Files
            sudo nano index.html (The HTML file has been added for download.)

### 🔹 Step 4: Enable .htaccess Overrides
            sudo nano /etc/apache2/apache2.conf
            Change:
                   <Directory /var/www/>
                        AllowOverride None
            To:
                   <Directory /var/www/>
                        AllowOverride All
  Restart Apache:
            sudo service apache2 restart

### 🔹 Step 5: Create .htaccess to Block Access
            sudo nano /var/www/html/carweb/.htaccess

            Add this:  
                      Order deny,allow
                      Deny from all
            Now visiting:
                      http://localhost/carweb/  OR  firefox http://localhost/carweb/
            
            # will show:  403 Forbidden

### 🔹 Step 6: Manual Bypass Simulation
   Update .htaccess to allow access from local IP:
   
            Order deny,allow
            Deny from all
            Allow from 127.0.0.1

Now try bypass with curl:

            curl http://localhost/carweb/ -H "X-Forwarded-For: 127.0.0.1"
            
➡️ Website will load successfully via spoofed header

✅ Educational Value

This project demonstrates:

How .htaccess can restrict access

Realistic simulation of web access denial (403)

Manual exploitation techniques (header spoofing)

Best practices in web access control configuration


### 📝 Summary of Commands

# Install & start Apache
sudo apt install apache2
sudo service apache2 start

# Create project folder
sudo mkdir /var/www/html/carweb
cd /var/www/html/carweb

# Create HTML, CSS, image
sudo nano index.html

# Enable .htaccess
sudo nano /etc/apache2/apache2.conf
# Change AllowOverride to All

# Restart server
sudo service apache2 restart

# Create protection
sudo nano .htaccess
# Add deny/allow rules

# Test bypass
curl http://localhost/carweb/ -H "X-Forwarded-For: 127.0.0.1"

🔐 Disclaimer
This project is strictly for educational purposes. Do not attempt unauthorized access to systems you do not own or have permission to test.

👨‍💻 Author
Lasindu Chathuranga Silva
Cybersecurity Undergraduate | Ethical Hacker | Web Security Enthusiast
🔗 LinkedIn Profile




   

                        
            


