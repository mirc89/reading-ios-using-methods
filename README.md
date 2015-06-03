# Using Methods
----
## Objectives:

1. Learn how to call a method and supply arguments.
2. Learn how to reference Apple documentation to find existing method names and their purposes.

## Calling a Method

In Objective-C as a language, methods fulfill the purpose of verbs. They are behaviors that most kinds of your variables can perform. Using a method is referred to as "calling a method" and means sending the command to the recipient variable to perform a pre-definied behavior. Calling a method uses a subject-verb syntax wrapped in square brackets (`[``]`):

```objc
[<#recipient#> <#methodName#>];
```

For example, `NSString` has a method named `length` which returns an `NSUInteger` of the number of characters in the string. Calling the `length` method on our `welcome` string from the previous reading would like this.

```objc
NSString *welcome = @"Welcome to the Flatiron School!";
NSUInteger welcomeLength = [welcome length];
```

**Note:** *The* `U` *in* `NSUInteger` *means "unsigned". We'll explain this in the reading about* `NSInteger`.

## Arguments

Any time you notice a `:` in the name of a method, that's a signifier that the method accepts an argument at that point in its name. A method can accept no arguments, one argument, or many arguments, but each one will be notated with `:` in the method name.

An easy example of a method that accepts an argument is `NSString`'s `stringByAppendingString:` method. This method concatenates the recipient string with another `NSString` supplied through an argument and returns the combination of the two strings.


```objc
NSString *welcomeToThe = @"Welcome to the ";
NSString *flatironSchool = @"Flatiron School!";

NSString *welcomeToTheFlatironSchool = 
[welcomeToThe stringByAppendingString:flatironSchool];

NSLog(welcomeToTheFlatironSchool);
```
This will print `Welcome to the Flatiron School!`.

Multiple-argument methods get called in much the same manner, but ***a whitespace character must be provided between the end of each argument and the continuation of the method name***. Review the following example:

```objc
NSString *welcome = @"Welcome to the Flatiron School!";

NSString *welcomeSlytherin = 
[welcome stringByReplacingOccurencesOfString:@" " withString:@"_"];

NSLog(welcomeSlytherin);
```
This will print a welcome message that has had the spaces converted to underscores (turning it into snake case): `Welcome_to_the_Flatiron_School!`. Do you see the space between the `@" "` argument string and `withString:`? You will receive an error if you forget that separation.

## Looking Up Methods