---
tags:
  - alpha
  - "#project"
Links: "[[Depono GDD]]"
---


# Coding Standards - Depono

```cpp 

/* NOTE: APPLY TO C# AS ABLE*/

#include "*.h"

class Class
{ //new line
	
	/*COMMENTS*/
	//single line.
	/*multiline. or all caps*/
	
	
	/*ACCESS MODIFIERS*/
	//Should be done in order of private-> protected->public
	
	/*VARIABLE*/
	//no raw pointers
	//constexpr for nums or algs that we know arent changing
	
	private: //don't use in classes, private by default
	
	T _privateVar; //private vars must begin with _
	
	protected: //use for base and children
	
	T _protectedVar; //same as private var
	
	public: //should be at bottom
	T publicVar; //no _ needed for public vars
	
	/*IMPORTANT: vars should always be over the methods
	
	/*METHODS*/
	//always at bottom of each protection level
	//Constructors in public by default
	//variables at top
	//if more then 10-15 lines, consider abstracting it to its own func
	
	Class() //define in header not cpp
	{
	}
	
	~Class() //same as header
	
	void Method(); //all methods go in cpp
}

```






## BackLinks

```dataview
list
from [[]]
```





