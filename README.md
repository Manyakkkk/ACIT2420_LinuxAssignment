# ACIT2420_LinuxAssignment
Creating a Remote Server using DigitalOcean: A Step-by-Step Guide

## Introduction

In this tutorial, we will create a remote server using DigitalOcean, a popular cloud infrastructure provider. We will cover the basics of creating SSH keys, adding a custom Arch Linux image, creating a Droplet, and using a cloud-init configuration file to automate initial setup tasks.

---
# Step 1: Create SSH Keys

## What are SSH Keys?

SSH keys are a secure way to authenticate with your remote server without using passwords. We will create a pair of SSH keys on our local machine. 

There are two types of keys we will be creating i.e. a Private and a Public key.

    A PUBLIC SSH key encrypts data and is shared with the server, while a PRIVATE SSH key decrypts data and is kept secret on your local machine.
## Why SSH keys?

SSH keys provide a secure way to authenticate with your remote server. They are more secure than passwords because they are difficult to guess and can be easily revoked if compromised.

Follow these steps to make a SSH Key!

1. We use the command **'ssh-keygen'** to generate a key after creating a .ssh directory in your home directory first.

Copy the command below into your Windows Powershell or Terminal if you are operating on macOS.

    ssh-keygen -t ed25519 -f ~/.ssh/do-key -C "your email address"
Here,

-t = type of encryption used for the key

~ = your home directory

-C = comment for the key

> **Note**: Sometimes the above syntax may not work in the powershell and you many have to enter the full path to generate the key i.e.



    ssh-keygen -t ed25519 -f C:\Users\your-user-name\.ssh\do-key -C "youremail@email.com"

2. Replace "your-user-name" with your Windows user name.

3. Then it will ask you to create a passphrase, like a password for security reasons, so make sure you choose one you can remember.

Now, this command is going to create botth the keys for you. 

The "do-key" is a priavate key and "do-key.pub" is public key.

> **Note**: You can name your key anything! "do-key" is just an exmaple.

The key will look something like this:
        
![Screenshot] <img src="./Assets/key.png">

---
# Step 2: Download an Arch Linux Image

## What is Arch Linux?

It is a free Linux distribution that focuses on simplicity, code-correctness. It is ideal for remote servers.
## Why Arch Linux?

This is used to provide more contol over the OS and can be configured to specific needs.

How to download the image?
1. Click on the link- 

        https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/1545

2. Go to the images section (click on the most recent one)
3. Go to the Cloud image section and select the image with '.qcow2' extension. (The file name includes "cloudimg" and a date)
4. Select and image and download it.

---
# Step 3: Create a Droplet
We will create a new Droplet running Arch Linux using the custom image we just created.

## What is a Droplet?

It’s essentially a scalable virtual machine (a software program that acts like a separate computer within your actual computer.) that you can use to run applications, host websites, and more.

For this, first you have to make an account on Digital Ocean. Click on the link below to do the same:

    https://www.digitalocean.com/

Now, once you have created an account and are on the home page, 

- You will see a "Create" button in green text box in the upper right corner. Click the button.
- It will open a drop-down menuof resources you can create. Click on the "Droplets" option.

![Screenshot]<img src="./Assets/do_create.png">

 Under 'Choose region' select the region which is closest to you.
- Once you click that, go under the 'Choose an Image' section and then select 'Custom Image', you should see the Linux image we downloaded in the prior step. Select the image.
- Then, under CPU options, you can select the basic one i.e. with either a $7 or $8 option.
- After that, for 'Choose Aunthentication Method', select the 'SSH key' option and choose the 'New SSH Key' button.

    - It will open a dialogue box asking to you paste the SSH key content created in the first step. 

    For that go back to the Powershell/Terminal and use the command below to directly copy the key to your clipboard.

    IN POWERSHELL:

        Get-Content C:\Users\your-user-name\.ssh\do-key.pub | Set-Clipboard

    IN MACOS:

        pbcopy < ~/.ssh/do-key.pub

> **Note**: Since the key is a plain text file you can also open it in VSCode and copy it just like any other .txt file.


 - Go back to your Digital Oceean Account and paste the content in that dialogue box. Once that is done, give your key a name and click 'Add SSH Key'.

![Screenshot]<img src="./Assets/add_ssh.png">

- Scroll down to the 'Host Name' text box. You would like to change the default name to a something shorter(anything that you can remember) for convinience sakes.
- Leave the rest setting on their defaults.
- Click on 'Create' in the end and your Droplet has been created!

---
# Step 4: Connect your Droplet 

After you have created a droplet you can connect to it via SSH. Follow the below given steps:

1. Copy the IP address of thr droplet you jujst created.

![Screenshot]<img src = "./Assets/IPAddress.png">

2. Go to your Command Promt/Terminnal and type in the follow command-

        ssh -i .ssh/test arch@your-droplets-ip-address

-i = identity_file, the path to the private key file

arch = your username. 

[The image that we used contains a regular user named "arch".]

3. Replace the 'your-droplets-ip-address' with the address you just copied.

4. Hit Enter and your droplet has been connected.

It will look like this in the terminal:

![Screenshot]<img src = "./Assets/connect_droplet.png">



    