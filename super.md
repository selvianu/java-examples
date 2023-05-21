super()
It's a way to call a constructor on the super class, directly from the sub class's constructor.
Like this(), it has to be the first statement of the constructor.
Because of that rule, this() and super() can never be called from the same constructor.
If you don't make a call to super(), then Java makes it for you, using super's default constructor. 
If your super class doesn't have a default constructor, than you must 
    explicitly call super() in all of your constructors, passing the right arguments to that constructor.
