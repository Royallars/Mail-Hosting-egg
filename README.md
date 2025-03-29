# Mailcow Email Hosting on Pterodactyl

NOT WORKING!!!

This guide will walk you through setting up a **Mailcow** email server using a custom **Pterodactyl egg**. The Mailcow server is containerized with **Docker**, making it easy to deploy and manage email services on your server.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Pterodactyl Egg Installation](#pterodactyl-egg-installation)
3. [Creating the Server](#creating-the-server)
4. [Configuring Mailcow](#configuring-mailcow)
5. [Post-Setup](#post-setup)
6. [Troubleshooting](#troubleshooting)
7. [Additional Resources](#additional-resources)

---

## 1. Prerequisites

Before getting started, make sure you have the following:

- **Pterodactyl Panel** and **Wings** installed and configured.
- A server with **at least 4GB RAM**, **2 CPUs**, and **20GB disk** to run Mailcow efficiently.
- **Docker** and **Docker Compose** installed on the host machine (required for Mailcow).
- A registered domain with the ability to configure DNS records (MX, SPF, DKIM).

## 2. Pterodactyl Egg Installation

### Importing the Custom Egg

1. Go to your **Pterodactyl Admin Panel**.
2. Navigate to **Nests** → **Import Egg**.
3. Upload the provided **Mailcow egg** to import the Mailcow egg.

Once imported, Pterodactyl will automatically set up a `docker-compose.yml` file and a startup command for Mailcow.

## 3. Creating the Server

After importing the egg, create the server:

1. In the **Pterodactyl Panel**, navigate to **Servers** and click **Create New Server**.
2. Select the **Mailcow Email Hosting** egg.
3. Assign the following **resources** to the server:
   - **CPU**: 2 vCPUs (minimum).
   - **RAM**: 4GB or more (recommended).
   - **Disk Space**: 20GB minimum.
4. Click **Create Server** and then **Start** the server.

## 4. Configuring Mailcow

Once your server is running, you will need to configure Mailcow:

1. **Access the server console** through Pterodactyl.
2. **Navigate to the Mailcow directory**:
   - Run `cd /home/container/mailcow-dockerized` to move to the Mailcow directory.
3. **Generate a configuration**:
   - Copy the example configuration with `cp mailcow.conf.example mailcow.conf`.
4. **Edit the `mailcow.conf` file**:
   - Open the `mailcow.conf` file and set your **hostname**, **domain**, and any other necessary configuration options.
5. **Set proper file permissions**:
   - Ensure all files have the correct permissions with `chmod +x /home/container/mailcow-dockerized/*.sh`.
6. **Start Mailcow**:
   - Use Docker Compose to start the services: `docker-compose up -d`.

## 5. Post-Setup

After Mailcow has started, follow these steps to complete the setup:

1. **Configure DNS**:
   - Set up **MX**, **SPF**, **DKIM**, and **DMARC** records for your domain. These can be configured through your domain registrar's DNS management panel.
  
2. **Access Mailcow's Web Interface**:
   - Go to `http://<YOUR_SERVER_IP>` in your browser to access Mailcow's setup page.
   
3. **SSL Setup (Optional)**:
   - Configure **Let's Encrypt** to secure your email server with SSL certificates.

4. **Email Account Setup**:
   - From the Mailcow admin interface, create email accounts and manage your email domains.

## 6. Troubleshooting

Here are some common issues and solutions:

- **Docker not starting**:
  - Ensure Docker and Docker Compose are correctly installed. Run `docker --version` and `docker-compose --version` to verify installation.
  
- **Firewall Issues**:
  - Make sure that ports like **25**, **443**, **587**, and others required by Mailcow are open in your firewall.
  
- **SSL Configuration**:
  - If SSL issues occur, double-check your domain’s DNS settings and ensure your SSL certificates are correctly configured.

## 7. Additional Resources

- [Mailcow Documentation](https://mailcow.github.io/mailcow-dockerized-docs/)
- [Docker Documentation](https://docs.docker.com/)
- [Pterodactyl Documentation](https://pterodactyl.io/)

---

Feel free to ask for
    help on my discord server 
    https://discord.gg/3A2nEQFQrd
