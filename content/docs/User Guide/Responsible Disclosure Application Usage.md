---
title: "Using The Responsible Disclosure Application"
linkTitle: "Using The Responsible Disclosure Application"
weight: 6
date: 2022-06-20
description:
---

<div class="alert alert-info">
Your instance must have the responsible disclosure application feature enabled, otherwise it will not be accessible for you.
</div>


## Vulnerability Listing
Visiting the [Responsible Disclosure Application](/docs/glossary/responsible-disclosure-app) opens up your list of vulnerabilities.

This list contains all vulnerabilities that you have created or that have been shared with you.

![Vulnerability List](/attachments/rd-vuln-list.png)


The default view is to show only open findings, while you can easily view closed ones by clicking the corresponding button.


## Vulnerability Details

If you click on one of the vulnerabilities in your list, you will see a screen similiar to the one below.

![](/attachments/rd-single-vuln.png)

A second navigatation bar appears which contains pages related to the vulnerability including a disclosure timeline, comments and access management.

If you have permissions to change the vulnerability you will find some buttons on the right to manage the vulnerability.

The buttons have the following functionality (from left to right):

- Download the vulnerability details as a PDF report
- Export the vulnerability details as a Markdown advisory
- Notify vendor by mail, with PDF report attached (**Warning: The mail will be send unencrypted. PGP or other encryption is not yet supported!**)
- Edit the vulnerability details
- Delete the vulnerability

In the bottom half of the page, you see two more buttons for adding new proofs to the vulnerability.


## Proofs

To create a new proof, just click on one of the buttons.

![](/attachments/rd-create-proof.png)

As you can see in the screenshot, you can use markdown.
You can highlight specific parts of a codeblock with `§§highlighted$$`.


If you have created the proof, the proof will appear on the vulnerability details page as shown below.

![](/attachments/rd-single-vuln-with-proof.png)

## Timeline

The timeline allows you and the vendor to track the process of the disclosure process.


![](/attachments/rd-timeline.png)


You can create new *events* using the button on the right corner.


## Comments

If you shared the vulnerability with a user, you can use the comment feature to discuss further things about the disclosure process.

![](/attachments/rd-comments.png)


You can use markdown in the comments too.


## Manage Access

To share the vulnerability with the vendor or other contributors you need the *Manage Access* page.

The pages shows who has access to the vulnerability details.

![](/attachments/rd-manage-access.png)


You can share the vulnerability by providing an email address.
If this address already belongs to a vulnman user, he will be granted the corresponding permissions.
Otherwise, an inactive user account will be created for the user with a random username.
An invitation email will be sent to the email address to activate the account and set a password.
