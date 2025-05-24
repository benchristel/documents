# Code blocks and inline monospace text

```ts
function factorial(n: number): number {
    assert(n >= 0, "factorial is only defined for positive numbers");
    assert(n === Math.floor(n), "factorial is only defined for integers");
    
    return n === 0
        ? 1
        : n * factorial(n - 1);
}
```

The code block above defines a `factorial` function in TypeScript.

## Code in figures

<figure float-left>

```html
<!DOCTYPE html>
<html lang="en">
    <meta charset="utf-8">
    <title>...</title>
    <body>
        ...
    </body>
</html>
```

<figcaption>An HTML template, showing the use of the <code>lang="en"</code> attribute</figcaption>
</figure>

So far, we have not discussed any of the language features you'd likely encounter in a grammar textbook for a typical human language: plurals, verb tenses, pronouns, etc. Those features are not part of OGTRTA proper; they are left up to the individual language designer.

One of the nice things about OGTRTA is that it provides a consistent backdrop against which to compare different implementations of various language features. Using OGTRTA, we can clearly see how different implementations make tradeoffs between conciseness, flexibility, and ambiguity.
