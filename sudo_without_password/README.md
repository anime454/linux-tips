# Run `sudo` Command Without Password

## Introduction

This guide explains how to configure `sudo` to allow specific users to run certain commands without entering a password on a Linux or Unix system.

I would like to acknowledge that this guide is not originally authored by me; instead, I have followed the instructions provided available at [💚 How to run sudo command without a password on a Linux or Unix 💚](https://www.cyberciti.biz/faq/linux-unix-running-sudo-command-without-a-password)

![The Capybara is coding. And he struck with some bug.](../images/capybara-coding.jpg)
[💚 Bing Image Creator 💚](https://www.bing.com/images/create/cool-capybara-is-wearing-wearing-the-black-glasses/65373b3dc24e4b24b97fcce68dac86a7?id=BC0EzpbnsqsazKtJ56FF8Q%3d%3d&view=detailv2&idpp=genimg&FORM=GCRIDP&mode=overlay)

## Gain root access

You can execute these commands to gain root access:

``` shell
su -
sudo -i
sudo su 
```

## Backup the `sudoers` File

Before making any changes, it's a good practice to back up the sudoers file:

``` shell
cp /etc/sudoers /root/sudoers.bak
```

## Edit the `sudoers` File Using `visudo`

To edit the sudoers file, use the visudo command:

``` shell
visudo
```

## Configure a List of `sudo` Commands for Passwordless Execution

The template for configuring passwordless sudo commands is as follows:

``` shell
${USERNAME} ALL = NOPASSWD: ${COMMANDS}
```

For example, if the username is "develop," and you want to run the `/usr/sbin/iptables` command without a password prompt, add the following line to the `sudoers` file:

``` shell
develop ALL = NOPASSWD: /usr/sbin/iptables
```

Save the changes in the `sudoers` file and exit.
