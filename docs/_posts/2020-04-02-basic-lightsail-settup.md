---
title: "How to get started with Cloud Computing using AWS"
date: 2020-04-02T21:57:40+08:00
categories:
  - Blog
tags:
  - Linux
  - Bash
  - Terminal
---

## Use AWS Lightsail to get started 
The option to start the cloud computing power is using Amazon Lightsail. As Nijim, S says “Lightsail is an easy-to-use cloud platform that offers you everything needed to build an application or website, plus a cost-effective, monthly plan.”

### 1. Create aws account [here](https://portal.aws.amazon.com/billing/signup#/start) (a credit/debit card is required, you are charged what you use) Or [here](https://aws.amazon.com/)
<br />

### 2. Once in the aws console, look for **Lightsail** Service, and click on it.
<br />

![Leave as default](/assets/images/blogs/basic-lightsail-settup/lightsail.png) 
<br />

### 3. Let’s create a new instance
<br />

![Create Instance](/assets/images/blogs/basic-lightsail-settup/1_create_instance.png)
<br />

### 4.  We leave the instance location as the default. 
<br />

![Leave as default](/assets/images/blogs/basic-lightsail-settup/2_leave_as_default.png) 
<br />

### 5.  Select a platform, let’s choose Linux/Unix
<br />

![Select platorm](/assets/images/blogs/basic-lightsail-settup/3_os.png)
<br />

### 6.  Select a blueprint: we have 2 options, create an instance with only a OS, or a OS with a pre-configured app. To get the best of the instance let’s choose OS Only and select Debian 9.5
<br />

![Apps + OS](/assets/images/blogs/basic-lightsail-settup/4_appos.png)
<br />

![OS](/assets/images/blogs/basic-lightsail-settup/5_os.png)
<br />

### 7.  Choose Instance Plan
<br />

![Choose Plan](/assets/images/blogs/basic-lightsail-settup/6_choose_plan.png)

<br />

### 8.  Name Instance and quantity
<br />

![Name Instance](/assets/images/blogs/basic-lightsail-settup/7_Name_Instance.png)
<br />

### 9.  Select just created instance
<br />  

![Select the created instance](/assets/images/blogs/basic-lightsail-settup/8_selec_just_created_instance.png)
<br />

### 10. Select Network Tab
<br />

![Select Network Tab](/assets/images/blogs/basic-lightsail-settup/9_select_network_tab.png)
<br />

### 11. Attach static ip
<br />

![Attach static ip](/assets/images/blogs/basic-lightsail-settup/10_attach_static_ip.png)
<br />

![Create statip ip](/assets/images/blogs/basic-lightsail-settup/11_create_static_ip.png)
<br />

### 12. Add HTTPS rule to Firewall
<br />

![Add Rule](/assets/images/blogs/basic-lightsail-settup/12_add_rule.png)
<br />

![Create Rule](/assets/images/blogs/basic-lightsail-settup/13_create_rule.png)

<br />

### 13. Activate snapshots
<br />

![Select snapshot tab](/assets/images/blogs/basic-lightsail-settup/14_select_snapshot_tab.png)
<br />

![Activate automatic snapshot](/assets/images/blogs/basic-lightsail-settup/15_activate_snapshot.png)
<br />

### 14. Connect to the instance through ssh

<br />

![Select connect tab](/assets/images/blogs/basic-lightsail-settup/16_select_connect_tab.png)

<br />

![Connect using ssh](/assets/images/blogs/basic-lightsail-settup/17_connect_using_ssh.png)

<br />