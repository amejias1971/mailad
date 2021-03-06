# MailAD

This is a handy tool to provision a mail server on linux linked to an Active Directory server (Samba or Windows, it does not care) with some constraints in mind, as this is a typical mail config to be used in Cuba under certain laws and security requirements

## Rationale

This repository is intended to be cloned on your fresh OS install under `/root` (you can use a LXC instance, VM, CT, etc) and setup on a main conf file as per the file comments, then run the steps on a makefile and follow the steps to configure your server.

After a few steps you will have a mail server up and running in about 15 minutes tops. _(this time is based on a 2Mbps internet connection to a repository, if you have a local repository it will be less)_

This tool is tested and supported on:

- Ubuntu Bionic 18.04 (last LTS)
- Ubuntu Focal 20.04 (Actual LTS and actual dev env)
- Debian Buster 10 (Stable)

It's recommended that the instance of MailAD sits inside your DMZ net with a firewall between it and your users and a mail gateway like [Proxmox Mail Gateway](https://www.proxmox.com/en/proxmox-mail-gateway) between it and the outside world

## Features

This will provision a mail server in a enterprise/SOHO as a real server facing the users and behind a Mail Gateway to the outside world, you can see the major features in the [Features.md](Features.md) file, among others you will find:

0. Low resource footprint
0. Automatic alias using AD groups
0. Optional user privilege access via AD groups (local/national/international)
0. Manual alias to handle typos or enterprise positions
0. Manual ban list for trouble some address (aka blacklist)
0. Manual headers & body checks lists
0. Painless upgrades

## TODO

There is a [TODO list](TODO.md), a kind of a "roadmap" for new features, but as I (only one dev so far) have a life, a family and a daily job, you know...

All dev is made on weekend or late at night (seriously take a peek on the commit dates!) if you need a feature or fix ASAP, please take into account making a donation or found me and I will be happy to help you, my contact info is on the bottom of this page

## Constraints and requirements

Remember the comment at top of the page about _"...with some constraints in mind..."_ yeha, here they are:

0. Your user base and config came from an Active Directory (AD from now on) as mentioned, we prefer a Samba AD but works on Windows too; see [AD requirements for this tool](AD_Requirements.md)
0. The mail storage will be a folder in `/home/vmail`, all mail will belong to a user named `vmail` with uid:5000 & gid:5000. Tip: that folder can be a NFS mount or any other type of network storage
0. You use a Windows PC to control and manage the domain (must be a domain member and have the RSAT installed and activated), we recommend a Windows 10 LTSC/Professional
0. The server allows all communications protocols by default _(POP3, POP3S, IMAP, IMAPS, SMTP, SSMTP and SUBMISSION)_ it's **up to you** to restrict the users access in a way that them just use the secure versions (POP3S, IMAPS & SUBMISSION. Take into account that the SMTP service must be used only to send/receive the emails from the outside world)

## How to install or try it?

We have a [INSTALL.md](INSTALL.md) file just for that

## This is free software

Have a comment, question, contributions or fix?

Don't hesitate, use the Issues tab in the repository URL or drop me a message via my social media accounts:

- Twitter: @co7wt
- Telegram: @pavelmc

We have a file to register the contributions to this Software, you can check it [here](Contributors.md)
