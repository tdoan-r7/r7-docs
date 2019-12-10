---
title: "Users, roles, and permissions frequently asked questions"
excerpt: ""
---
This page concerns user management and user account roles and permissions.

## How do I find out what my permissions are in InsightVM?

Click the link for your user name, which appears near the upper right corner of every page of the InsightVM Security Console Web interface. InsightVM displays the User preferences wizard for your account. Click through it to view which sites and asset groups you have access to. If you are unsure of what InsightVM functions you are able to perform, such as running scans, consult your InsightVM global administrator.

## Why do I see "InsightVM user" in my authentication options for creating user accounts if I'm using an LDAP server to authenticate users?

The "InsightVM user" authentication option represents the default, built-in InsightVM method for authenticating users. Even if your organization has configured a separate user authentication service, such as LDAP/Active Directories (AD), you still have the option to authenticate a given user with the built-in InsightVM service.

## Can I edit permissions for a preset InsightVM role?

No. You can only change permissions for a customized role.

## Can any user with a customized InsightVM role have access to administrative functions?

No. Only a user with a global administrator role can access administrative functions, such as configuring the InsightVM Security Console settings, creating user accounts, or performing maintenance tasks. The global administrator role is a preset role within InsightVM.