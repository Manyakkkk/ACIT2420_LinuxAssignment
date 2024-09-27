# ACIT2420_LinuxAssignment
Creating a Remote Server using DigitalOcean: A Step-by-Step Guide

**Introduction**

In this tutorial, we will create a remote server using DigitalOcean, a popular cloud infrastructure provider. We will cover the basics of creating SSH keys, adding a custom Arch Linux image, creating a Droplet, and using a cloud-init configuration file to automate initial setup tasks.


## Step 1: **Create SSH Keys**

**What are SSH Keys?**

SSH keys are a secure way to authenticate with your remote server without using passwords. We will create a pair of SSH keys on our local machine. 

There are two types of keys we will be creating i.e. a Private and a Public key.

    A PUBLIC SSH key encrypts data and is shared with the server, while a PRIVATE SSH key decrypts data and is kept secret on your local machine.

**Why SSH keys?**

SSH keys provide a secure way to authenticate with your remote server. They are more secure than passwords because they are difficult to guess and can be easily revoked if compromised.

**Create SSH Keys**

**1.** We use the command **'ssh-keygen'** to generate a key after creating a .ssh directory in your home directory first.

Copy the command below into your Windows Powershell or Terminal if you are operating on macOS.

    ssh-keygen -t ed25519 -f ~/.ssh/do-key -C "your email address"
Here,

-t = type of encryption used for the key

~ = your home directory

-C = comment for the key

**Note:** Sometimes the above syntax may not work in the powershell and you many have to enter the full path to generate the key i.e.

    ssh-keygen -t ed25519 -f C:\Users\your-user-name\.ssh\do-key -C "youremail@email.com"

**2.** Replace "your-user-name" with your Windows user name.

**3.** Then it will ask you to create a passphrase, like a password for security reasons, so make sure you choose one you can remember.

Now, this command is going to create botth the keys for you. 

The "do-key" is a priavate key and "do-key.pub" is public key.

**Note:** You can name your key anything! "do-key" is just an exmaple.

The key will look something like this:
        
![Screenshot] <img src="./Assets/key.png">


## Step 2: Download an Arch Linux Image

What is Arch Linux?

It is a free Linux distribution that focuses on simplicity, code-correctness. It is ideal for remote servers.

Why Arch Linux?

This is used to provide more contol over the OS and can be configured to specific needs.

How to download the image?
1. Click on the link- 

        https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/1545

2. Go to the images section (click on the most recent one)
3. Go to the Cloud image section and select the image with '.qcow2' extension. (The file name includes "cloudimg" and a date)
4. Select and image and download it.






    