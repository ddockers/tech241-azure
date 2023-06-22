# Creating a Virtual Machine (VM)

![VM_diagram](/my_vm_diagram.png)

We first need be able to select the SSH key. The key needs to be on our local machine for us to SSH in.

We create the private key first, and then put the padlock (public key) onto Azure.

## GitBash

We need to begin in the home directory.

`cd` + enter takes us to `dedo2@Dee_Doxton_PC MINGW64 ~`
We need to navigate to the `.ssh` folder. Becaise we currently don't have one we need to make one.

To make a new directory,
```
mkdir .ssh
```
Then, `cd` into `.ssh`.

Next thing to do is to generate the SSH key pair.
```
ssh-keygen -t rsa -b 4096 -C "deanne.dockery@gmail.com"
```
`-t` is the type of encryption (RSA in this case), `-b` is the number of bytes.
```
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/dedo2/.ssh/id_rsa):
```
The key pair is being generated and we need to save it in the tech241 directory in Azure.

We need to enter:
```
tech241-deanne-az-key
```

After disregarding the passphrase prompt, we can use `ls` to see the keys.
```
dedo2@Dee_Doxton_PC MINGW64 ~/.ssh
$ ls
tech241-deanne-az-key  tech241-deanne-az-key.pub
```
The `.pub` key is the public key, and the other is the private key.


**The public key can be seen as the padlock, so it doesn't matter if it's public. The private key can be seen as the key for the padlock.**

To get the public key:
```
cat tech241-deanne-az-key.pub
```
This generates a *really* long string that needs to be entered into Azure.

## Azure

### Creating an SSH Key in Azure

Navigate to *SSH Keys* in Azure and click *Create*.

It's best practice to give the key the same name as on the local computer.

![Azure_SSH](/azure_ssh_1.png)

The *really* long string needs to be entered into the *Upload key* box. 

NB. The key starts with `ssh-rsa` and ends with the email address.

Then navigate to *Tags* and enter *Owner* as Name and *Deanne* as Value, and select *Review + create*.

When it's created, all SSH keys in the resource group will be displayed.

### Creating the VM

Navigate to *Virtual machines* in Azure, and select *Create*. Enter the following info:

| Column 1 | Column 2 | 
| -------- | -------- | 
| Resource group | tech241 |  
| Virtual machine name | tech241-deanne-man-app | 
|Region | (Europe) UK South |
Security type | Standard


## Connect to VM
On azure enter ~/.ssh/tech241-deanne-az-key

Enter this into GitBash


