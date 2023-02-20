---
title: "UTM parameters in ProtonVPN email"
date: 2022-03-06
categories: [Tech]
tags: [Privacy]
description: ""
draft: false
---

## ProtonVPN

ProtonVPN is a VPN service affiliated with ProtonMail.
According to their promotional statement, they do privacy business.

> ### Why use VPN
> Keep your browsing history private. As a Swiss VPN provider, we do not log user activity or share data with third parties. Our anonymous VPN service enables Internet without surveillance.

## UTM in email links

When I deleted my ProtonVPN account, I received an email notifying me that the deletion was complete. 
ProtonVPN's site has no third party analytics so far and there are no beacons in the email.
It looks so clean, but the links in the email contained UTM parameters.

![protonvpn-utm](/img/protonvpn-utm.png)

UTM is the Urchin Tracking Module, which is currently a part of Google Analytics.
Recently, ad blocking and third-party cookie blocking are available even in the default browser settings, so server-side analytics using URLs like this may provide more accurate analysis.
Even though they are selling privacy, it seems that companies still have to analyze.
