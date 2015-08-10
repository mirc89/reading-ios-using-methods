# Using Methods

## Objectives:

1. Understand the syntax for calling a method and supplying arguments.
2. Recognize a method with no return type (type `void`).
3. Know how to capture the return of a non-`void` method.
4. Learn how to reference documentation to find existing method names and their purposes.

## Calling a Method

In Objective-C as a language, methods fulfill the purpose of verbs. They are behaviors that most kinds of variables can perform. Using a method is referred to as "calling a method" and means sending the command to the recipient variable to perform a pre-defined behavior. In its simplest form, method calls use a subject-verb kind of syntax wrapped in square brackets (`[``]`):


`[subject verb]`


The variable that we wish to have perform the method (called the "recipient object") is like the *subject*, while the method itself is like the *verb*:


`[variable method]`

Or, in Objective-C syntax:

```objc
[recipientObject methodName];
```

For example, let's create an `NSString` variable on which to call a method:

```objc
NSString *welcome = @"Welcome to the Flatiron School!";
```

To find the number of characters in the `welcome` string, we can call the `length` method on it:


`[welcome length]`


Since this method supplies a return, we can use an `NSLog()` to print the result of the method call to the console: 

```objc
NSLog(@"Length: %lu", [welcome length] );
```
This will print: `Length: 31`.

**Note:** *We'll explain how* `NSLog()` *works in the next reading on* `NSString`.

## Arguments

Any time you notice a `:` ("colon") in the name of a method, that's a signifier that the method accepts an argument at that point in its name. A method can accept no arguments, one argument, or many arguments, but each one will be notated with a `:` in the method name.

```objc
[recipientObject methodNameArgument:argumentVariable];
```

An easy example of a method that accepts an argument is `NSString`'s `stringByAppendingString:` method. This method concatenates the recipient string with another `NSString` supplied through an argument and returns the combination of the two strings.


```objc
NSString *welcomeToThe = @"Welcome to the ";
NSString *flatironSchool = @"Flatiron School!";

NSString *welcomeToTheFlatironSchool = 
    [welcomeToThe stringByAppendingString:flatironSchool];

NSLog(@"%@", welcomeToTheFlatironSchool);
```
This will print `Welcome to the Flatiron School!`.

**Advanced:** *The* `@` *symbol is used in Objective-C to prefix all literal syntaxes, in this case the string literal. It is also used in the format specifier for object types (*`%@`*) as used above in the the* `NSLog()` *function which prints information to the debug console. We'll discuss the string literal, format specifiers, and* `NSLog()` *in the next reading on* `NSString`.

Multiple-argument methods get called in much the same manner, but ***a whitespace character must be provided between the end of each argument and the continuation of the method name***. Review the following example:

```objc
NSString *welcome = @"Welcome to the Flatiron School!";
NSString *stringToReplace = @"the Flatiron School";
NSString *replacementString = @"Flatiron";

NSString *shorthandWelcome = [welcome stringByReplacingOccurrencesOfString:stringToReplace withString:replacementString];

NSLog(@"%@", shorthandWelcome);
```
This will print `Welcome to Flatiron!`. 

Do you see the space between the argument variable's name and the continuation of the method name? You will receive an error if you don't put a whitespace character there, since the compiler won't know when the variable name ends and the method name continues. You might also see multiple arguments split onto different lines. Since the "newline" character is also a whitespace character, the compiler will accept the method call formatted like this:

```objc
NSString *shorthandWelcome = [welcome stringByReplacingOccurrencesOfString:stringToReplace 
                                                                withString:replacementString];
```
Aligning the arguments of a multiple-argument method call is a common practice, and Xcode will `tab`-align the arguments on separate lines according to the `:`s ("colons"). This is useful for improving the readability of your code, though it makes no difference at runtime.

## Void Types

