ReturnValues
============

I’ve been trying to think of small, practical ways to improve my code. This is the latest that I’m trying to adopt.

Approach: 
Try to return values from my methods as often as I can. 

Reasoning:

1. Values can be inspected. 
2. Values can be tested. 
3. The concept of a value decreases emphasis of time sensitivity/dependency.
4. It makes it hard to do more than one thing within a single method.

Examples:

    - (void)processMessages:(NSSet *)messages;
This method does not make certain what it does. It is most likely doing something to the message after it has been processed as doing nothing after bothering to process them would be wasteful.

    - (NSSet *)processedMessages;
This method does not specify exactly what it’s doing either but it returns a value that can be inspected and gives more faith that it’s not doing more than it says it is.

    - (void)processWithIterationHandler:(void (^)(Message *processedMessage))iterationHandler;
The third is semantic exception in that it technically returns void right away but it will return the messages eventually. This approach also allows you to explicitly set the return type, which you cannot do with an array/set.
