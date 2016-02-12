# Java Collections Can Have `null`

Today I came across this bit of code in our Android app:

```
// final List<Shelf> shelves is defined earlier

Iterator<Shelf> iter = shelves.iterator();
while (iter.hasNext()) {
  Shelf shelf = iter.next();
    if (shelf == null)
      continue;
```

The iterator's `hasNext()` function returns `true` even when the next object is `null`?

Java considers `null` a valid object can be inserted into a collection?

Why yes, [yes it does](http://stackoverflow.com/questions/6997142/is-there-a-java-collection-framework-class-that-doesnt-allow-null-elements).