Some methods don't return a value. Because Objective-C requires the return type to be declared, these methods are declared as type `void` which means that they don't return anything and thus don't require a capture. For example, the `appendString:` method on `NSMutableString` (we'll explain mutable types later) is a method which a mutable string can perform to add another string to itself. Since there's no result being returned, the method call occupies the line by itself:

```objc
NSString *welcome = @"Welcome to the Flatiron School!";

NSMutableString *mutableWelcome = [welcome mutableCopy];
[mutableWelcome appendString:@" (づ｡◕‿‿◕｡)づ"];

NSLog(@"%@", mutableWelcome);
```

This will print `Welcome to the Flatiron School! (づ｡◕‿‿◕｡)づ`. 

We're really happy that you're joining us.

## Capturing the Return

For those methods with a non-`void` return type, their returns must be captured into a variable of that same type. "Capturing the return" is done by preceding the method call with the name of the variable to which you wish to set the method's return. 

```objc
captureVariable = [recipientObject methodNameArgument:argumentVariable];
```

This can be either a new variable which you are declaring, or an existing one which you are redefining. If it is a new variable, then you must also declare the class of the variable when you capture the return:

```objc
ReturnType *captureVariable = [recipientObject methodNameArgument:argumentVariable];
```

Capturing the return of a calling the `uppercaseString` method on our `welcome` string into a new `NSString` variable called `alteredString` would like this:

```objc
NSString *welcome = @"Welcome to the Flatiron School!";

NSString *alteredWelcome = [welcome uppercaseString];
NSLog(@"%@", alteredWelcome);
```
This will print `WELCOME TO THE FLATIRON SCHOOL!`.

```objc
alteredWelcome = [welcome lowercaseString];
NSLog(@"%@", alteredWelcome);
```
This will print `welcome to the flatiron school!`.

Notice how we overwrote `alteredWelcome` as an uppercase string into a lowercase string. We can run these `NSString` methods on the `welcome` string and capture the result with an `NSString`. In the examples above, we captured the result with the `alteredWelcome` string, but we can actually capture the return of the method with the same variable which is the recipient of the method call:

```objc
welcome = [welcome uppercaseString];
NSLog(@"%@", welcome);

welcome = [welcome stringByAppendingString:@"!!"];
NSLog(@"%@", welcome);
```
This will now print:

```objc
WELCOME TO THE FLATIRON SCHOOL!
WELCOME TO THE FLATIRON SCHOOL!!!
```

**Note:** *You can also capture a return directly into a string formatter without setting it to a named variable. We'll explain string formatting in the reading about* `NSString`.

## Looking Up Methods To Use

One of the most useful skills that you'll build as a developer is improving your ability to reference documentation. There are various kinds of resources available for this, the most fundamental of which is the resource guide provided with the programming language, framework, or product itself.

Built right in to Xcode is Apple's reference documentation on all of the frameworks and classes that they provide. It's usually the first place to look for information on Objective-C. Go ahead and open the Reference Guide to the `NSString` class. You can access it in Xcode's status bar under Help -> Documentation and API Reference `⇧``⌘``0` and searching for "NSString". 

**Top Tip:** *You can also find a quick link to the reference guide for a specific code item (usually a class name or a method name in this case) by placing your cursor within it in the code editor and opening the Quick Help window in Xcode's utility area. You should see a link following the "Reference" label.*

Here's a wealth of information about the intended use of the `NSString` class and a summary of its functionality. It lists and explains all of the method calls you can send to an instance variable of the class. You'll notice that there are some 150 method calls on the `NSString` class alone, so the thought of memorizing each and every one is not only overwhelming, but even impractical. 

Many of these methods have very specific uses and in general, you won't need to know how to use something until you need to use it. Being comfortable figuring out how to use a class and its methods which are new to you is even more important than recalling how to use everything that you've previously learned. Frameworks and programming languages are constantly evolving so knowing how to find what's current can trump what you learned in the past. In effect, knowing how to learn on your own is the primary skill of a software developer.

In the next reading we're going to discuss some of these 150 methods that you see and how you can apply them in your code.
