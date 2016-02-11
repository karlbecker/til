# Don't Append `nil` NSStrings

I've written code a few too many times where this happens:

```
NSString *myGreatString = nil;
...
myGreatString = [self getTheDesiredValue];  //getTheDesiredValue returned nil, to indicate there is no desired value
...
[@"someString" appendString:myGreatString];  //append nil?  App goes CRASH BOOM BAM
```

I like returning `nil` from a method that says "There is no valid string to use here." Because we can send messages to `nil`, something in my brain goes a little haywire and it intuitively thinks appending `nil` will act like appending `@""`.

Wrong, brain.

I'm a little torn on the best way to solve this. Options I see:
1. Add `nil` checks each time I `appendString:`, something I have failed to do for years
2. Stop returning `nil` from methods that return an NSString; only return `@""` if there's no string of interest
3. Some ugly method swizzling/override where `NSString's` `appendString:` treats a `nil` as `@""` - would require adding a library to each file that uses `appendString:`

Number 2 definitely seems best - anyone see downsides to this?
