---
title : Django重置后台密码
data : 2018-07-15 00:00:00
tags : 
- Django
- skill
---
emmm时间长忘记密码了
### 执行

```shell
$ python manage.py shell
```
### 修改

```python
In [1]: from django.contrib.auth.models import User
In [2]: user = User.objects.get(username='Username')
In [3]: user.set_password('Password')
In [4]: user.save()
In [5]: exit()
```
