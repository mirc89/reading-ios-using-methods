#
#Using Methods

Objects are the 'things' in a language, and methods are the actions or behaviors that those 'things' can do. 

For example,let's say we have a dog. What can dogs do? Well they can bark. So we'd have a `Dog` class (which we can use to create individual `Dog` objects), and the `Dog` class would have a `bark` method (which each individual `Dog` object could use). Let's say for the purposes of this example, calling the bark method prints `woof woof!`.

```objc
Dog *snoopy = [[Dog alloc] init];
[snoopy bark]; // prints 'woof woof!'
```

Methods are amazing because they allow us to store an object's behavior as code that we can call on whenever we need it.
