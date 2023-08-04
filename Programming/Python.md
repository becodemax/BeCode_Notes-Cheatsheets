### Find files with their extensions in directories

```
import os
for root, dirs, files in os.walk('/path/to/directory'):
	for file in files:
		if file.endswith('.txt'):
			print(os.path.join(root, file))
```

### Super Python!

Example :

```
class Parent:  
  def __init__(self, txt):  
    self.message = txt  
  
  def printmessage(self):  
    print(self.message)  
  
class Child(Parent):  
  def __init__(self, txt):  
    super().__init__(txt)  
  
x = Child("Hello, and welcome!")  
  
x.printmessage()
```

## Definition and Usage

The `super()` function is used to give access to methods and properties of a parent or sibling class.

The `super()` function returns an object that represents the parent class.