---
title: "Current Development Status"
linkTitle: "Current Development Status"
date: 2022-05-26
description:
---

This post is intended to give a brief summary of the current development processes and ideas in vulnman.


Currently the focus is on implementing and improving the "Responsible Disclosure" application.
There have been some bug fixes and UI improvements here.

In addition, preparations are underway for new user roles that will be able to log in and use vulnman in the future.
Using the "Responsible Disclosure" application as an example, we are thinking of developers of the software in question.
These should be able to be invited in the future and thus receive a release for the corresponding vulnerabilities.

A few other quick updates:

We have already implemented our own user model.
This is a breaking change to version 0.3.0.
Data from version 0.3.0 will probably not be migratable.
However, this change will allow us more flexibility in the future.

User profiles already exist. These are currently still minimalistic, but the base is already done.
Pentester profiles are public and should be able to be changed to private in the future.

Soon there will be a first implementation of a comment function under vulnerabilities in the RD.

The page a user sees after login will differ per user role.

These will be by and large the changes in the next release.

See you soon.