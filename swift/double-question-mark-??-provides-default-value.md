# Use `??` to specify a default value

My teammate is adding the first Swift to our iOS project, and during a code review, I saw this line:

```
return appDelegate.journals as NSArray? as? [Journal] ?? []
```

I had seen a lot of `!` and `?` in the code review so far, but never a `??`!

A quick Google turned up [this SO answer](http://stackoverflow.com/a/30772099/192141), which tells us it's the "nil coalescing operator," which can be simply thought of as providing a default value if an expression evaluates to `nil`.
