---
title: How to Set Up Azuracast for Your Own Internet Radio Station
author: Randy Black
date: 'Do not worry about this as it will be generated later'
categories:
  - Tutorials
tags:
  - Azuracast
  - Live Stream
  - Internet Radio
toc: true
---
This article was published orginially at [https://randallblack.com/azuracast/](https://randallblack.com/azuracast/) and is shared here by it's author.

# How to Set Up Azuracast for Your Own Internet Radio Station

Azuracast is a powerful, open-source web radio management software that allows you to easily stream both live and pre-recorded audio. Whether you're looking to host your own internet radio station or use it for podcasting, Azuracast makes the process straightforward. In this post, we’ll walk you through how to set up Azuracast on a server and get your station up and running.

## Prerequisites

Before starting the installation, ensure you have the following:

- **A server** (VPS or dedicated) running a Linux-based operating system like Ubuntu 20.04 or later.
- **Docker and Docker Compose** installed on your server.
- **A domain name** (optional) if you plan to use a custom URL instead of the default IP address.
  
### Step 1: Install Docker and Docker Compose

First, you’ll need to install Docker and Docker Compose on your server. Run the following commands:

```bash
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt install -y docker-ce docker-compose
```

Verify that Docker and Docker Compose were installed correctly:

```bash
docker --version
docker-compose --version
```

### Step 2: Download and Install Azuracast

Next, clone the Azuracast repository and install it on your server:

```bash
cd /var/azuracast
git clone https://github.com/AzuraCast/AzuraCast.git .
./docker.sh install
```

This script will automatically set up all the necessary containers and dependencies for Azuracast.

### Step 3: Access the Azuracast Web Interface

Once the installation is complete, the script will provide a URL to access the Azuracast web interface. By default, this will be on port 80 (HTTP) or 443 (HTTPS), and you can access it using:

```
http://<your-server-ip>/
```

You’ll be prompted to log in. The default admin credentials are:

- **Username**: `admin`
- **Password**: You’ll set this up during the installation.

### Step 4: Configure Your Station

After logging in, you'll need to set up your radio station. Follow these steps:

1. Click on **"Create a New Station"**.
2. Choose the type of stream you want to use: **SHOUTcast**, **Icecast**, or **AutoDJ**.
3. Set the basic details for your station, such as the stream name, description, genre, and more.
4. Customize additional settings, such as metadata and artwork for your station.

### Step 5: Upload Media

To populate your station with music, audio clips, or podcasts, you can upload media files. Azuracast allows you to organize your files into playlists that can be scheduled for automatic playback.

1. Go to the **"Media"** section.
2. Upload your audio files.
3. Create playlists to organize your content.

### Step 6: Broadcasting Your Stream

Azuracast supports both **live broadcasting** and **AutoDJ**.

#### Live Broadcasting

To broadcast live, you can use software like **OBS**, **BUTT (Broadcast Using This Tool)**, or any compatible broadcasting software. Azuracast provides you with a URL and password that you’ll input into your broadcasting software.

#### AutoDJ

AutoDJ automatically plays music from the library you’ve uploaded. You can configure the AutoDJ feature in your station’s settings and set it up to play content when you’re not broadcasting live.

### Step 7: Set Up a Custom Domain (Optional)

If you'd like to use a custom domain (e.g., `radio.yourdomain.com`), follow these steps:

1. Set up a **reverse proxy** using **Nginx** or **Apache**.
2. Update your domain’s DNS settings to point to your server’s IP address.
3. Optionally, use **Let’s Encrypt** to obtain a free SSL certificate for HTTPS support.

### Step 8: Monitor and Analyze Your Station

Azuracast provides real-time listener statistics and detailed analytics, including track information and playback history. You can access this data from the Azuracast dashboard to monitor your station's performance.

### Step 9: Backup and Updates

Regular backups of your Azuracast data are recommended. You can create backups using Docker commands. Azuracast also provides a feature to easily update to the latest version through the admin interface.

### Troubleshooting Tips

- **Firewall Settings**: Ensure that necessary ports (like 8000 for Icecast/SHOUTcast and 80/443 for the web interface) are open in your server’s firewall.
- **Logs**: If you encounter issues, you can check Azuracast logs for errors:
  ```bash
  docker-compose logs -f
  ```

## Conclusion

Azuracast is a versatile platform for managing your own internet radio station. Whether you’re streaming music, podcasts, or live events, its features are robust and easy to use. By following the steps in this guide, you’ll have your station up and running in no time!

If you run into any issues or need help with any part of the setup, feel free to reach out for assistance.
--------------------------------------------
Author info - Note this only needs to be submitted once as it gets saved on the site
You may submit again if you need to change your info
--------------------------------------------
"YOUR-NAME": "A brief description of yourself. May include [markdown formatted urls](https://your-website.com)"
