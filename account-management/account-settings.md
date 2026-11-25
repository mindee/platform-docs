---
description: Manage your Mindee account.
icon: user
---

# Account Settings

A Mindee account is required for logging into the platform.

However, models and API keys are stored at the organization level.

When you create your Mindee account, a default organization will be created. Your account will be the [owner](organizations.md#member-roles) of this organization.

You can be a member of multiple organizations.

## Access Account Settings

Click on "<i class="fa-gear">:gear:</i> Settings" in the main menu, then on the "Account" tab.

Or simply click here: <a href="https://app.mindee.com/settings?tab=account" class="button primary">Go to Account page</a>

## Personal Information

### Email

If you connect to Mindee using your email and a password, you can change your email address. You'll be sent a link to confirm the new email address.

If you connect to Mindee through a 3rd party, such as Google or Github, the email address used will be displayed. It is not possible to change it, you'll need to connect with another provider or use an email/password login.

### Full Name

You can change your full name as it appears in the Mindee platform to other users in your organization.

## Two-Factor Authentication

2FA can be added by any user on their account. The organization Owner may also require all users in the organization to use 2FA.

Add and remove your authentication devices in this section. A device is simply any physical device or application that supports HOTP or TOTP. For example you can use [FreeOTP](https://freeotp.github.io/).

Recovery codes can be downloaded at any time.

{% hint style="info" %}
**Make sure to always download and save the recovery codes!**

If you lose access to the device you can use the recovery codes to log in and set up a new device. Otherwise you'll be locked out of your account.
{% endhint %}

## Danger Zone

### Delete Account

You can delete your account and all its associated data.

{% hint style="danger" %}
Deleting your account is an **irreversible action**, all data will be lost forever!
{% endhint %}

Deleting your account will also delete all organizations in which you are the only owner.

Any non-owner users will lose access to these organizations.
